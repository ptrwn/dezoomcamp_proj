# dezoomcamp_proj
Data Engineering Zoomcamp 2024 course project

[DASHBOARD](https://lookerstudio.google.com/reporting/fd198067-fc96-4830-8b58-9b887556ca3e/)

## Problem description

The dashboard can be used for analysis of liquor sales and alcohol consumption in Iowa: 

- for specific locations - counties, towns, and stores;
- within an arbitrary range of dates;
- with breakdown by vendors, categories and brands. 


## Usage examples

Generic view:
![generic view](https://github.com/ptrwn/dezoomcamp_proj/blob/master/pics/report_general_view.jpg)

Details for January, 2023:
![jan_23](https://github.com/ptrwn/dezoomcamp_proj/blob/master/pics/jan_23.jpg)


Details for January, 2023, for Polk county and spiced rum:
![breakdown](https://github.com/ptrwn/dezoomcamp_proj/blob/master/pics/polk_county_jan23_captmorgan.jpg)


Iowa Liquor Sales [dataset](https://data.iowa.gov/Sales-Distribution/Iowa-Liquor-Sales/m3tr-qhgy/about_data).

## Steps to reproduce

Load data into BigQuery from Google's public dataset:
```sql
CREATE TABLE `radiant-firefly-412220.booze.iowa_sales` AS
SELECT * FROM `bigquery-public-data.iowa_liquor_sales.sales`;
```

Add a column for name of week day and fill it in:
```sql
ALTER TABLE radiant-firefly-412220.booze.iowa_sales ADD COLUMN weekday STRING;
UPDATE radiant-firefly-412220.booze.iowa_sales SET weekday = FORMAT_DATE('%A', date) WHERE TRUE;
```