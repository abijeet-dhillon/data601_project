# DATA 601 — Predicting Next-Year GDP per Capita

University of Calgary DATA 601 group project by **Abijeet Dhillon, Noor Fatima, and Tam Nguyen**.

The analysis asks whether current-year energy, economic, infrastructure, urbanization, environmental, and country information can predict a country's GDP per capita in the following year. The complete analysis is in [notebooks/DATA601_Project.ipynb](notebooks/DATA601_Project.ipynb), from data cleaning and exploratory plots through model comparison, tuning, and interpretation.

## Repository structure

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── Data.xlsx
├── notebooks/
│   └── DATA601_Project.ipynb
├── presentation/
│   ├── DATA601_Presentation.pdf
│   └── DATA601_Presentation.pptx
└── report/
    ├── DATA601_Report.docx
    └── DATA601_Report.pdf
```

Local setup creates `.venv/`. Running the notebook creates intermediate CSV files and encoder artifacts in `data/`; these generated files are ignored by Git. The optional command-line run below saves an executed notebook in `build/`, which is also ignored.

## Dataset and analysis

The included [data/Data.xlsx](data/Data.xlsx) workbook contains World Bank [World Development Indicators](https://databank.worldbank.org/source/world-development-indicators#advancedDownloadOptions) data. Its `Data` sheet has 5,208 country-indicator rows, covering 217 countries, 24 indicators, and years 2006–2025. The workbook is already included; no download or Google Drive connection is needed to run the analysis.

The notebook:

1. Reshapes the workbook into country-year observations, limits the analysis to 2006–2021, and removes countries with incomplete GDP per capita or GDP growth histories. This leaves 193 countries and 3,088 country-year observations.
2. Explores GDP, energy use, electricity access, emissions, urbanization, and correlations.
3. Constructs next-year GDP per capita as the regression target. Predictor years are split chronologically into training (2006–2015), validation (2016–2017), and test (2018–2020).
4. Handles missing predictors using missing-value flags, forward filling within countries, and training-set medians; selects features and encodes countries.
5. Compares Linear Regression, Decision Tree, Random Forest, and XGBoost, tunes the ensemble models, and evaluates a log-transformed target.
6. Evaluates the final XGBoost model on the held-out test period, compares it with a “next year equals this year” benchmark, and examines errors and feature importance.

The [report](report/DATA601_Report.pdf) and [presentation](presentation/DATA601_Presentation.pdf) describe the findings and limitations.

## Run locally

Use **Python 3.14** for the documented environment. Run setup commands from the repository root.

### 1. Get the project and create a virtual environment

On macOS or Linux:

```bash
git clone https://github.com/abijeet-dhillon/data601_project.git
cd data601_project
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

If you already have this folder, start with `cd` into it and skip cloning. If multiple Python versions are installed, use `python3.14` to create the environment.

On Windows PowerShell, use these setup commands after cloning and entering the repository:

```powershell
py -3.14 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

The requirements include the analysis libraries, the Excel reader (`openpyxl`), the LOWESS dependency (`statsmodels`), and the Jupyter tools needed to open and execute the notebook.

On **macOS**, use the OpenMP runtime already bundled with scikit-learn inside `.venv`. From the repository root, run this in each new terminal before starting Jupyter:

```bash
export DYLD_LIBRARY_PATH="$PWD/.venv/lib/python3.14/site-packages/sklearn/.dylibs${DYLD_LIBRARY_PATH:+:$DYLD_LIBRARY_PATH}"
```

This lets XGBoost load `libomp.dylib` without a system-wide Homebrew installation. Keep this environment variable set in the terminal used for either execution method below.

### 2. Open and execute the notebook

With `.venv` activated, launch Jupyter from the repository root:

```bash
python -m notebook notebooks/DATA601_Project.ipynb
```

Use the Python kernel from `.venv`, then choose **Kernel → Restart Kernel and Run All Cells**. Run the notebook from the beginning: later cells reload CSVs and encoders produced by earlier cells. The notebook resolves `data/` when its working directory is either the repository root or `notebooks/`.

Hyperparameter searches evaluate 150 XGBoost fits and 540 Random Forest fits, plus final refits. A complete run can take several minutes or longer depending on your machine.

### 3. Execute without the browser (optional)

From the repository root, with `.venv` activated:

```bash
python -m nbconvert --to notebook --execute notebooks/DATA601_Project.ipynb \
  --ExecutePreprocessor.kernel_name=python3 \
  --ExecutePreprocessor.timeout=-1 \
  --output DATA601_Project.executed.ipynb \
  --output-dir build
```

This runs every code cell and saves fresh outputs to `build/DATA601_Project.executed.ipynb`. The source notebook retains its existing saved outputs until you rerun and save it. In PowerShell, put the command on one line or use backticks instead of the shell continuation backslashes.

The tuning cells use all available job workers (`n_jobs=-1`). To limit a run to four workers and one OpenMP thread per worker on macOS/Linux, prefix the execution command with `LOKY_MAX_CPU_COUNT=4 OMP_NUM_THREADS=1`. This changes resource usage without changing the notebook's models or search grids.

## Local validation

All **93 code cells** completed successfully on macOS (Apple Silicon), using Python 3.14.7 and the versions pinned in `requirements.txt`. Validation executed the notebook cells in order through IPython, with four threading workers and one OpenMP thread, because this session's sandbox blocks Jupyter kernel sockets. The browser and `nbconvert` launch commands above are provided for normal local use; a Jupyter kernel launch was not verified in the sandbox.

The local final model's test MAE was **1,470.75**, RMSE **3,835.69**, and R² **0.9772**. Library version differences can change tuning results and metrics from the original Colab run. The notebook's analysis code, existing written interpretation, report, and presentation retain the original project work; use the freshly executed tables when reviewing local results.

## Generated files

A complete run writes these files under `data/` and overwrites them on subsequent runs:

| Files | Contents |
| --- | --- |
| `df_final.csv` | Cleaned country-year data used for exploration and modelling |
| `train_ffill_median.csv`, `validation_ffill_median.csv`, `test_ffill_median.csv` | Imputed splits with country, year, and target columns |
| `X_train_final.csv`, `X_val_final.csv`, `X_test_final.csv` | Selected predictors with country one-hot encoding |
| `y_train_final.csv`, `y_val_final.csv`, `y_test_final.csv` | Matching next-year GDP targets |
| `country_encoder.pkl`, `final_feature_columns.pkl` | Country encoder and final predictor column order |

Plots and evaluation tables appear inside the notebook. The analysis does not export a trained final model.

## Troubleshooting

- **Missing files:** keep `data/Data.xlsx` in its supplied location, start Jupyter from the repository root, and run all cells in order.
- **Missing Python module:** activate `.venv`, install `requirements.txt`, and make sure Jupyter is using the environment's Python kernel.
- **macOS XGBoost OpenMP error:** repeat the `DYLD_LIBRARY_PATH` export above from the repository root, then relaunch Jupyter from that terminal. The runtime stays inside `.venv`; no Homebrew install is required.
- **Run still busy:** the Random Forest grid search is the largest step. Let it finish; the command-line timeout is disabled for this reason.

To leave the virtual environment, run `deactivate`.
