# Gym Exercise Safety Analytics & Recommendation Engine

## Executive Summary

This project delivers a comprehensive end-to-end data pipeline focused on the analysis and recommendation of gym exercises based on safety profiles. By leveraging automated Extract, Transform, Load (ETL) processes and Machine Learning techniques, the system curates exercise data, predicts safety scores, and provides interactive recommendations tailored to user capability levels.

## Key Features

*   **Automated Data Pipeline**: A robust ETL workflow that extracts raw data from Kaggle, cleanses and normalizes it, and prepares it for analytical modeling.
*   **Predictive Analytics**: Utilizes K-Nearest Neighbors (KNN) regression with Hyperparameter Tuning (GridSearchCV) to model and predict exercise safety ratings.
*   **Intelligent Data Handling**: Implements sophisticated imputation strategies for missing values, including mean imputation based on proficiency levels and categorical encoding.
*   **Interactive User Interface**: Features a CLI-driven visualization tool that generates personalized exercise recommendations based on muscle groups and safety thresholds.
*   **Comprehensive Logging**: Integrated logging system for monitoring pipeline health, debugging protocols, and execution tracking.

## System Architecture

The project is structured into modular components ensuring maintainability and scalability:

1.  **Data Extraction**: Interacts with the Kaggle API to programmatically retrieve the latest gym exercise datasets.
2.  **Data Transformation**:
    *   Normalization of proficiency levels (Beginner, Intermediate, Advanced).
    *   Statistical imputation for missing ratings.
    *   Standardization of equipment metadata.
3.  **Machine Learning & Analysis**:
    *   **Prescriptive Analysis**: Generates actionable datasets for downstream reporting.
    *   **Descriptive Analysis**: Evaluates model performance using MSE, MAE, and $R^2$ metrics.
4.  **Visualization**: Renders visual infographics for exercise distribution and recommendations.

## Technical Requirements

*   **Python 3.11+**
*   **Kaggle API** (for data retrieval)
*   **Key Libraries**: `pandas`, `numpy`, `scikit-learn`, `plotly`, `matplotlib`

## Installation & Setup

### 1. Prerequisite Configuration
Ensure you have a valid Kaggle API token (`kaggle.json`).
1.  Download your API token from your Kaggle account settings.
2.  Place the `kaggle.json` file in your user directory:
    *   **Windows**: `C:\Users\<Username>\.kaggle\kaggle.json`
    *   **Linux/Mac**: `~/.kaggle/kaggle.json`

### 2. Repository Setup
Clone the project and install dependencies:

```bash
git clone <repository-url>
cd ETL-Analysis
python -m pip install -r requirements.txt
```

## Usage

The entire pipeline is orchestrated via a single entry point for ease of use.

### Execute Pipeline
Run the main control script to trigger the full workflow (Extraction -> Transformation -> Analysis -> Visualization):

```bash
python main.py
```

### Module Descriptions
*   **`etl/extract.py`**: Handles authentication and data fetching.
*   **`etl/transform.py`**: Performs data cleaning, encoding, and imputation.
*   **`analysis/knn_regression_and_summary.py`**: Trains the ML model and outputs performance metrics.
*   **`vis/visualizations.py`**: Launches the interactive recommendation visualizer.

## Analytical Methodology

The core analytical engine employs a K-Nearest Neighbors (KNN) regressor to predict safety scores suitable for different user levels. The model optimization process helps identify the ideal number of neighbors ($k$) to minimize error rates (MSE).

*   **Data Quality**: Missing ratings are imputed using the mean rating of the respective proficiency level to ensure dataset integrity without introducing significant bias.
*   **Evaluation**: The model is rigorously tested against a hold-out test set, with results visualized via regression plots comparing Predicted vs. Actual safety scores.

## Project Structure

```
ETL-Analysis/
├── analysis/               # Analytical scripts and ML models
├── data/                   # Data storage (raw, processed, reference)
├── etl/                    # Extraction and Transformation scripts
├── log/                    # Runtime logs
├── vis/                    # Visualization modules
├── main.py                 # Application entry point
└── requirements.txt        # Project dependencies
```

## Logging

Execution logs are automatically generated in the `log/` directory (e.g., `gym_project.log`). These logs provide granular details on process execution, successful transactions, and error stack traces.

---
*Developed for advanced exercise analytics and safety modeling.*
