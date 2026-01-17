📊 FBref Premier League Match Data Scraper

A robust Python web-scraping project built to collect Premier League match-level data across multiple seasons from FBref — a website known for Cloudflare protection, dynamic page loading, and hidden HTML tables.

This project uses a hybrid scraping approach combining Selenium and Cloudsraper to reliably extract football statistics that cannot be accessed using simple request-based methods.

🔍 Project Overview

FBref is one of the most widely used football statistics platforms, but scraping data from it is difficult due to:

Cloudflare anti-bot protection

JavaScript-rendered pages

Tables hidden inside HTML comments

Column names that change across seasons

This scraper was designed to handle all of these issues automatically and produce a clean, structured dataset suitable for analysis, visualization, or machine learning.

⚙️ Features

✅ Multi-season scraping (automatic season navigation)

✅ Hybrid scraping system (Selenium + Cloudsraper)

✅ Bypasses request blocking and rate limiting

✅ Extracts teams dynamically from standings tables

✅ Parses hidden HTML tables inside comments

✅ Handles renamed statistical columns across seasons

✅ Robust retry and timeout logic

✅ Randomized user agents and request delays

✅ Automatic backup saving during execution

✅ Final merged dataset exported as CSV

🧠 Why This Project Is Difficult

This is not a basic scraping script.

Several real-world problems had to be solved.

1. Anti-Bot & DDoS Protection

FBref limits repeated requests and uses Cloudflare protection.

To reduce blocking, this project uses:

Multiple request methods

Selenium (browser-based simulation)

Cloudsraper (Cloudflare-aware requests)

Random user-agent rotation

Random sleep delays between requests

Retry logic with exponential backoff

This allows the scraper to continue running even when some requests fail.

2. Loop-Based Crawling Logic

The scraper relies heavily on for-loop based crawling, similar to real data-collection pipelines:

Loop through multiple seasons

Loop through all teams per season

Loop through match and shooting data

Merge statistics per team and season

Each loop includes error handling so the program does not stop when a single page fails.

3. Hidden HTML Tables

FBref hides many important tables inside HTML comments:

<!-- <table> ... </table> -->


Standard parsers cannot read these tables.

This project automatically removes the comment tags and reconstructs valid HTML tables before parsing them.

4. Dynamic Column Name Changes

Column names on FBref change between seasons, for example:

Sh → Shots

SoT → Shots on Target

Dist → Average Shot Distance

Hardcoding column names would cause failures.

This scraper dynamically matches column names using keyword detection, allowing it to work across different seasons without manual modification.

🧪 Technologies Used

Python

Selenium

Cloudsraper

BeautifulSoup

pandas

webdriver-manager

📁 Output Files

premier_league_combined.csv
Final merged dataset containing all Premier League matches scraped.

fbref_partial_backup.csv
Automatic backup file saved during execution to prevent data loss.

▶️ How to Run
pip install -r requirements.txt
python scraper.py


⚠️ Scraping may take time due to intentional delays added to avoid rate-limiting and blocking.

📌 Possible Use Cases

Football data analysis

Sports analytics research

Match performance evaluation

Machine learning preprocessing

Data visualization projects

⚠️ Disclaimer

This project is intended for educational and research purposes only.
Please respect FBref’s terms of service and avoid excessive scraping.

📊 Project Evaluation (GPT Assessment)

Overall Rating: ⭐ 4.6 / 5

Evaluation Parameters (Max 5)
Parameter	Description	Score
Technical Difficulty	Cloudflare handling, dynamic HTML, multi-season crawling	5.0
Engineering Design	Retry logic, autosave, stability	4.5
Real-World Practicality	Reflects real data-collection workflows	5.0
Code Structure	Modular helpers and readable logic	4.0
Portfolio Value	Strong GitHub showcase project	4.5

Final Verdict:
This project demonstrates real-world scraping engineering rather than tutorial-level scripting. It reflects an understanding of website protection, unstable data structures, and long-running data pipelines, making it suitable for a GitHub portfolio, research preparation, or data-focused internship applications.
