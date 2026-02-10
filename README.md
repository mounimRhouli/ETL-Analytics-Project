# Gym Safety Analytics & Recommendation System

## Executive Summary

This project delivers a comprehensive data engineering and analytics solution designed to evaluate and enhance gym exercise safety. By leveraging an automated ETL (Extract, Transform, Load) pipeline, the system processes exercise metadata to calculate safety scores, classify techniques by difficulty, and generate data-driven recommendations. The initiative aims to mitigate injury risks and improve client retention through actionable insights and accessible visualizations.

## Business Context

Unsafe training practices represent a significant liability and safety hazard within fitness environments. This solution addresses these challenges by determining objective safety metrics for various exercises. The resulting recommendation engine aids in curating safer workout routines, customized by difficulty level and specific muscle groups, ultimately fostering a safer training environment.

## Technical Methodology

The project employs a modular Python-based architecture utilizing the following techniques:

- **ETL Automation**: Seamless extraction and transformation of raw exercise datasets.
- **Data Engineering**: Robust handling of missing data using Mean Imputation strategies and categorical variable encoding.
- **Predictive Modeling**: Implementation of K-Nearest Neighbors (KNN) algorithms to predict exercise safety scores.
  - **Hyperparameter Optimization**: Usage of GridSearchCV for optimal neighbor selection.
  - **Model Evaluation**: Rigorous testing using MSE (Mean Squared Error), MAE (Mean Absolute Error), and $R^2$ metrics.
- **Visualization**: Generation of both technical model performance plots and user-facing clustering diagrams.

## Repository Structure

The codebase is organized into distinct logical modules to ensure meaningful separation of concerns:

```text
├── analysis/               # Analytical logic and model evaluation
│   ├── descriptive_analysis.py
│   └── prescriptive_analysis.py
├── data/                   # Data storage layer
│   ├── downloaded/         # Raw ingestion stage
│   └── processed/          # Transformed analytical datasets
├── etl/                    # Extraction & Transformation pipeline
│   ├── extract.py
│   └── transform.py
├── log/                    # System runtime logs
│   └── gym_project.log
├── outputs/                # Analytical deliverables
│   ├── descriptive_analysis.csv
│   └── prescriptive_analysis.csv
├── vis/                    # Visualization generation
│   └── visualizations.py
├── main.py                 # Application entry point/Orchestrator
└── requirements.txt        # Project dependencies
```

## Data Assets

The analysis is driven by the **Mega Gym Dataset** (`megaGymDataset.csv`), incorporating detailed attributes such as:
- Exercise Type & Description
- Target Body Part & Muscle Groups
- Equipment Requirements
- Difficulty Ratings

## Getting Started

### Prerequisites
- Python 3.11 or higher
- Kaggle API Account (for data ingestion)

### Configuration & Installation

1. **Kaggle API Setup**:
   To facilitate automated dataset downloads, configure your Kaggle credentials:
   - Generate an API token (`kaggle.json`) from your Kaggle account settings.
   - Securely place the file in your home directory:
     - **Windows**: `%USERPROFILE%/.kaggle/kaggle.json`
     - **Linux/Mac**: `~/.kaggle/kaggle.json`

2. **Environment Installation**:
   Clone the repository and install the required dependencies:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   # Recommended: Create and activate a virtual environment
   pip install -r requirements.txt
   ```

### Execution

To execute the full pipeline—including ETL, analysis, logging, and visualization generation—run the application entry point:

```bash
python main.py
```

### Logging & Debugging

The system maintains detailed execution logs in `log/gym_project.log`. This includes timestamped entries for process start/completion, error tracking, and information levels to assist with debugging and auditability.

## Outputs & Deliverables

- **Statistical Reports**: Detailed descriptive statistics of the exercise landscape.
- **Safety Recommendations**: Prescriptive analysis outputting exercise suggestions based on calculated safety scores.
- **Visual Analytics**: 
  - Hierarchical clustering of exercises.
  - Model proficiency graphs comparing predicted vs. actual safety metrics.
