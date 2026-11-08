## Overview
This repository contains a Python-based data engineering pipeline designed to fetch nested JSON data from a REST API, flatten the data structures, and transform it into a clean, flat CSV file using Pandas. The project is modeled around Duka Connect, a Nairobi-based B2B distributor onboarding a partner's customer directory


*Key Features & Deliverables*

The script implements a robust data extraction and transformation workflow, including:
1. API Extraction: Fetches data reliably using the requests library with built-in error handling for timeouts, invalid URLs, and bad status codes.
2. JSON Flattening: Employs a dynamic, reusable flattening function (flatten_user) that handles multi-layered, nested JSON objects (like coordinates inside addresses) without hardcoding field names.
3. Data Transformation: Utilizes Python loops, list/dictionary comprehensions, and pandas DataFrames to clean data types, rename columns (e.g., id to customer_id), and format data.
4. Clean Export: Automatically creates an output/ directory and writes a flat customers_clean.csv ready for spreadsheet analysis

### Project Setup Instructions
__1. Clone this repository__
To clone this repository, run:
```
git clone https://github.com/Lameck-22/API_data_extraction_and_transformation.git
cd API_data_extraction_and_transformation
```


__2. Environment Setup__

The project uses uv or standard pip for dependency setup. If you are using standard pip, you can set it up by running:
```
# Create a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows use: .venv\Scripts\activate

# Install required dependencies (pandas, requests, etc.)
pip install -r requirements.txt
```

Error Handling

Error handling was implemented using a try-except block to identify and report four common API errors: connection failures, request timeouts, non-200 HTTP status codes, and invalid JSON responses. Each error produces a clear message to help identify the problem, while sys.exit(1) terminates the program to prevent further processing of invalid or missing data.
