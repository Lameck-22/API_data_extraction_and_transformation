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
