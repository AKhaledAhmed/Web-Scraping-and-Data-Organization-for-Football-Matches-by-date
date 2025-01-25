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
