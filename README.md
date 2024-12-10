# Data-Scrapping

Overview
This script scrapes book data from the website http://books.toscrape.com, including the book name, price (in GBP and INR), availability, and rating. The scraper fetches data from multiple pages and stores the cleaned data in a CSV file (cleaned_books_data.csv).

Requirements
Before running the script, make sure you have the following Python libraries installed:

requests for making HTTP requests.
beautifulsoup4 for parsing HTML content.
pandas for data handling.
time for controlling the rate of requests to avoid overwhelming the server.
Script Functions
scrape_books_large(): This function scrapes all book data from the website across multiple pages. It extracts:

Book name
Price in GBP and INR (using a conversion rate of 1 GBP = 100 INR)
Availability (in stock or not)
Rating (mapped from star rating classes like "One", "Two", etc.)
The function loops through the pages until it finds no books on a page or encounters an error in the HTTP request. The scraped data is stored in a list, which is then converted into a Pandas DataFrame.

process_and_clean_data(df): This function processes and cleans the scraped data:

Removes duplicates from the DataFrame.
Drops rows with missing values.
Cleans the 'Price (GBP)' and 'Price (INR)' columns, removing currency symbols and converting them to numerical values.
Standardizes the 'Rating' column, converting it to numeric values.
Cleans the 'Availability' column by marking "In stock" as "Yes" and others as "No".
Renames columns to ensure consistency.
How to Run and Test
Run the Script: Simply execute the script in a Python environment. It will automatically begin scraping data from the books.toscrape.com website.

Testing:

Verify CSV Output: Check the output file cleaned_books_data.csv to ensure that the data has been correctly scraped and cleaned. The file should contain columns for book name, price, availability, and rating.
Test Data Quality: Inspect the cleaned data in the CSV file to ensure there are no duplicates, missing values, and that the columns have been standardized.
Error Handling:

If you encounter any issues with scraping, ensure that the website is accessible and that your internet connection is stable.
If the scraper stops at a particular page, it may be due to network issues or an invalid URL structure. Ensure that the base URL is correct and that you are not being blocked by the website for too many requests.
The script includes a delay (time.sleep(1)) between requests to avoid overwhelming the server.
