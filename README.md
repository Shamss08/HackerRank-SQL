# HackerRank-SQL
## CITY TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

1. Query all columns for all American cities in the **CITY** table with populations larger than 100000. The **CountryCode** for America is USA.

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE CountryCode = 'USA' AND POPULATION > 100000;
```
----

2. Query the **NAME** field for all American cities in the **CITY** table with populations larger than 120000. The CountryCode for America is USA.

- *Solution:*
```sql
SELECT NAME
FROM CITY
WHERE POPULATION > 120000 AND CountryCode = 'USA';
```
----

3. Query all columns (attributes) for every row in the **CITY** table.

- *Solution:*
```sql
SELECT *
FROM CITY;
```
----
4. Query all columns for a city in **CITY** with the ID 1661.

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE ID =1661;
```
----
5. Query all attributes of every Japanese city in the **CITY** table. The **COUNTRYCODE** for Japan is JPN.

- *Solution:*
```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```
----
## STATION TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

6. Query a list of **CITY** and **STATE** from the **STATION** table.

- *Solution:*
```sql
SELECT CITY, STATE
FROM STATION;
```
----
7. Query a list of **CITY** names from **STATION** for cities that have an even **ID** number. Print the results in any order, but exclude duplicates from the answer.

- *Solution:*
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID%2=0;
```
----
8. Find the difference between the total number of **CITY** entries in the table and the number of distinct **CITY** entries in the table.

- *Solution:*
```sql
SELECT COUNT(CITY) - COUNT(DISTINCT(CITY))
FROM STATION;
```
----
9. Query the two cities in **STATION** with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

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

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[AEIOUaeiou]%';
```
----
11. Query the list of CITY names ending with vowels (a, e, i, o, u) from **STATION**. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '%[AEIOUaeiou]';
```
----
12. Query the list of CITY names from **STATION** which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[AEIOUaeiou]%[AEIOUaeiou]';
```
----
13. Query the list of CITY names from **STATION** that do not start with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%';
```
----
14. Query the list of CITY names from **STATION** that do not end with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '%[^AEIOUaeiou]';
```
----
15. Query the list of CITY names from **STATION** that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%' OR CITY LIKE '%[^AEIOUaeiou]';
```
----
16. Query the list of CITY names from **STATION** that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%[^AEIOUaeiou]';
```
----
## STUDENTS TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/12896/1443815243-94b941f556-1.png)

17. Query the Name of any student in **STUDENTS** who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

- *Solution:*
```sql
SELECT Name
FROM STUDENTS
WHERE Marks > 75
order by RIGHT(Name, 3) , ID;
```
----
## Employee TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png)

18. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

- *Solution:*
```sql
SELECT name
FROM Employee
ORDER BY name;
```
----
19. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

- *Solution:*
```sql
SELECT name
FROM Employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id;
```
----
## TRIANGLES TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/12887/1443815629-ac2a843fb7-1.png)

20. Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

...Equilateral: It's a triangle with  sides of equal length.
...Isosceles: It's a triangle with  sides of equal length.
...Scalene: It's a triangle with  sides of differing lengths.
...Not A Triangle: The given values of A, B, and C don't form a triangle.

- *Solution:*
```sql
SELECT name
FROM Employee
ORDER BY name;
```
----

