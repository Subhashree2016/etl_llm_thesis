# Optimizing ETL Pipelines through the Integration of Language Models
Application of Large Language Models for Data Extraction, Transformation, and Loading.

# Table of Contents

1. [Overview](#overview)
2. [Repository Structure](#RepositoryStructure)
3. [Installation](#installation)
4. [Data](#Dataset)
5. 
6. [Usage Instructions](#Usage-Instructions)
7. [Acknowledgements](#acknowledgements)

# Overview
# Repository Structure
```
etl-llm (root directory of the repository)
├── TrainingData (Contains data used for training models)
│  └── processed_data_adw_full_shuffledrows.csv- Training dataset created using the schema and data from base tables (200 records from every base table in AdventureWorks database)
    └── processed_data_training_shuffledrows.csv - Training dataset created using the schema and data from base tables 
├── schema (Contains schema definitions and related files)
│   ├── schema_adventureadw/- This directory contains the schema definitions and json files for the AdventureWorks tables.
    ├── Adventuredataset_WH/ - This directory includes the dataset files for the AdventureWorks base tables without header information.
    └── adventureworks_tableschema_sequence.csv - Schema extracted from AdventureWorks database for all base tables-
├── evaluations (Contains evaluation results and scripts)
│   ├── T5/ (Evaluation metrics for all the dataset sampling saved in CSV for T5 model)
    ├── Bert/ (Evaluation metrics for all the dataset sampling saved in CSV for Bert model)
        └──metrics_df_bert_small.csv: Performance metrics of the BERT model evaluated on a small dataset.
        └──metrics_df_bert_medium.csv: Performance metrics of the BERT model evaluated on a medium dataset.
        └──metrics_df_bert_large.csv: Performance metrics of the BERT model evaluated on a large dataset.
        └──metrics_df_bert_new.csv: Performance metrics of a newly evaluated BERT model, possibly with different configurations or a new dataset.
        └──true_pred_labels_small.json: True and predicted labels of the BERT model on a small dataset.
        └──true_pred_labels_medium.json: True and predicted labels of the BERT model on a medium dataset.
        └──true_pred_labels_large.json: True and predicted labels of the BERT model on a large dataset.
├── metrics (Contains notebook to generate model's performance in detail and for performing further analyses such as confusion matrix computation, performance analysis, and more)
│   └── metrics.ipynb (Add specific files and descriptions here)
└── notebooks (Contains Jupyter notebooks for experimentation and analysis)
    └── Data Processing.ipynb (Retreives the schema from adventureworks database,data amd preprocesses the data to generate the training dataset)
    └── Bert_model_schema_training.ipynb (Bert base model trained on AdventureWorks schema)
    └── t5_small_model.ipynb (T5 small model trained on AdventureWorks schema)
```


# Training Data Preparation Flow
## Dataset
In evaluating Language Learning Models (LLMs), AdventureWorks database is used. This repository outlines the process for preparing training data from the AdventureWorks database. The workflow involves retrieving schemas from all tables in the correct order, extracting data without headers, creating schema JSON files, generating a training dataset formatted as "prompt" and "response," and shuffling the data for model training. 
## Setting Up PostgreSQL for Data processing

For data processing, a local installation of PostgreSQL is required. Follow the steps below to set up PostgreSQL and connect to it from your local environment.

1. **Install PostgreSQL**:
   - Download and install PostgreSQL from the [official website](https://www.postgresql.org/download/).
   - During the installation, set a password for the PostgreSQL superuser (postgres).

2. **Set Up a Database**:
   - Open the PostgreSQL shell (psql) and create a new database:
     ```sql
     CREATE DATABASE your_database_name;
     ```

3. **Install psycopg2**:
   - Ensure `psycopg2` is installed in your Python environment:
     ```sh
     pip install psycopg2
     ```

4. **Connect to PostgreSQL**:
   - Use the following code snippet to connect to your PostgreSQL database in your Python scripts:
     ```python
     import psycopg2

     # Establish a connection to the PostgreSQL database
     connection = psycopg2.connect(
         host="localhost",
         database="your_database_name",
         user="your_postgres_user",
         password="your_postgres_password"
     )

     # Create a cursor object
     cursor = connection.cursor()

     # Execute queries
     cursor.execute("SELECT * FROM your_table_name;")
     results = cursor.fetchall()

     # Close the connection
     cursor.close()
     connection.close()
     ```

## Usage Instructions

1. **Set Up**:
   - Ensure all required libraries are installed. Install the required dependencies using:  ``` pip install -r requirements.txt ```
   - Place your datasets in the `TrainingData` directory.

2. **Running Scripts**:
   - Navigate to the notebooks directory.
   - Open the desired notebook (Bert_model_schema_training.ipynb or t5_small_model.ipynb) in Google Colab or your preferred Jupyter environment.  

3. **Evaluating Models**:
   - Use the script in the `metrics` directory (metrics.ipynb) to evaluate model performance.
   - Results will be stored in the `evaluations` directory.

4. **Plotting Results**:
   - Use the `metrics.ipynb` notebook to visualize the results after training the model.


