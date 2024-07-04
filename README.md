# etl_llm_thesis
# Optimizing ETL Pipelines through the Integration of Language Models
Application of Large Language Models for Data Extraction, Transformation, and Loading


# Repository Structure
```
etl-llm (root directory of the repository)
├── TrainingData (Contains data used for training models)
│   └── ... (Add specific files and descriptions here)
├── schema (Contains schema definitions and related files)
│   └── ... (Add specific files and descriptions here)
├── evaluations (Contains evaluation results and scripts)
│   └── ... (Add specific files and descriptions here)
├── metrics (Contains metrics results and scripts)
│   └── ... (Add specific files and descriptions here)
└── notebooks (Contains Jupyter notebooks for experimentation and analysis)
    └── ... (Add specific files and descriptions here)
```




# Training Data Preparation Flow
## Dataset
In evaluating Language Learning Models (LLMs), AdventureWorks database is used. This repository outlines the process for preparing training data from the AdventureWorks database. The workflow involves retrieving schemas from all tables in the correct order, extracting data without headers, creating schema JSON files, generating a training dataset formatted as "prompt" and "response," and shuffling the data for model training. 
