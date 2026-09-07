# Walmart-Product-ETL

A data engineering project that extracts, transforms, and loads (ETL) product data scraped from Walmart's website, demonstrating a practical end-to-end pipeline from web scraping to data visualization and insight generation, developed as a group project for the TTTC3213 Data Engineering course.

## Table of Contents

- [Overview](#overview)
- [Objective](#objective)
- [Group Members](#group-members)
- [Getting Started](#getting-started)
- [Tech Stack](#tech-stack)
- [ETL Pipeline](#etl-pipeline)
- [Dataset](#dataset)
- [Key Insights](#key-insights)
- [Challenges and Solutions](#challenges-and-solutions)
- [References](#references)
- [Disclaimer](#disclaimer)

## Overview

This walks through a complete ETL pipeline built in Python: scraping laptop product listings from Walmart's search results, cleaning and structuring the raw data, and analyzing it for insights such as pricing trends and customer review patterns.

A full write-up of the project is available on Medium: [Mastering Walmart Product ETL: A Data Engineering Journey from Web Scraping to Insights](https://jonathanafernandi.medium.com/mastering-walmart-product-etl-a-data-engineering-journey-from-web-scraping-to-insights-b0a008bdeb19).

## Objective

To scrape product data from Walmart's website, transform it into a structured format, and analyze the data for insights such as pricing trends and customer reviews.

## Group Members

| Name | Student ID |
|---|---|
| Jonathan Alvindo Fernandi | A207961 |
| Kevin Maverick | A208051 |
| Lai Junlin | A197837 |

**Course**: TTTC3213 Data Engineering (Set 6, Group INT-2)

**Special thanks to:**
- Prof. Madya Dr. Sabrina Tiun (Lecturer)
- Prof. Madya Dr. Ravie Chandren A/L Muniyandi (Laboratory Instructor)

## Getting Started

### Prerequisites

- Python 3.x
- Jupyter Notebook or Google Colab

### Installation

```bash
git clone https://github.com/jonathanafernandi/Walmart-Product-ETL.git
cd Walmart-Product-ETL
pip install requests beautifulsoup4 pandas numpy matplotlib seaborn
```

### Running the Notebook

Open `Walmart_Product_ETL.ipynb` in Jupyter Notebook, or run it directly in Google Colab, and execute the cells sequentially to perform scraping, cleaning, transformation, and visualization.

## Tech Stack

| Purpose | Library |
|---|---|
| Web Scraping | `requests`, `BeautifulSoup` (bs4) |
| Data Manipulation | `pandas`, `numpy` |
| Data Visualization | `matplotlib`, `seaborn` |
| Supporting Utilities | `json` (parsing JSON responses), `time` (request throttling), `re` (regular expressions) |

## ETL Pipeline

### 1. Extract: Web Scraping

The `scrape_product_data` function sends HTTP requests to Walmart's search results pages and extracts product details (name, price, rating, number of reviews, and product URL). Key techniques used:

- **Browser-mimicking headers** to reduce the risk of being blocked by Walmart's anti-scraping mechanisms.
- **JSON parsing** — Walmart embeds product data inside a `<script id="__NEXT_DATA__">` tag, which is parsed using Python's `json` module.
- **Pagination support**: iterates through multiple search result pages by appending page parameters to the search term.
- **Request throttling**: a `time.sleep(2)` delay between requests to avoid overloading Walmart's servers and reduce the likelihood of being rate-limited.
- **Error handling**: scraping continues gracefully even if individual products or pages fail to load.

### 2. Transform: Data Cleaning and Structuring

- Raw scraped data (a list of dictionaries) is converted into a structured `pandas` DataFrame.
- A `clean_data` function handles missing values and ensures consistency across columns (e.g., replacing missing price or rating fields with defaults).
- Derived columns are added for analysis, including `rating_rounded` and `price_category` (Cheap, Standard, Moderate, Expensive).

### 3. Load: Data Export

- The cleaned and transformed DataFrame is exported to `walmart_products.csv` using `pandas.to_csv()` (without the index column).
- The exported file is read back with `pd.read_csv()` to verify that the export preserved data integrity.

### 4. Analysis and Visualization

- **Count plots** visualize the frequency of ratings, segmented by rounded rating and by RAM size.
- **KDE (Kernel Density Estimation) plots** visualize the distribution of ratings across different price categories.

## Dataset

The final dataset (`walmart_products.csv`) contains the following columns:

| Column | Description |
|---|---|
| `name` | Product title as listed on Walmart |
| `price` | Product price (USD) |
| `rating` | Average customer rating |
| `number_of_reviews` | Total number of customer reviews |
| `url` | Direct link to the product page |
| `ram` | RAM capacity extracted from the product title (GB) |
| `rating_rounded` | Rating rounded to the nearest 0.5 |
| `price_category` | Derived price bucket: Cheap, Standard, Moderate, or Expensive |

The dataset used in this project focuses on the **laptop** product category as the search term.

## Key Insights

- Higher-rated laptops are more frequently categorized as **Expensive** or **Moderate**, while cheaper laptops show more spread-out rating distributions.
- Rounded ratings provide additional clarity when visualizing customer rating preferences.
- Rating distribution varies meaningfully across different RAM configurations, suggesting a relationship between hardware specifications and customer satisfaction.

## Challenges and Solutions

| Challenge | Solution |
|---|---|
| Dynamic content loading (Walmart uses JavaScript to render listings) | Extracted the JSON payload embedded directly in the page's script tag instead of relying on rendered HTML |
| Rate limiting / risk of IP blocking | Introduced delays (`time.sleep`) between consecutive requests |
| Inconsistent data formats (missing price or rating fields) | Handled missing values by substituting defaults (e.g., 0 or "NA") during the cleaning step |

## References

- Van Broucke, S., & Baesens, B. (2019). *Practical Web Scraping for Data Science: Best Practices and Examples with Python*. Apress.
- IBM Data Science, Coursera Course Materials.
- Sabrina Tiun, TTTC3123 Data Engineering Lecture Notes, Universiti Kebangsaan Malaysia (UKM).
- BMC Blogs. *What is ETL? Extract, Transform, Load Explained.*
- EliteDataScience. *A Guide to Data Cleaning with Python and Pandas.*
- [Beautiful Soup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Pandas Documentation](https://pandas.pydata.org/docs/)

## Disclaimer

This project was created strictly for **educational purposes** as part of a group project for the TTTC3213 Data Engineering course. The scraping techniques demonstrated here interact with Walmart's public website and may be subject to Walmart's Terms of Service. This repository is not intended for commercial use, and any reuse of the scraping logic should independently verify compliance with the target website's terms and applicable laws before deployment.
