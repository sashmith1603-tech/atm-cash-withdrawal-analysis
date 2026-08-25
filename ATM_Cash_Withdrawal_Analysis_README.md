# ATM Cash Withdrawal Analysis

## Project Overview

**ATM Cash Withdrawal Analysis** is an end-to-end data analytics project
focused on ATM cash usage, transaction performance, ATM health, refill
requirements, and suspicious withdrawal patterns.

### Project Workflow

**Raw Data → SQL → Power BI Data Cleaning → DAX Measures → Power BI
Dashboards → Business Insights**

The objective is to transform ATM transaction and operational data into
an interactive Power BI solution that supports ATM cash management,
service monitoring, refill planning, and suspicious-transaction review.

------------------------------------------------------------------------

## 1. Business Problem

Traditional ATM monitoring is often reactive: it shows what has already
happened, but it may not make it easy to identify which ATMs need
immediate attention.

This project focuses on:

-   ATM cash withdrawal analysis
-   Failed transaction monitoring
-   ATM health monitoring
-   Refill requirement identification
-   Withdrawal-demand analysis
-   Suspicious transaction pattern monitoring
-   Data-driven operational decision-making

------------------------------------------------------------------------

## 2. Project Objectives

1.  Analyze ATM cash withdrawals.
2.  Monitor transaction volume and failed transaction percentage.
3.  Evaluate ATM health.
4.  Identify ATMs requiring refill.
5.  Analyze withdrawal patterns over time.
6.  Monitor unusual transaction indicators.
7.  Build interactive Power BI dashboards.
8.  Provide useful business insights for ATM operations.

------------------------------------------------------------------------

## 3. Dataset

The project uses a prepared **20,000-record ATM analytics dataset**.

The dataset was structured to support ATM cash management, transaction
analysis, operational monitoring, and suspicious-transaction analysis.

### Main Data Areas

The final project data covers fields relating to:

-   ATM ID
-   Transaction ID
-   Date
-   Day Name
-   Weekend
-   Withdrawal amount
-   Opening cash
-   Cash loaded/refilled
-   Closing cash
-   Transaction information
-   Failed transaction indicators
-   ATM health score
-   Refill indicators
-   Downtime/service indicators
-   Customer complaint indicators
-   Fraud/suspicious transaction indicators
-   Suspicious transaction reasons

> **Dataset note:** The prepared dataset is for analytics/project
> demonstration. It should not be described as confidential or official
> bank transaction data unless independently verified as such.

------------------------------------------------------------------------

## 4. Tools and Technologies

  Tool          Purpose
  ------------- ----------------------------------------------
  SQL           Database storage, querying and data handling
  Power Query   Data cleaning and transformation
  Power BI      Data modeling, DAX and visualization
  DAX           KPI and analytical calculations
  Excel/CSV     Dataset/source format

------------------------------------------------------------------------

# 5. Project Workflow

## Step 1 --- Raw Data

The project started with a structured ATM dataset.

The data was reviewed to understand:

-   Available columns
-   Data types
-   ATM identifiers
-   Transaction information
-   Cash-related fields
-   Date fields
-   Operational indicators
-   Suspicious/fraud-related fields

------------------------------------------------------------------------

## Step 2 --- SQL

The dataset was loaded into SQL and used as the database layer.

### SQL activities

1.  Imported the ATM dataset into SQL.
2.  Reviewed the table structure.
3.  Checked available fields.
4.  Worked with the data using SQL.
5.  Connected the SQL data source to Power BI.

### Why SQL?

SQL provides a structured way to store, access, query and validate data
before performing BI analysis.

------------------------------------------------------------------------

## Step 3 --- Power BI Data Cleaning

The SQL data was connected to Power BI and reviewed using Power Query.

### Cleaning performed

#### Duplicate Check

Duplicate records were checked before removal.

