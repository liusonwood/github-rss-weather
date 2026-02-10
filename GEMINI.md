# Project Context: Shanghai Weather RSS Feed

## Overview
This project automates the generation of an RSS feed (`weather.xml`) containing the daily weather forecast for Shanghai. It utilizes a Python script to fetch data from the QWeather API and GitHub Actions to schedule the update and commit the changes back to the repository.

## Key Files
- **`fetch_weather.py`**: The core Python script that:
    1.  Fetches the daily weather forecast from the QWeather API.
    2.  Parses the JSON response.
    3.  Generates an RSS 2.0 compliant XML file.
- **`weather.xml`**: The generated RSS feed file. This is the artifact that users subscribe to.
- **`.github/workflows/weather.yml`**: The GitHub Actions workflow definition that runs the script daily at 20:00 UTC and handles the git commit/push process.
- **`requirements.txt`**: Lists the Python dependencies (primarily `requests`).

## Setup & Usage

### Environment Variables
The application requires the following environment variables to function:
- `QWEATHER_KEY`: Your QWeather API Key.
- `QWEATHER_HOST`: The API host provided by QWeather (e.g., `xxx.re.qweatherapi.com`).

### Automation (GitHub Actions)
The workflow is configured to:
1.  Checkout the code.
2.  Set up Python 3.10.
3.  Install dependencies.
4.  Run `fetch_weather.py` with secrets injected as environment variables.
5.  Commit and push `weather.xml` .

## Conventions
- **Output File:** The script appends the new forecast to `weather.xml` in the project root, maintaining a history of past weather.
- **Location:** Hardcoded to Shanghai (`101020100`) in `fetch_weather.py`.
- **Commit Identity:** Automated commits use "Weather Bot" as the user name.
