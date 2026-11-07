# Exploratory Data Analysis (EDA) on Multiple Datasets Using Python

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter)

## Project Overview

This repository contains a hands-on **Exploratory Data Analysis (EDA)** notebook that uses Python to explore and visualize four datasets: **Tips, Titanic, Iris, and Flights**.

The notebook demonstrates how different plots help examine numerical distributions, compare categories, explore relationships between variables, and inspect changes over time. It is a practical data visualization exercise, not a predictive modeling project.

## Objectives

- Practice loading and inspecting datasets with Pandas and Seaborn.
- Explore relationships between numerical and categorical features.
- Compare groups using bar plots, box plots, and cross-tabulations.
- Visualize distributions with kernel density estimation (KDE).
- Examine multivariate relationships using pair plots.
- Explore time-related patterns using line plots and pivot-table heatmaps.
- Practice clustered heatmaps with Seaborn.

## Datasets

| Dataset | Source in notebook | Focus |
| --- | --- | --- |
| **Tips** | `sns.load_dataset('tips')` | Total bills, tips, sex, smoking status, and party size |
| **Titanic** | `pd.read_csv('train.csv')` | Passenger class, age, sex, survival, and parents/children aboard |
| **Iris** | `sns.load_dataset('iris')` | Relationships between flower measurements by species |
| **Flights** | `sns.load_dataset('flights')` | Passenger counts across months and years |

> **Important:** The Titanic dataset is loaded from a local file named `train.csv`. Place this file beside `eda.ipynb` before running the notebook. The other three datasets are loaded using Seaborn's dataset loader, which may require internet access on first use.

## Analysis and Visualizations

### 1. Tips Dataset — Relationships Between Bills and Tips

The notebook uses a Seaborn **scatter plot** to compare `total_bill` and `tip`, while encoding additional variables:

- **Color (`hue`)**: `sex`
- **Marker style (`style`)**: `smoker`
- **Point size (`size`)**: party `size`

This visualization demonstrates how several variables can be represented in a single chart.

### 2. Titanic Dataset — Passenger Characteristics and Survival

The Titanic section includes:

| Visualization | Variables / purpose |
| --- | --- |
| **Bar plot** | Passenger class (`Pclass`) versus age (`Age`), grouped by `Sex` |
| **Box plot** | Age distribution by `Sex`, grouped by `Survived` |
| **KDE curves** | Age distributions for passengers with `Survived = 0` and `Survived = 1` |
| **Heatmap** | Cross-tabulated counts of `Pclass` and `Survived` |
| **Cluster map** | Cross-tabulated counts of `Parch` and `Survived` |

These plots support visual comparison of passenger groups and survival categories. The notebook does not include a written statistical interpretation of the results.

### 3. Iris Dataset — Multivariate Feature Relationships

A Seaborn **pair plot**, colored by `species`, visualizes pairwise relationships among the Iris measurements. This is useful for exploring feature distributions and how observations from different species appear across feature combinations.

### 4. Flights Dataset — Passenger Trends Over Time

The Flights section includes:

- A **line plot** of `year` against `passengers`.
- A **pivot table** of passenger counts by `month` and `year`.
- A **heatmap** of that pivot table.
- A **cluster map** of the same month-by-year passenger matrix.

These visualizations offer complementary ways to inspect passenger counts over time.

## Tools and Libraries

| Tool | Usage |
| --- | --- |
| **Python** | Programming language |
| **Pandas** | DataFrames, CSV loading, cross-tabulations, and pivot tables |
| **Seaborn** | Statistical data visualization and built-in datasets |
| **Matplotlib** | Plot display and visualization support |
| **Jupyter Notebook** | Interactive execution and presentation of analysis |

## Repository Structure

```text
eda-multiple-datasets/
├── README.md
├── eda.ipynb
├── train.csv           # Required locally for Titanic analysis
└── requirements.txt    # Optional: recommended dependencies
```

**Note:** `train.csv` is not embedded in the notebook. Include it in the repository only if its source and license permit redistribution; otherwise provide a download/source link and setup instructions.

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/YOUR-USERNAME/eda-multiple-datasets.git
   cd eda-multiple-datasets
   ```

2. (Recommended) Create and activate a virtual environment:

   ```bash
   python -m venv .venv
   ```

   On Windows PowerShell:

   ```powershell
   .venv\Scripts\Activate.ps1
   ```

   On macOS/Linux:

   ```bash
   source .venv/bin/activate
   ```

3. Install the dependencies:

   ```bash
   pip install pandas seaborn matplotlib notebook
   ```

4. Place the Titanic `train.csv` dataset in the repository root, next to `eda.ipynb`.

5. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

6. Open `eda.ipynb` and run the cells from top to bottom.

## Example Code

**Tips: Multivariate scatter plot**

```python
sns.scatterplot(
    x='total_bill', y='tip', data=tips,
    hue='sex', style='smoker', size='size'
)
```

**Titanic: Passenger class and survival heatmap**

```python
sns.heatmap(pd.crosstab(titanics['Pclass'], titanics['Survived']))
```

**Iris: Pair plot**

```python
sns.pairplot(iris, hue='species')
```

**Flights: Month-by-year passenger heatmap**

```python
sns.heatmap(
    flights.pivot_table(values='passengers', index='month', columns='year')
)
```

## Skills Practiced

- Data loading and initial inspection with `.head()`
- Exploratory visualization of numerical and categorical variables
- Group comparisons and distribution analysis
- Cross-tabulations with `pd.crosstab()`
- Pivot tables with `pivot_table()`
- Scatter plots, bar plots, box plots, KDE curves, pair plots, line plots, heatmaps, and cluster maps
- Working with multiple datasets in one notebook

## Scope and Future Improvements

This notebook focuses on **visual EDA**. Potential next steps include:

- Add dataset summaries, missing-value checks, and descriptive statistics.
- Add Markdown explanations and conclusions after each visualization.
- Annotate heatmaps and improve plot titles, labels, and legends.
- Add screenshots of selected visualizations to the README.
- Document the original source of the Titanic `train.csv` file.
- Add a `requirements.txt` file for reproducible setup.

## Author

Created as a hands-on Python data analysis and visualization learning project.

---

If you find this project useful, consider starring the repository.