During the project, removing duplicates caused the row count to decrease
significantly. Therefore, duplicate removal was not treated as an
automatic operation. The records and selected duplicate columns had to
be validated before deleting anything.

#### Null and Empty Values

Columns were checked for:

-   Null values
-   Empty values
-   Error values

The Date table was checked and showed valid date values with no empty
values in the displayed validation.

#### Data Types

Important columns were checked for correct types:

-   Date
-   Whole number
-   Decimal number
-   Text

#### Date Validation

The Date field was validated/corrected and used with:

-   Date
-   Day Name
-   Weekend

These fields support time-based and weekday/weekend analysis.

#### Negative Values

Cash-related fields were checked for negative values.

Negative values were not automatically deleted because filtering without
understanding the business logic can remove valid records or calculated
results.

#### Fraud/Suspicious Fields

Fraud-related fields were checked based on the categories actually
available in the dataset.

------------------------------------------------------------------------

# 6. DAX Measures

DAX (Data Analysis Expressions) was used to create dynamic KPIs.

### Total Cash Withdrawn

``` dax
Total Cash Withdrawn =
SUM('ATM Table'[Total_Withdrawal])
```

### Failed Transaction %

``` dax
Failed Transaction % =
DIVIDE(
    [Failed Transactions],
    [Total Transactions],
    0
)
```

This calculates failed transactions as a percentage of total
transactions.

### Average Health Score

``` dax
Avg Health Score =
AVERAGE('ATM Table'[Health_Score])
```

### ATMs Requiring Refill

Example:

``` dax
ATMs Requiring Refill =
CALCULATE(
    DISTINCTCOUNT('ATM Table'[ATM_ID]),
    'ATM Table'[Need_Refill] = "YES"
)
```

> Replace the example table and column names with the exact names in the
> final Power BI model.

### Other KPI areas

The project also includes/uses measures or indicators for:

-   Total Transactions
-   Failed Transactions
-   Average Health Score
-   Refill requirements
-   Large withdrawals
-   Night transactions
-   High-frequency transactions
-   Suspicious transactions
-   Downtime/service indicators

------------------------------------------------------------------------

# 7. Dashboard 1 --- ATM Performance & Cash Management

The first Power BI dashboard focuses on ATM operational performance and
cash management.

### Main KPI cards

-   Total Cash Withdrawn
-   Failed Transaction %
-   Average Health Score
-   ATMs Requiring Refill

### Analysis

The dashboard is designed to show:

-   Cash withdrawal performance
-   ATM demand
-   Refill requirements
-   ATM health
-   Transaction performance

### Business value

It helps users quickly identify ATMs that may need cash management,
refill or operational attention.

------------------------------------------------------------------------

# 8. Dashboard 2 --- Smart Monitoring & Fraud Analysis

The second dashboard focuses on suspicious transaction indicators.

### Main indicators

-   Large Withdrawals
-   Night Transactions
-   High-Frequency Transactions
-   Suspicious Transactions by ATM
-   Suspicious Transactions by Reason

### Business value

The dashboard helps users identify unusual patterns and prioritize
transactions or ATMs for further investigation.

> **Important:** A suspicious indicator does not prove that a
> transaction is fraudulent. It is a risk signal that may require
> investigation.

------------------------------------------------------------------------

# 9. Key Business Insights

### Cash Demand

Identify ATMs with higher withdrawal activity and possible refill
pressure.

### Service Quality

Monitor failed transaction percentage, downtime and ATM health
indicators.

### Refill Management

Identify ATMs that require refill and support better cash management.

### Suspicious Activity

Identify unusual patterns such as:

-   Large withdrawals
-   Night-time transactions
-   High-frequency transactions
-   Other suspicious reasons present in the dataset

### Operational Prioritization

Use KPI values and visual patterns to prioritize ATM maintenance, cash
replenishment and transaction review.

------------------------------------------------------------------------

# 10. Business Benefits

