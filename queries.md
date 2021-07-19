# World Bank Queries

*Meta data
*Summary stats
*univariate
  * Histograms, density plot
* Bivariate (two coloums)
  * Scatter Plot - corellation

## no. of countires 

```sql
SELECT count(distinct country_name) FROM `patents-public-data.worldbank_wdi.wdi_2016` 
```

## Min and max year 

```sql
SELECT min(year) as min_year , max(year ) as max_year FROM `patents-public-data.worldbank_wdi.wdi_2016` 
```

* average min and max surface area of all countries and also each country in the dataset 

```sql
SELECT min(indicator_value) as minimum_surface_area
, max(indicator_value) as maximum_surface_area
, avg(indicator_value) as average_surface_area 
FROM `patents-public-data.worldbank_wdi.wdi_2016` 
where 1=1 
--and lower(indicator_name) like '%surface%'
and indicator_name = 'Surface area (sq. km)'

```


```sql

SELECT
  country_name,
  MIN(indicator_value) AS minimum_surface_area,
  MAX(indicator_value) AS maximum_surface_area,
  AVG(indicator_value) AS average_surface_area
FROM
  `patents-public-data.worldbank_wdi.wdi_2016`
WHERE
  1=1
  --and lower(indicator_name) like '%surface%'
  AND indicator_name = 'Surface area (sq. km)'
GROUP BY
  country_name
ORDER BY
  average_surface_area DESC,
  country_name  -- double sort - first by avg_sa descending and then by country name

```
![image](https://user-images.githubusercontent.com/37925362/126155606-7ffe79ae-41ba-487c-a19b-abe367ae16ae.png)

* average co2 emissions for one location over the years


* Which country's manufacturing sector has largest contribution to GDP?
* Total population for each country?
* i see there are some common indicator codes a bar plot should able to tell us the frequency!!
* Urban population of countries where gdp < global avergage
