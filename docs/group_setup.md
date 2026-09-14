# DATA 601 Project — Local VS Code Setup

This guide is for our group members who want to run the project notebook locally in Visual Studio Code.

The repository currently contains the main notebook, `DATA601_Project.ipynb`, along with the project data files (`Data.xlsx`, `MetaData.xlsx`, `df_final.csv`, and `df_final.xlsx`).

## 1. Make sure Python is installed

You need Python installed in addition to VS Code. You can check by opening a terminal and running:

```bash
python --version
```

On some Windows installations, use:

```bash
py --version
```

If Python is not installed, download it from the official Python website:

https://www.python.org/downloads/

## 2. Install VS Code extensions

VS Code needs the **Python** and **Jupyter** extensions to work with `.ipynb` notebooks.

In VS Code:

1. Open the Extensions panel (`Ctrl+Shift+X` on Windows/Linux or `Cmd+Shift+X` on macOS).
2. Search for **Python** and install the extension published by Microsoft.
3. Search for **Jupyter** and install the extension published by Microsoft.

Microsoft's Jupyter documentation confirms that VS Code uses the Python and Jupyter extensions to run notebook cells and that the notebook kernel should come from a Python environment containing Jupyter support.

Official Microsoft documentation:

- Jupyter notebooks in VS Code: https://code.visualstudio.com/docs/datascience/jupyter-notebooks
- Python environments in VS Code: https://code.visualstudio.com/docs/python/environments

### If you do not have VS Code installed

Use Microsoft's installation guide:

https://code.visualstudio.com/docs/setup/setup-overview

## 3. Clone the GitHub repository

Open a terminal in VS Code (`Terminal` → `New Terminal`) or use your normal terminal.

Clone the repository with:

```bash
git clone https://github.com/abijeet-dhillon/data601_project.git
```

Then move into the project directory:

```bash
cd data601_project
```

You can verify that you are in the correct folder with:

```bash
git status
```

You should see the `main` branch and the project files.

## 4. Open the repository in VS Code

From inside the project directory, run:

```bash
code .
```

If the `code` command is not available, open VS Code normally and use:

**File → Open Folder...**

Then select the `data601_project` folder you just cloned.

## 5. Create a virtual environment

Create a virtual environment named `.venv` in the project folder.

### Windows

```powershell
py -m venv .venv
```

Activate it in PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Or in Command Prompt:

```cmd
.venv\Scripts\activate.bat
```

### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

After activation, your terminal should show something similar to:

```text
(.venv) ...
```

## 6. Upgrade pip and install the notebook dependencies

The current repository does not include a `requirements.txt`, so install the core packages needed for the notebook manually.

With `.venv` activated, run:

```bash
python -m pip install --upgrade pip
python -m pip install jupyter ipykernel pandas numpy matplotlib seaborn openpyxl
```

These packages provide notebook execution, data manipulation, visualization, and Excel-file support for the files included in this repository.

If the notebook later reports that another package is missing, install it into the same active environment with:

```bash
python -m pip install PACKAGE_NAME
```

For example:

```bash
python -m pip install scikit-learn
```

## 7. Select the `.venv` as the notebook kernel

Open:

```text
DATA601_Project.ipynb
```

In the top-right corner of the notebook, click **Select Kernel** (or the currently selected kernel).

Choose the Python interpreter from the project's `.venv` environment.

It should look similar to:

```text
Python 3.x.x ('.venv': venv)
```

You can also use the Command Palette:

```text
Ctrl+Shift+P  (Windows/Linux)
Cmd+Shift+P   (macOS)
```

Then run:

```text
Python: Select Interpreter
```

and choose `.venv`.

Microsoft's VS Code documentation recommends selecting the appropriate Python environment before running Jupyter notebook cells.

## 8. Run the notebook

Once `.venv` is selected as the kernel:

1. Open `DATA601_Project.ipynb`.
2. Start at the first code cell.
3. Run cells from top to bottom using the **Run Cell** (▶) button.
4. Check that each cell completes without an error before moving to the next one.

You can also use the notebook controls to run all cells.

### Important: run cells in order

Some cells create variables, data frames, or transformed data that later cells depend on. Run the notebook from the beginning rather than jumping directly to a later cell.

## 9. Working with the project data

The repository already contains the project's data files, so you should **not need to download the dataset separately**.

The files currently in the repository include:

```text
Data.xlsx
MetaData.xlsx
df_final.csv
df_final.xlsx
```

Keep the notebook and data files in the repository's expected locations. If you move the data files, file paths in the notebook may no longer work.

## 10. Before making changes

Before starting work, make sure your local copy is up to date:

```bash
git pull origin main
```

Then activate your `.venv` and open the notebook.

## 11. Saving and pushing your changes

After making changes to the notebook:

```bash
git status
git add DATA601_Project.ipynb
git commit -m "update project notebook"
git push origin main
```

If you changed other files, use:

```bash
git add .
git commit -m "update project files"
git push origin main
```

## 12. Common problems

### `python` is not recognized

Try:

```powershell
py --version
```

on Windows, or install Python from:

https://www.python.org/downloads/

### The notebook says a package is missing

Make sure `.venv` is activated, then install the missing package:

```bash
python -m pip install PACKAGE_NAME
```

After installing it, restart the notebook kernel and run the affected cell again.

### `.venv` does not appear as a kernel

First make sure these are installed inside `.venv`:

```bash
python -m pip install jupyter ipykernel
```

Then restart VS Code and select `.venv` from the notebook kernel picker.

### PowerShell will not activate `.venv`

If Windows blocks PowerShell script execution, use Command Prompt and run:

```cmd
.venv\Scripts\activate.bat
```

Alternatively, use the VS Code terminal with Command Prompt as the shell.

### Git is not installed

Check with:

```bash
git --version
```

If Git is missing, install it from:

https://git-scm.com/downloads

## Quick setup checklist

```text
[ ] Python installed
[ ] VS Code installed
[ ] Python extension installed
[ ] Jupyter extension installed
[ ] Repository cloned
[ ] `cd data601_project`
[ ] `.venv` created
[ ] `.venv` activated
[ ] Jupyter + required Python packages installed
[ ] `.venv` selected as the notebook kernel
[ ] DATA601_Project.ipynb opened
[ ] Notebook cells run from top to bottom
```

## Repository

GitHub:

https://github.com/abijeet-dhillon/data601_project
