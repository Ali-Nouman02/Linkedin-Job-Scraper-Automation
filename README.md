# LinkedIn Job Scraper and Excel Tracker Automation 

A Python-based project that uses the Apify LinkedIn Jobs Scraper Actor to collect current LinkedIn job listings and maintain them in an Excel workbook.
My Goal is that the user does not need to manually search for Jobs but rather can completely rely on the Output from this script to find relevant position. 
This script can be run at regular intervals to update the Excel sheet with more jobs and remove jobs that are not suitable for the user.

The Project is dynamic and is intended to support all fields/categories of jobs 
For the purpose of illustration: The current implementation focuses on Financial Analyst searches.

## General Script Structure

The project is intended to automate the following process:

1. Search LinkedIn job listings through the Apify API.
2. Retrieve fresh job data as JSON.
3. Convert the JSON response into pandas.
4. Clean and standardize the job data.
5. Remove duplicate listings using `jobId`.
6. Store jobs in an Excel workbook.
7. Keep different job categories on separate worksheets.
8. Preserve existing jobs between runs.
9. Track applications and unwanted jobs.
10. Maintain a daily run log.

## Blacklist CSV

- If user marks a job with "X" in Excel file then on the next script run the job id is added into the Blacklist CSV 
- That job position is removed from the Excel file and if fetched again through api will not be added to the Excelsheet
- Script also adds conditional formating to the Excel file to mark that row "light red" if marked with X

## Daily Log CSV

- This tracks info everytime the script runs. It saves info such as when the script was executed. 
- Which sheet jobs were added too. How jobs were fetched from API. How many jobs were removed and How many were added to Excel sheet

# Configuration 

This project uses the Apify `cheap_scraper/linkedin-job-scraper` Actor to collect LinkedIn job listings.

[Open the Apify Actor input and configuration page](https://console.apify.com/actors/2rJKkhh7vjpX7pvjg/input)

Currently i set to fetch max 150 jobs per fetch. The jobs actually written to Excel ouput might be less as i intend 
to keep only the most relevant positions per category. Quality over Quantity is the Goal.

## API used in Script

## Features

- Supports multiple LinkedIn search URLs
- Switches between fresh Apify runs and previous already fetched datasets (for testing purposes)
- Converts API JSON results into pandas
- Removes duplicate jobs using `jobId`
- Maintains Excel worksheets by job sector
- Tracks comments, applications, and unwanted jobs
- Maintains a persistent blacklist
- Adds daily run logs
- Formats and conditionally formats the Excel output

## Setup

1. Install the required packages.
2. Create a local `.env` file.
3. Add the Apify API token and LinkedIn search URLs.
4. Open `job_scraper.ipynb`.
5. Select the correct Python kernel.
6. Run the cells from top to bottom.
