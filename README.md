# Customer_Segmentation

## Table of Content

- [Project Overview](#project-overview)

- [Data Source](#data-source)

- [Tool](#tool)

- [Data Cleaning and Preparation](#Data-Cleaning-Preparation)

- [Exploratory](#Exploratory)

- [Data Analysis](#Data-Analysis)


## Project Overview
Customer Segmentation is a typical strategy used by organizations to categorize clients based on their demographics, shopping patterns, or other traits. This practice is essential for understanding the diverse needs and preferences of the customer base, allowing businesses to tailor their products, services, and marketing efforts more effectively.


## Data Source
The Retail Dataset provides a view of customers’ transactions, allowing for in-depth analysis and segmentatioin. This dataset contains the following variables: InvoiceNo: The invoice number for each transaction, StockCode: The unique code for each product sold, Description: The description of each product sold, Quantity: The quantity of each product sold in each transaction InvoiceDate: The date and time of each transaction, UnitPrice: The price of each product sold, CustomerID: The unique identifier for each customer, Country: The country where each transaction occurred.


## Tool
- Postgresql - Data Cleaning and Analysis


## Data Cleaning & Preparation
The data preparation phase comprises of the following tasks:

- Data loading and inspection
- Handling null values
- Data cleaning and formating


## Exploratory

The following questions were answered after the cleaning and preparation phase:
- What is the distribution of order values across all customers in the dataset?
- How many unique products has each customer purchased?
- Which customers have only made a single purchase from the company?
- Which products are most commonly purchased together by customers in the
dataset?


## Data Analysis
This includes the code worked with:

WITH common_products AS (
    SELECT 
        a.stockcode AS product1,
        b.stockcode AS product2
    FROM 
        retail a
    JOIN 
        retail b 
    ON 
        a.invoiceno = b.invoiceno
    WHERE 
        a.stockcode < b.stockcode
)

-- Step 3: Count the occurrences of each product pair
	
SELECT 
    product1, 
    product2, 
    COUNT(*) AS product_count
FROM 
    common_products
GROUP BY 
    product1, 
    product2
ORDER BY 
	 product_count DESC;

