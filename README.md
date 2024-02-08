# Industry Prediction Using OpenAI API

This repository contains a Python script that utilizes the OpenAI API to classify the industry of companies based on their names. It fetches data from a CSV file, processes it using the API, and provides predictions for each company's industry.

## Installation

1. Install necessary Python packages:
    ```
    !pip install openai==0.28
    !pip install pandas requests
    !pip install tqdm
    ```

2. Import required libraries:
    ```python
    import pandas as pd
    import openai
    import requests
    import re
    from tqdm import tqdm
    import time
    import numpy as np
    from google.colab import drive
    from google.colab import files
    ```

3. Mount Google Drive to access files:
    ```python
    drive.mount('drive')
    ```

4. Set your OpenAI API key:
    ```python
    openai.api_key = "GET-YOUR-OWN-API-KEY"
    ```

## Usage

1. Load your CSV file containing company data:
    ```python
    df = pd.read_csv('/content/drive/MyDrive/Location for your file/your_file.csv')
    ```

2. Split the data into chunks if necessary:
    ```python
    df = np.array_split(df, 5)
    ```

3. Classify the industry for each company:
    ```python
    for company_name in tqdm(df["company_name"], desc="Classifying industries"):
        predicted_industry = classify_company_industry(company_name)
        industries.append(predicted_industry)
    ```

4. Clean up and categorize the predicted industries:
    ```python
    # Clean up industry predictions
    for x in range(len(results_df)):
        industry_prediction = results_df["predicted_industry"][x].lower()
        # Add more cleanup logic if needed
    ```

5. Group detailed industries into general categories:
    ```python
    unique_values = df[df['general_industry'].eq('')]['predicted_industry'].unique()
    unique_values_list = list(unique_values)
    industry_mapping = group_industries_detailed_to_general(unique_values_list)
    ```

6. Save the results to a CSV file:
    ```python
    df.to_csv(f'Industry_prediction_fin.csv')
    ```

## Contact

For inquiries or feedback, please feel free to contact Marijn Quartel on LinkedIn: [Marijn Quartel](https://www.linkedin.com/in/marijnquartel/)
