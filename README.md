# DATA 601 — Data Science Project

This repository contains our group project for **DATA 601 at the University of Calgary (UofC)**. The project follows the three-stage structure of the course, taking a dataset from initial exploration and visualization through predictive modelling and, finally, communicating insights through a data-driven story.

## Project Overview

The project is completed in three stages:

1. **Stage 1 — Visualize Your Data**
2. **Stage 2 — Running a Model**
3. **Stage 3 — Telling a Story with Data**

Our goal is to develop a clear question of interest, understand the data through meaningful visualizations, apply an appropriate predictive model, and communicate the results to a stakeholder who has a direct interest in the question.

---

## Stage 1: Visualize Your Data

**Due:** September 18  
**Weight:** 20% of final mark

The first stage focuses on exploring and visualizing our chosen dataset.

The computational notebook includes:

- An introduction to the dataset
- Data cleaning and preparation
- Exploratory data analysis
- Key descriptive statistics
- Appropriate data visualizations
- Discussion of patterns, relationships, and potential questions raised by the data

The emphasis is on the **organization, reasoning, and effectiveness of our visualizations**, rather than simply producing a large number of plots.

### Deliverable

The Stage 1 computational notebook is submitted to the **D2L Project 1 folder**.

---

## Stage 2: Running a Model

**Due:** October 2  
**Weight:** 20% of final mark

In Stage 2, we build on the exploratory work from Stage 1 by using a predictive model to investigate a question of interest.

The notebook includes:

- A clearly defined modelling question
- Justification for the selected model
- Data preparation and feature selection
- Model training
- Model evaluation
- Appropriate performance metrics and visualizations
- Interpretation of the results
- Discussion of limitations and potential next steps

The objective is not simply to obtain the best possible prediction, but to use an appropriate model to answer a meaningful question with the available data.

### Deliverable

The Stage 2 computational notebook is submitted to the **D2L Project 2 folder**.

---

## Stage 3: Telling a Story with Data

**Presentation:** October 5  
**Written report + notebook:** October 9

### Weight

| Component | Weight |
|---|---:|
| Written report | 20% |
| Computational notebook | 2.5% |
| Group presentation | 2.5% |
| **Total** | **25%** |

The final stage brings together the skills developed throughout the course.

We use our dataset to tell a coherent, data-driven story to a stakeholder with a direct interest in the answer.

The final project includes:

1. **Problem statement**
   - Clearly state the question we are trying to answer.
   - Explain why the question matters and who has a stake in the answer.

2. **Data description**
   - Describe the dataset and its relevant variables.
   - Explain any data cleaning or preprocessing.
   - Use key visualizations to communicate important characteristics of the data.

3. **Modelling**
   - Apply at least one predictive model.
   - Explain why the selected model is appropriate for the question and data.
   - Evaluate and interpret the model's results.

4. **Results and discussion**
   - Explain what the analysis tells us about the original question.
   - Connect the model results with the exploratory analysis.
   - Discuss limitations and uncertainty.
   - Identify reasonable next steps.

Importantly, **weak or inconclusive results are still useful**. A model that does not produce strong results can reveal limitations in the data and motivate further investigation.

### Deliverables

The final project consists of:

- A written report in Word, PDF, or another appropriate format
- The computational notebook containing the code used to produce the analysis
- A 3-minute group presentation

The report and notebook are submitted to the **D2L Project 3 folder**.

---

## Repository Structure

The repository is organized as follows:

```text
.
├── README.md
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── project_1_visualization.ipynb
│   ├── project_2_model.ipynb
│   └── project_3_final.ipynb
├── src/
│   └── ...
├── figures/
│   └── ...
├── report/
│   └── final_report.pdf
└── presentation/
    └── presentation.pdf
```

### Directory descriptions

- **`data/raw/`** — Original, unmodified datasets.
- **`data/processed/`** — Cleaned or transformed datasets used for analysis.
- **`notebooks/`** — Computational notebooks for each project stage.
- **`src/`** — Reusable Python code and helper functions.
- **`figures/`** — Visualizations generated during the analysis.
- **`report/`** — Final written report.
- **`presentation/`** — Materials for the final presentation.

---

## Dataset

Our project uses:

> **Dataset:** *[Dataset name]*

The dataset was obtained from:

> *[Source / URL]*

### Why this dataset?

We selected this dataset because:

- *[Reason 1]*
- *[Reason 2]*
- *[Reason 3]*

The dataset contains information about *[brief description of what the observations represent]* and allows us to investigate *[general topic/question]*.

---

## Research Question

### Primary Question

> **[Insert your main research question here.]**

### Motivation

Our question is motivated by *[brief explanation of why the question matters]*.

The primary stakeholder for this analysis is **[stakeholder]**, who may use the results to *[decision/action/use of findings]*.

---

## Methodology

Our analysis follows the general workflow:

```text
Raw Data
   ↓
Data Cleaning & Preparation
   ↓
Exploratory Data Analysis
   ↓
Data Visualization
   ↓
Research Question
   ↓
Predictive Model
   ↓
Model Evaluation
   ↓
Interpretation
   ↓
Data-Driven Conclusions
```

We will use appropriate statistical and machine-learning techniques based on the research question and characteristics of the dataset.

---

## Technologies

The project is primarily developed using:

- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- seaborn
- scikit-learn

Additional libraries may be added as required.

---

## Reproducibility

To reproduce the analysis:

1. Clone this repository.
2. Install the required Python dependencies.
3. Obtain the dataset from the source described above.
4. Place the raw data in `data/raw/`.
5. Run the notebooks in order.

A `requirements.txt` file will be provided once the project dependencies have been finalized.

```bash
git clone <repository-url>
cd <repository-name>
pip install -r requirements.txt
```

---

## Group Members

| Name | Role |
|---|---|
| *[Name]* | *[Role / contribution]* |
| *[Name]* | *[Role / contribution]* |
| *[Name]* | *[Role / contribution]* |

---

## Project Timeline

| Date | Milestone |
|---|---|
| September 18 | Stage 1 — Visualization notebook due |
| October 2 | Stage 2 — Modelling notebook due |
| October 5 | 3-minute group presentation |
| October 9 | Stage 3 — Final report and notebook due |

---

## Status

- [ ] Dataset selected
- [ ] Research question defined
- [ ] Stage 1 — Data cleaning
- [ ] Stage 1 — Exploratory analysis
- [ ] Stage 1 — Visualizations
- [ ] Stage 2 — Model selection
- [ ] Stage 2 — Model training
- [ ] Stage 2 — Model evaluation
- [ ] Stage 3 — Final analysis
- [ ] Stage 3 — Written report
- [ ] Stage 3 — Presentation
- [ ] Final submission

---

## Acknowledgements

This project was completed as part of **DATA 601 at the University of Calgary**.

Dataset and external resources are credited in the relevant notebooks and final report.