# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
SELECT MIN(resale_price/floor_area_sqm) AS max_price_per_sqm,
MAX(resale_price/floor_area_sqm) AS min_price_per_sqm
FROM main.resale_flat_prices_2017;
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
SELECT town, AVG(resale_price/floor_area_sqm) AS avg_price_per_sqm
FROM main.resale_flat_prices_2017
GROUP BY town;

```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql

SELECT COUNT(*) AS flat_num,
CASE
	WHEN rfp.resale_price <400_000 THEN 'Budget'
	WHEN rfp.resale_price > 700_000 THEN 'Premium'
	ELSE 'Mid-Range'
END AS price_range
FROM main.resale_flat_prices_2017 rfp
GROUP BY price_range
ORDER BY flat_num DESC;

```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql

SELECT rfp.town, COUNT(*) AS first_quarter,
FROM main.resale_flat_prices_2017 rfp
WHERE rfp.month BETWEEN '2017-01' AND '2017-03'
GROUP BY rfp.town
ORDER BY first_quarter DESC;

```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
