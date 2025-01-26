# Match Scraper

This project scrapes match data from a football statistics website and organizes it into a structured format. The data is then saved into an Excel file with sheets named according to the date of the scrape.

## Features

- **Web Scraping**: Fetches match data (teams, time, and scores) from a football statistics website.
- **Data Structuring**: Organizes the scraped data into a pandas DataFrame for easy manipulation.
- **Excel Export**: Saves the data into an Excel file (`matches.xlsx`) with sheets named by the date.
- **Error Handling**: Includes basic error handling for time format validation and missing data.

## Requirements

- **Python 3.x**
- **pandas**: For data manipulation and structuring.
- **BeautifulSoup4**: For parsing HTML content.
- **requests**: For making HTTP requests to fetch the webpage.
- **openpyxl**: For saving the data to an Excel file.

## Installation

1. **Clone the repository**:
    ```sh
    git clone https://github.com/your-username/match-scraper.git
    cd match-scraper
    ```

2. **Install the required packages**:
    ```sh
    pip install pandas beautifulsoup4 requests openpyxl
    ```

3. **Run the script**:
    ```sh
    python todays_matches_data.ipynb
    ```

## Usage

### Running the Script

- Execute the script using Python:
  ```sh
  python todays_matches_data.ipynb
  ## Output

- The output Excel file (`matches.xlsx`) will contain the following columns:
  - **Date**: The date when the data was scraped.
  - **Cup**: The league or tournament name.
  - **Team 1**: The first team in the match.
  - **Team 2**: The second team in the match.
  - **Time**: The scheduled time of the match or its current status (e.g., "Not started Yet", "on play", "Ended").
  - **Score**: The current score if the match is in progress or has ended, otherwise "Not started Yet".

- Each sheet in the Excel file will be named according to the date of the scrape (e.g., `Matches_2023-10-25`).

### Example Output (DataFrame)

```plaintext
           Date             Cup                   Team 1             Team 2  Time            Score
0    25/01/2025  Premier League          AFC Bournemouth  Nottingham Forest  15:00  Not started Yet
1    25/01/2025  Premier League   Brighton & Hove Albion            Everton  15:00  Not started Yet
2    25/01/2025  Premier League                Liverpool       Ipswich Town  15:00  Not started Yet
3    25/01/2025  Premier League              Southampton   Newcastle United  15:00  Not started Yet
4    25/01/2025  Premier League  Wolverhampton Wanderers            Arsenal  15:00  Not started Yet
...
```
## Automation with GitHub Actions

This project uses GitHub Actions to automatically run the Jupyter Notebook every 30 minutes. The workflow is defined in the `.github/workflows/run_notebook.yml` file.

### Setting Up GitHub Actions

1. **Create the Workflow File**:
   - In your repository, create a directory called `.github/workflows`.
   - Inside this directory, create a file named `run_notebook.yml`.

2. **Define the Workflow**:
   - Add the following content to `run_notebook.yml`:

```yaml
name: Run Jupyter Notebook

on:
  schedule:
    - cron: '*/30 * * * *'  # This cron expression schedules the job to run every 30 minutes
  push:
    branches:
      - main  # Adjust this to your default branch

jobs:
  run-notebook:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.x'  # Specify the Python version you need

    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install pandas beautifulsoup4 requests openpyxl jupyter nbconvert

    - name: Run Jupyter Notebook
      run: |
        jupyter nbconvert --to notebook --execute todays_matches_data.ipynb --output executed_notebook.ipynb

    - name: Commit and push changes
      run: |
        git config --global user.name 'github-actions'
        git config --global user.email 'github-actions@github.com'
        git add matches.xlsx
        git commit -m 'Update matches.xlsx'
        git push
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
