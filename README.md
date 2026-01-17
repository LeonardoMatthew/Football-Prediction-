# 📊 FBref Premier League Match Data Scraper

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![Scraping Framework](https://img.shields.io/badge/library-Selenium%20%2B%20Cloudscraper-orange.svg)](https://github.com/VeNoMouS/cloudscraper)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A robust Python web-scraping engine built to collect Premier League match-level data across multiple seasons from **FBref**. This project is specifically engineered to handle Cloudflare protection, dynamic page loading, and hidden HTML data structures.

---

## 🔍 Project Overview

FBref is a gold mine for football statistics, but it is notoriously difficult to scrape. This project implements a **hybrid scraping architecture** to reliably extract data that standard request-based methods cannot reach.

### Why this is a challenge:
1.  **Anti-Bot Protection:** Strict Cloudflare challenges and rate-limiting.
2.  **JavaScript Rendering:** Dynamic content that requires browser simulation.
3.  **Hidden Data:** Key statistical tables are often wrapped inside HTML comments `` to bypass standard parsers.
4.  **Schema Drift:** Column names (e.g., `Sh` vs `Shots`) change between seasons.

---

## ⚙️ Key Features

* ✅ **Multi-Season Scraping:** Automatic navigation through historical seasons.
* ✅ **Hybrid System:** Uses **Selenium** for browser simulation and **Cloudscraper** for Cloudflare clearance.
* ✅ **Comment Parsing:** Custom logic to extract and reconstruct tables hidden within HTML comments.
* ✅ **Dynamic Mapping:** Keyword-based column detection to handle seasonal naming variations.
* ✅ **Resilience:** Includes randomized user-agents and exponential backoff retry logic.
* ✅ **Data Safety:** Automatic backup saving (`.csv`) during execution to prevent data loss.

---

## 🧠 Engineering Highlights

### 1. Defensive Scraping
To mimic human behavior and avoid IP bans, the script implements:
* **Randomized Delays:** `time.sleep()` intervals between requests.
* **User-Agent Rotation:** Prevents fingerprinting by rotating browser headers.
* **Retry Logic:** Automatically handles failed requests without crashing the entire pipeline.

### 2. The "Hidden Table" Solution
Most scrapers fail on FBref because data is hidden in comments. This project uses a specialized approach to strip comment tags, allowing BeautifulSoup to "see" and parse the data correctly.

### 3. Loop-Based Crawling Logic
The scraper follows a production-grade data pipeline:
1.  **Outer Loop:** Iterates through selected seasons.
2.  **Middle Loop:** Identifies and visits every team link from the standings table.
3.  **Inner Loop:** Merges match logs with specific shooting/performance metrics.

---

## 🧪 Tech Stack

* **Language:** Python 3.x
* **Libraries:** * `Pandas`: For data manipulation and CSV export.
    * `BeautifulSoup4`: For HTML parsing and comment extraction.
    * `Selenium`: For handling dynamic JavaScript content.
    * `Cloudscraper`: To bypass Cloudflare V2/V3 protections.
    * `Webdriver-manager`: For automated Chrome driver handling.

---

## 📁 Output Files

| File Name | Description |
| :--- | :--- |
| `premier_league_combined.csv` | Final merged dataset containing all scraped match data. |
| `fbref_partial_backup.csv` | Automatic backup file saved during execution. |

---

## ▶️ Getting Started

### Installation
1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/fbref-scraper.git](https://github.com/yourusername/fbref-scraper.git)
   cd fbref-scraper
