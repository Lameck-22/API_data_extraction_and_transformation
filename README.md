## Overview
This repository contains a Python-based data engineering pipeline designed to fetch nested JSON data from a REST API, flatten the data structures, and transform it into a clean, flat CSV file using Pandas. The project is modeled around Duka Connect, a Nairobi-based B2B distributor onboarding a partner's customer directory


__*Key Features & Deliverables*__

The script implements a robust data extraction and transformation workflow, including:
1. API Extraction: Fetches data reliably using the requests library with built-in error handling for timeouts, invalid URLs, and bad status codes.
2. JSON Flattening: Employs a dynamic, reusable flattening function (flatten_user) that handles multi-layered, nested JSON objects (like coordinates inside addresses) without hardcoding field names.
3. Data Transformation: Utilizes Python loops, list/dictionary comprehensions, and pandas DataFrames to clean data types, rename columns (e.g., id to customer_id), and format data.
4. Clean Export: Automatically creates an output/ directory and writes a flat customers_clean.csv ready for spreadsheet analysis

### Project Setup Instructions
Since the repository already contains pyproject.toml and a uv.lock file, using uv is the fastest and most seamless way to run this project. It will read the lockfile and install the exact pinned dependencies instantly.

__1. Clone this repository__
- To clone this repository, run:
```
git clone https://github.com/Lameck-22/API_data_extraction_and_transformation.git
cd API_data_extraction_and_transformation
```

__2. Initialize and Install Dependencies__
- You don't need to manually create a virtual environment; uv handles it automatically when you sync the lockfile. Run the following command in the project root folder.
```
uv sync
```
*This command creates a .venv directory and installs the precise versions of pandas, requests, and any other dependencies specified in uv.lock*

__3. Run the Script__
- To run the script within the context of the managed environment, use uv run
```
uv run extract_customers.py
```

## Error Handling
- Error handling was implemented using a try-except block to identify and report four common API errors: connection failures, request timeouts, non-200 HTTP status codes, and invalid JSON responses. Each error produces a clear message to help identify the problem, while sys.exit(1) terminates the program to prevent further processing of invalid or missing data.
