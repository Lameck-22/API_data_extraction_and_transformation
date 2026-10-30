## Overview
Duka Connect, a Nairobi-based B2B distributor, is onboarding a partner whose customer directory is only available through a REST API.
The analytics team wants that directory as a flat, tidy CSV they can join against their own sales data.
You are the data engineer on the job. The API returns nested JSON (addresses inside users, coordinates inside addresses, companies alongside).
Your script must fetch it reliably, understand its shape, pull out the fields that matter, flatten everything else, and export a CSV
that a spreadsheet user could open without surprises.
The partner's API is not always up, so the script has to fail politely rather than crash with a stack trace.

### Deliverables
- Retrieve JSON data from a REST API with the requests library and check the response before trusting it
- Identify the Python data structures (lists, dicts, nested dicts) a JSON payload becomes
- Use loops and comprehensions to build lists, tuples and dictionaries from raw records
- Flatten nested JSON into single-level records with a reusable function
- Load records into a pandas DataFrame and export a clean CSV
- Handle network and HTTP failures without crashing

### Steps and Guidelines used
1. Retrieve the users with requests.get()

Implement fetch_users(url, timeout) so it calls the users endpoint with requests.get(), passes a timeout, and returns the parsed JSON. Confirm the status code before using the body.

2. Identify the returned data structures

Implement describe_structure(payload) to print the type of the top-level payload, of one record, and of every nested value in that record. Record in your README which fields are nested and how deep they go.

3. Extract names, emails, cities and companies

Implement extract_core_fields(users) returning one small dict per user with id, name, email, city and company. A missing nested key must not crash the function — decide on a sensible default and document it.

4. Build lists, tuples and dicts with loops and comprehensions

Implement build_structures(users) returning a list of names, a list of (id, email) tuples, and a dict mapping id to city. Use at least one list comprehension, one dict comprehension and one plain for loop somewhere in the solution.

5. Flatten the nested JSON

Implement flatten_user(user, parent_key, sep) so any depth of nesting becomes underscore-joined keys (for example address_geo_lat). It must work for records it has never seen, not just these ten — do not hard-code field names.

6. Load the records into a DataFrame

Implement to_dataframe(flat_users) producing columns in the order shown in the expected-output resource, with id renamed to customer_id and coordinates converted to numbers. Print the DataFrame's shape and dtypes.

7. Export the cleaned CSV

Implement export_csv(df, path) to write output/customers_clean.csv without the pandas index, creating the folder if it does not exist. Re-running the script must overwrite, not append.

8. Handle API request failures

Make the script survive a wrong URL, a timeout, a non-200 response and a body that is not JSON: each should produce one clear message and a non-zero exit, never a raw traceback. Show in your README how you tested each case.
