# Retail Store Sales — Data Cleaning & Standardisation
<img width="1889" height="361" alt="Image" src="https://github.com/user-attachments/assets/30b13882-8c5d-4c8d-afd5-a8170c2ed835" />

## Overview
Cleaning and validation of a 12,575-row dirty retail sales dataset (8 product 
categories, ~200 unique items), using cross-field logic to deduce missing values 
from a static Category + Price Per Unit relationship, rather than deleting 
incomplete rows outright. Every action is documented in a full decision log with 
before/after counts and reasoning.

## Key Features
- Built a reference lookup table of all ~200 unique Item/Category/Price 
  combinations to deduce missing values across two linked columns
- Recovered 604 of 1,213 missing Item values (50%) by matching Category + Price 
  Per Unit against the lookup table; the remaining 609 had no Price Per Unit to 
  match against and were correctly left unresolved rather than guessed
- Recovered all 609 missing Price Per Unit values (100%) by looking up the fixed 
  price for each Item — a direct, unambiguous relationship with no risk of 
  incorrect matches
- Validated Total Spent = Quantity × Price Per Unit across every row where all 
  three values were present — 0 mismatches found, confirming the complete records 
  in this dataset are internally consistent
- Identified 604 rows missing both Quantity and Total Spent simultaneously — with 
  no third value to calculate from, these were deliberately left blank rather than 
  estimated, to avoid mixing deduced facts with statistical guesses
- Standardised 4,199 blank/None Discount Applied values to an explicit "Unknown" 
  category rather than defaulting to False, since assuming False would have 
  understated discount usage
- Fixed 340 Payment Method and 26 Location entries with inconsistent 
  capitalisation/whitespace (e.g. "cash" / "Cash " / "CASH") using TRIM + PROPER
- Confirmed Transaction ID fully unique (0 duplicates) and Transaction Date fully 
  clean, requiring no changes

## Cleaning Summary
- Total rows: 12,575
- Total issues found across all columns: 7,595
- Total values successfully fixed/deduced: 1,584
- Total rows left unresolved/flagged: 5,407 (Item: 604 · Quantity/Total Spent: 604, 
  overlapping · Discount Applied: 4,199 relabelled as Unknown)
- Duplicate Transaction IDs: 0

## Tools Used
Microsoft Excel — INDEX/MATCH, VLOOKUP, COUNTIF/COUNTIFS, TRIM, PROPER, 
SUBSTITUTE, conditional formatting, data validation, Paste Special (Values)

## Files
raw_data.csv — original uncleaned dataset (12,575 rows)
retail_store_sales_cleaned_data.xlsx — cleaned data, including Raw Data, Cleaned Data and Cleaning Log tabs

## Data Source
Retail Store Sales: Dirty for Data Cleaning — via Kaggle
kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning

