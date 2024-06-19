# HackerRank-SQL
1. Query all columns for all American cities in the **CITY** table with populations larger than 100000. The **CountryCode** for America is USA.
The **CITY** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE CountryCode = 'USA' AND POPULATION > 100000;
```

