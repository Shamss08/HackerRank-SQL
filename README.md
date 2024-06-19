![image](https://github.com/Shamss08/HackerRank-SQL/assets/152320040/e2416f8b-dee2-48f4-b2be-ed8e9f38c117)# HackerRank-SQL
1. Query all columns for all American cities in the **CITY** table with populations larger than 100000. The **CountryCode** for America is USA.
The **CITY** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE CountryCode = 'USA' AND POPULATION > 100000;
```
----

2. Query the **NAME** field for all American cities in the **CITY** table with populations larger than 120000. The CountryCode for America is USA.
The **CITY** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

- *Solution:*
```sql
SELECT NAME
FROM CITY
WHERE POPULATION > 120000 AND CountryCode = 'USA';
```
----

3. Query all columns (attributes) for every row in the **CITY** table.
The **CITY** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

- *Solution:*
```sql
SELECT *
FROM CITY;
```
----
4. Query all columns for a city in **CITY** with the ID 1661.
The **CITY** table is described as follows:
![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE ID =1661;
```
----
5. ###japanese-cities-attributes
Query all attributes of every Japanese city in the **CITY** table. The **COUNTRYCODE** for Japan is JPN.
The **CITY** table is described as follows:
![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```
----
