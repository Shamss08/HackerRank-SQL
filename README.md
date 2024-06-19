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
5. Query all attributes of every Japanese city in the **CITY** table. The **COUNTRYCODE** for Japan is JPN.
The **CITY** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```
----
6. Query a list of **CITY** and **STATE** from the **STATION** table.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where **LAT_N** is the northern latitude and **LONG_W** is the western longitude.

- *Solution:*
```sql
SELECT CITY, STATE
FROM STATION;
```
----
7. Query a list of **CITY** names from **STATION** for cities that have an even **ID** number. Print the results in any order, but exclude duplicates from the answer.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID%2=0;
```
----
8. Find the difference between the total number of **CITY** entries in the table and the number of distinct **CITY** entries in the table.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT COUNT(CITY) - COUNT(DISTINCT(CITY))
FROM STATION;
```
----
9. Query the two cities in **STATION** with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT TOP 1 CITY, LEN(CITY) AS NAME_LENGTH
FROM STATION
ORDER BY NAME_LENGTH, CITY;

SELECT TOP 1 CITY, LEN(CITY) AS NAME_LENGTH
FROM STATION
ORDER BY NAME_LENGTH DESC, CITY;
```
----
10. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from **STATION**. Your result cannot contain duplicates.
The STATION table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[AEIOUaeiou]%';
```
----
11. Query the list of CITY names ending with vowels (a, e, i, o, u) from **STATION**. Your result cannot contain duplicates.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '%[AEIOUaeiou]';
```
----
12. Query the list of CITY names from **STATION** which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
The **STATION** table is described as follows:
![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[AEIOUaeiou]%[AEIOUaeiou]';
```
----
13. Query the list of CITY names from **STATION** that do not start with vowels. Your result cannot contain duplicates.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%';
```
----
14. Query the list of CITY names from **STATION** that do not end with vowels. Your result cannot contain duplicates.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '%[^AEIOUaeiou]';
```
----
15. Query the list of CITY names from **STATION** that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%' OR CITY LIKE '%[^AEIOUaeiou]';
```
----
16. Query the list of CITY names from **STATION** that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
The **STATION** table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%[^AEIOUaeiou]';
```
----
