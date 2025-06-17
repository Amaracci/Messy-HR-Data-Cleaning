# Messy-HR-Data-Cleaning
## Overview
This project focuses on cleaning a messy HR dataset that had lots of inconsistencies and missing information. The data included employee details like names, ages, salaries, genders, departments, joining dates, phone numbers, and emails. Our goal was to make the data clean, consistent, and ready for analysis or reporting.

## Thought Process
When I started, I knew the data was far from clean:
- Some fields like Age and Salary were stored inconsistently (e.g., "thirty" instead of 30, or "SIXTY THOUSAND" instead of 60000).
- Dates were in various formats like 2020/02/20, 01/15/2020, or 5-Apr-18.
- Phone numbers and emails had missing values, but not always as recognizable NaN — sometimes they were just empty cells.
- Some columns had text entries for missing data, like "missing" instead of actual nulls.

## Challenges Faced
- Inconsistent formats: Numbers stored as words or text made conversion tricky.
- Date parsing: Dates in many formats caused pd.to_datetime() to fail or return NaT (missing dates).
- Missing values: Empty strings and custom strings like "missing" didn’t behave like NaN, which complicated filtering and filling missing data.
- Mixed data types: Some columns had numbers, text, and missing entries mixed together.

## How I Went About It
### Step 1: Standardizing text
First, I cleaned text fields by stripping extra spaces to avoid hidden errors.

### Step 2: Fixing numeric columns
For Age and Salary, I converted text numbers to actual numbers. I used pd.to_numeric() with error coercion to handle weird values, then converted to integers where possible.

### Step 3: Parsing dates
To handle all date formats, I used the dateutil parser with a custom function that tries to parse any string into a datetime object. This helped convert mixed formats without losing data.

### Step 4: Handling missing phone numbers and emails
I replaced empty strings in these columns with NaN so pandas could detect them properly as missing values.

### Step 5: Dealing with ‘missing’ strings
Since some missing info was marked as the string "missing", I filtered rows containing that word in key columns (like Phone Number or Email) to highlight incomplete staff data.

### Step 6: Filtering incomplete records
Using pandas filtering, I isolated rows with missing or “missing” details so HR can easily identify which staff need follow-up.

## Final Thoughts
Cleaning messy data takes patience and careful handling. It’s important to:
- Know your data types and handle each appropriately.
- Use flexible tools (like dateutil.parser) for tricky fields.
- Standardize how missing data is represented for easier analysis later.
- This project was a great hands-on example of dealing with real-world messy data and turning it into something usable.


If you want to explore or use the cleaned data, check the scripts and feel free to ask questions!
