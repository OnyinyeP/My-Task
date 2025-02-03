HNG Internship Program TASK (MY PROJECT)
AS A DATA ANALYST - MY ANSWER 

Stage 1: Data Cleaning and Title Optimization – A Step-by-Step Guide

This task ensures that the marketing dataset is clean, structured, and optimized for analysis. The goal is to resolve missing values, duplicates, and formatting issues while creating an SEO-friendly short_title for better readability and marketing impact.

Step 1: Understanding the Dataset

Before making any changes, let's download and review the dataset:
•Open the dataset in Google Sheets, Excel, or Python (Pandas)
•Identify key columns like Product_Title, Category, Price, and Description
•Check column names for inconsistencies (e.g., ProductTitle vs. Product_Title)

What to look for?

Missing values

Duplicates

Formatting issues (uppercase/lowercase inconsistencies, extra spaces, special characters)

Step 2: Initial Data Exploration

Now, let's inspect the dataset for errors using Python or Excel.

In Python (Pandas)

import pandas as pd

# Load dataset
df = pd.read_csv("product_data.csv")

# Check basic structure
print(df.info())  # Shows column types and missing values
print(df.describe())  # Summary of numerical data
print(df.head())  # First 5 rows

What to fix?
•Missing values: Which columns have blank entries?
•Duplicates: Are there repeated product entries?
•Inconsistent formatting: Are there any misaligned categories or mixed data types?

Step 3: Data Cleaning Process

Now, we fix all identified issues to ensure the dataset is reliable.

A. Handling Missing Values

If Price is missing → Fill with the average price

If Category is missing → Fill with the most common category

If Product_Title is missing → Drop the row

df['Price'].fillna(df['Price'].mean(), inplace=True)
df['Category'].fillna(df['Category'].mode()[0], inplace=True)
df.dropna(subset=['Product_Title'], inplace=True)

B. Removing Duplicates

Drop identical rows

Keep the latest product version

df.drop_duplicates(inplace=True)  
df.sort_values(by='Updated_Date', ascending=False).drop_duplicates(subset=['Product_Title'], keep='first', inplace=True)

C. Standardizing Column Names

Convert column names to lowercase and replace spaces with underscores

df.columns = df.columns.str.lower().str.replace(' ', '_')

D. Checking for Invalid Data

Negative prices? → Set to zero

Product ratings > 5? → Cap at 5

df.loc[df['price'] < 0, 'price'] = 0
df.loc[df['rating'] > 5, 'rating'] = 5

•Now, the dataset is clean, structured, and ready for optimization!

Step 4: Creating the short_title Feature

The goal is to make product titles shorter and SEO-friendly while keeping important details.

Rules for Short Titles

•Keep brand name, product type, and key attributes
•Remove filler words like "includes," "for," "set of"
• Limit to 30–50 characters
_______________________________
 Original Title         Optimized Short title 
_______________________________                                                        
“Tulip Flowers         Eyelets & Tile Black
Blackout Curtain
for Door, Window 
& Room
________________________________
“Marks & Spencer     “Girls’ Navy Pyjama 
Girls’ Pyjama Sets.     Set-9-10Y”
T86_2561C_Navy
Mix_9-10Y”
__________________________________
“Samsung Galaxy.       “Samsung S21
S21 Ultra 5G.                Ultra 5G-128GB”
Smartphone-128GB
Phantom Black”
__________________________________

Python Function to Automate Short Titles

def generate_short_title(title):
    words_to_remove = ["for", "with", "includes", "featuring", "set of", "|"]
    title_words = title.split()
    filtered_words = [word for word in title_words if word.lower() not in words_to_remove]
    short_title = " ".join(filtered_words)[:50]  # Limit to 50 characters
    return short_title.strip()

df['short_title'] = df['product_title'].apply(generate_short_title)

• Now, each product has a clean, SEO-optimized title.

Step 5: Documentation and Reporting

The final step is to create a technical report that explains what we did.

What to Include?

1. Introduction

Overview of the dataset and the objective.

2. Data Cleaning Summary

Issues identified (missing values, duplicates, formatting problems)

How they were fixed (e.g., filling missing values, removing duplicates)

3. Short Title Creation

Methodology (how short titles were generated)

Before & after examples

4. Final Dataset Overview

How many rows were cleaned?

How many duplicates were removed?

Key improvements in product title lengths

Report Format (Example)

•Title: Data Cleaning & Title Optimization Report

1. Introduction

This report details the data cleaning and title optimization process for the provided product dataset. The goal was to ensure the dataset is error-free, standardized, and includes SEO-friendly short titles for better marketing impact.

2. Data Cleaning Process

Fixed missing values (e.g., filled missing prices with the average)

Removed duplicates (X duplicate rows were deleted)

Standardized column names for consistency

3. Short Title Optimization

Implemented a logic-based approach to shorten titles while keeping essential details

Before & after examples:
__________________________________
Original Title.              Short Title 
__________________________________
“Apple iPhone 14.      “iPhone 14 Pro 
Pro Max - 256GB.       Max - 256GB”
Deep Purple, 5G 
Smartphone”
__________________________________
“Nike Running Shoes   “Nike Running 
With Breathable Mesh   Shoes - Black, 10”
Upper - Black, Size
10
__________________________________

4. Key Improvements in the Dataset

X% reduction in missing values

Y% improvement in product title readability

•Final Cleaned Dataset: Google Drive Link

• Full Report: [Google Drive Link]

Step 6: Review & Submission

•Final Checklist

•Proofread the technical report

•Ensure the cleaned dataset includes short_title

•Upload files to Google Drive and enable public access

•Submit via the provided submission link

Final Deliverables

1• Cleaned Dataset (CSV or Excel format)

Missing values fixed

Duplicates removed

short_title column added

2• Technical Report (PDF or DOCX format)

Overview of cleaning & optimization process.

Examples of before & after improvements.
