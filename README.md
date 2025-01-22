# Web-Scraping-and-Data-Organization-for-todays-Football-Matches

## Requirements

- Python 3.x
- pandas
- BeautifulSoup4
- requests

## Installation

1. Clone the repository:
    ```sh
    git clone <repository-url>
    cd <repository-directory>
    ```

2. Install the required packages:
    ```sh
    pip install pandas beautifulsoup4 requests
    ```

## Usage

1. Run the [train.py](http://_vscodecontentref_/6) script to scrape the match data and save it to [matches.csv](http://_vscodecontentref_/7):
    ```sh
    python train.py
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

## Example

Example of the output DataFrame:
