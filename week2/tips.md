
## basic sql
### Comparison operators and Arithmetic 
 * =  <> != > < >=  <=
```
SELECT * FROM tutorial.patient_list WHERE age = 30;
SELECT * FROM tutorial.patient_list WHERE physician_last_name > 'Jack';
SELECT patient_id, weight_lbs - height_inches as weight_height_diff FROM tutorial.patient_list;
```

### SQL Logical operators
 * LIKE  case-sensitive while ilike is not
```
SELECT * FROM tutorial.patient_list WHERE physician_last_name like 'pay%';
SELECT * FROM tutorial.patient_list WHERE physician_last_name ilike 'pay%';
```
 * IN 
```
SELECT * FROM tutorial.patient_list WHERE physician_last_name in ('Smith', 'Goldberg');
```
 * BETWEEN
```
SELECT * FROM tutorial.patient_list WHERE age between 42 and 50;
```
 * IS NULL
```
SELECT * FROM tutorial.patient_list WHERE weight_lbs IS NULL;
```
 * AND
```
SELECT * FROM tutorial.patient_list WHERE weight_lbs IS NULL and height_inches = 76;
```
 * OR
```
SELECT * FROM tutorial.patient_list WHERE weight_lbs IS NULL or height_inches = 76;
```
 * NOT
```
SELECT * FROM tutorial.patient_list WHERE weight_lbs IS NOT NULL;
SELECT * FROM tutorial.patient_list WHERE physician_last_name not like 'pay%';
SELECT * FROM tutorial.patient_list WHERE physician_last_name not in ('Smith', 'Goldberg');
SELECT * FROM tutorial.patient_list WHERE age not between 42 and 50;
```

### Order By
```
SELECT * FROM tutorial.patient_list WHERE weight_lbs IS NOT NULL ORDER BY age;
SELECT * FROM tutorial.patient_list WHERE weight_lbs IS NOT NULL ORDER BY age DESC;
```

### SQL Aggregate Functions
 * COUNT
```
SELECT count(*) FROM tutorial.aapl_historical_stock_price LIMIT 100;
SELECT count(high) FROM tutorial.aapl_historical_stock_price LIMIT 100;
```
 * SUM
```
SELECT sum(high) FROM tutorial.aapl_historical_stock_price;
```
 * MAX/MIN
```
SELECT max(high) as max_value, min(low) as min_value  FROM tutorial.aapl_historical_stock_price;
```
 * AVG
```
SELECT avg(high) as avg_value  FROM tutorial.aapl_historical_stock_price;
```
 * GROUP BY
```
SELECT year, month, count(*) as count  FROM tutorial.aapl_historical_stock_price group by year, month;
```
 * HAVING
```
SELECT year, month, max(high) as max_high  FROM tutorial.aapl_historical_stock_price group by year, month HAVING max(high) > 400 ;
```
 * DISTINCT
```
SELECT DISTINCT  year FROM tutorial.aapl_historical_stock_price;
```
 * CASE
```
select player_name, year, CASE WHEN year > 'SR' THEN 'YES' ELSE 'NO' END as is_a_senior from benn.college_football_players
```
 * JOIN
```
SELECT teams.conference AS conference,
       AVG(players.weight) AS average_weight
  FROM benn.college_football_players players
  JOIN benn.college_football_teams teams
    ON teams.school_name = players.school_name
    GROUP BY teams.conference
 ORDER BY AVG(players.weight) DESC

 SELECT companies.permalink AS companies_permalink,
       companies.name AS companies_name,
       acquisitions.company_permalink AS acquisitions_permalink,
       acquisitions.acquired_at AS acquired_date
  FROM tutorial.crunchbase_companies companies
  LEFT JOIN tutorial.crunchbase_acquisitions acquisitions
    ON companies.permalink = acquisitions.company_permalink

 SELECT companies.permalink AS companies_permalink,
       companies.name AS companies_name,
       acquisitions.company_permalink AS acquisitions_permalink,
       acquisitions.acquired_at AS acquired_date
  FROM tutorial.crunchbase_companies companies
 RIGHT JOIN tutorial.crunchbase_acquisitions acquisitions
    ON companies.permalink = acquisitions.company_permalink   

SELECT companies.permalink,
       companies.name,
       companies.status,
       COUNT(investments.investor_permalink) AS investors
  FROM tutorial.crunchbase_companies companies
  LEFT JOIN tutorial.crunchbase_investments_part1 investments
    ON companies.permalink = investments.company_permalink
 WHERE investments.funded_year > companies.founded_year + 5
 GROUP BY 1,2, 3

SELECT companies.permalink,
       companies.name,
       companies.status,
       COUNT(investments.investor_permalink) AS investors
  FROM tutorial.crunchbase_companies companies
  LEFT JOIN tutorial.crunchbase_investments_part1 investments
    ON companies.permalink = investments.company_permalink
 AND investments.funded_year > companies.founded_year + 5
 GROUP BY 1,2, 3
```
 * UNION
```
SELECT *
  FROM tutorial.crunchbase_investments_part1
 UNION
 SELECT *
   FROM tutorial.crunchbase_investments_part2
```

### TRANSFORM
 * LEFT RIGHT LENGTH TRIM
```
SELECT location,
       TRIM(both '()' FROM location)
  FROM tutorial.sf_crime_incidents_2014_01
```

### SUBQUERY
```
SELECT sub.*
  FROM (
        SELECT *
          FROM tutorial.sf_crime_incidents_2014_01
         WHERE day_of_week = 'Friday'
       ) sub
 WHERE sub.resolution = 'NONE'
```

### References
https://community.modeanalytics.com/sql/tutorial/sql-operators/


