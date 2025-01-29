# Walmart Product ETL Project

Welcome to the **Walmart Product ETL Project** repository! This project demonstrates the process of extracting, transforming, and loading (ETL) product data from Walmart's website, using Python for web scraping, data manipulation, and visualisation.

---

## **Project Overview**

This project was developed as part of the **TTTC3213 Data Engineering course** at Universiti Kebangsaan Malaysia (UKM). It focuses on extracting product data from Walmart's website, transforming it into a structured format, and analysing it to gain insights such as pricing trends, brand distribution, and customer reviews.

**Key Objectives:**
- Scrape product data (e.g., names, prices, ratings) from Walmart's search results.
- Clean and transform the scraped data into a structured format.
- Visualise the data to uncover trends and insights.

You can read the detailed explanation of this project in our Medium article:  
[Mastering Walmart Product ETL: A Data Engineering Journey from Web Scraping to Insights](https://a207961-siswa-ukm.medium.com/mastering-walmart-product-etl-a-data-engineering-journey-from-web-scraping-to-insights-b0a008bdeb19).

---

## **Features**

- **Web Scraping**: Extract product details (name, price, rating, reviews) from Walmart using Python's `requests` and `BeautifulSoup`.
- **Data Transformation**: Clean and structure the data using `pandas`, including handling missing values and categorising prices.
- **Data Visualisation**: Generate insightful visualisations such as pie charts, scatter plots, and heatmaps using `matplotlib` and `seaborn`.
- **Data Export**: Save the cleaned dataset as a CSV file for further analysis.

---

## **Technologies Used**

The following Python libraries were used in this project:
- **Web Scraping**: `requests`, `BeautifulSoup`
- **Data Manipulation**: `pandas`, `numpy`
- **Visualisation**: `matplotlib`, `seaborn`
- **Others**: `json`, `re`, `time`

---

## **Installation**

1. Clone this repository:
   ```bash
   git clone https://github.com/jonathanfernandi/Walmart-Product-ETL.git
   cd Walmart-Product-ETL
   ```

2. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

## **Usage**

1. Open the Jupyter Notebook file (`Walmart_Product_ETL.ipynb`) in your preferred IDE or Jupyter environment.

2. Update the search term in the code to scrape specific product categories:
   ```python
   search_term = "laptop"
   ```

3. Run all cells to execute the ETL pipeline:
   - Extract product data from Walmart.
   - Transform and clean the data.
   - Visualize insights and save the cleaned dataset.

4. The final cleaned dataset will be saved as a CSV file:
   ```bash
   walmart_products.csv
   ```

---

## **Project Structure**

```
Walmart-Product-ETL/
│
├── Walmart_Product_ETL.ipynb    # Main Jupyter Notebook for the ETL process
├── requirements.txt             # List of required Python libraries
├── walmart_products.csv         # Cleaned dataset (generated after running the notebook)
└── README.md                    # Project documentation
```

---

## **Results and Visualisations**

### 1. **Pie Chart: Brand Distribution**
Displays the proportion of popular laptop brands in the dataset.

### 2. **Heat Map: Feature Correlations**
Shows correlations between numerical features like price, rating, reviews, and RAM size.

### 3. **Scatter Plots**
- *RAM vs Price*: Highlights how RAM size influences laptop prices.
- *Rating vs Price*: Explores relationships between customer ratings and price categories.

### 4. **Count Plots**
Visualises distributions of RAM sizes and ratings across products.

### 5. **KDE Plot**
Shows density distributions of ratings across different price categories.

For detailed visualisations, refer to our Medium article linked above.

---

## **Contributors**

This project was developed by Group INT-2 for the Data Engineering course:

1. Jonathan Alvindo Fernandi (A207961)  
2. Kevin Maverick (A208051)
3. Lai Junlin (A197837)

---

Thank you for exploring our project! If you have any questions or feedback, feel free to reach out or open an issue in this repository!
