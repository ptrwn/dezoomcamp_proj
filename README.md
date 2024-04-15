# dezoomcamp_proj
Data Engineering Zoomcamp 2024 course project

Iowa Liquor Sales [dataset](https://data.iowa.gov/Sales-Distribution/Iowa-Liquor-Sales/m3tr-qhgy/about_data).

Load data into BigQuery from Google's public dataset:

```sql
CREATE TABLE `radiant-firefly-412220.booze.iowa_sales` AS
SELECT * FROM `bigquery-public-data.iowa_liquor_sales.sales`;
```

