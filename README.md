# Match Scraper

This project scrapes match data from a website and organizes it into a structured format. The data is then saved into a CSV file.

# Project Structure

## Requirements

- Python 3.x
- pandas
- BeautifulSoup4
- requests

## Installation

1. Install the required packages:
    ```sh
    pip install pandas beautifulsoup4 requests
    ```

2. The script will print the scraped data in both dictionary and DataFrame formats, and save the DataFrame to [matches.csv](http://_vscodecontentref_/8).

## Output

The output CSV file [matches.csv](http://_vscodecontentref_/9) will have the following columns:
- Date
- Cup
- Team 1
- Team 2
- Time
- Score