The project can support ATM operations by helping to:

-   Improve visibility of ATM cash demand
-   Reduce the risk of ATMs running out of cash
-   Support refill planning
-   Monitor failed transactions
-   Prioritize ATM maintenance
-   Identify unusual transaction patterns
-   Support data-driven decision-making

------------------------------------------------------------------------

# 11. Project Challenges and Solutions

### Challenge 1 --- Duplicate Records

**Problem:** Removing duplicates caused a significant reduction in rows.

**Solution:** The duplicate logic was reviewed rather than blindly
deleting records.

### Challenge 2 --- Negative Cash Values

**Problem:** Negative values appeared during cash-related
validation/calculation.

**Solution:** The values were checked according to the meaning of the
field before applying filters.

### Challenge 3 --- Date Errors

**Problem:** Date values initially required validation/correction.

**Solution:** The Date field was converted/validated and checked for
errors.

### Challenge 4 --- Power BI Learning Curve

**Problem:** The project required learning Power Query, DAX, visual
formatting and dashboard design.

**Solution:** The dashboard was built incrementally:

**Cleaning → Measures → KPI Cards → Charts → Formatting**

------------------------------------------------------------------------

# 12. Future Improvements

## Smart Cash Refill Prediction

A future version can predict when an ATM may need cash replenishment
using:

-   Historical withdrawals
-   Day of week
-   Salary periods
-   Festival seasons
-   Nearby events
-   Historical ATM demand

## Real-Time Monitoring

Connect the dashboard to continuously updated ATM transaction data.

## Automated Alerts

Create alerts when:

-   Cash reaches a critical level
-   Failed transaction percentage increases
-   ATM health decreases
-   Suspicious activity increases

## Machine Learning

A future version could add:

-   Cash-out prediction
-   ATM demand forecasting
-   Transaction anomaly detection
-   Fraud-risk scoring

------------------------------------------------------------------------

# 13. Skills Demonstrated

-   Data Analytics
-   SQL
-   Power BI
-   Power Query
-   DAX
-   Data Cleaning
-   Data Validation
-   KPI Development
-   Dashboard Design
-   Data Visualization
-   Business Analysis
-   Suspicious Pattern Analysis

------------------------------------------------------------------------

# 14. Project Architecture

``` text
RAW ATM DATA
     |
     v
   SQL
     |
     v
POWER BI / POWER QUERY
     |
     v
DATA CLEANING
     |
     v
DAX MEASURES
     |
     +--------------------+
     |                    |
     v                    v
DASHBOARD 1          DASHBOARD 2
ATM Performance      Smart Monitoring
& Cash Management    & Fraud Analysis
```

------------------------------------------------------------------------

# 15. Final Outcome

The completed project demonstrates an end-to-end data analytics
workflow:

**Raw Data → SQL → Power BI Cleaning → DAX Measures → Dashboard →
Business Insights**

The final Power BI solution provides a management view of:

-   ATM cash withdrawals
-   Failed transactions
-   ATM health
-   Refill requirements
-   Large withdrawals
-   Night transactions
-   High-frequency transactions
-   Suspicious transaction patterns

------------------------------------------------------------------------

# 16. Conclusion

The ATM Cash Withdrawal Analysis project demonstrates how raw
transaction data can be transformed into a practical business
intelligence solution.

SQL was used as the database layer, Power Query was used for data
preparation and cleaning, DAX was used for KPI calculations, and Power
BI was used to create interactive dashboards.

The project provides a foundation for better ATM cash management,
operational monitoring and suspicious transaction review.

------------------------------------------------------------------------

## Project Information

**Project:** ATM Cash Withdrawal Analysis\
**Dataset Size:** 20,000 records\
**Dashboard Pages:** 2\
**Primary Tools:** SQL, Power BI, Power Query, DAX\
**Data Format:** Excel / CSV\
**Project Type:** Data Analytics / Business Intelligence
