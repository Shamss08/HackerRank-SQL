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
6. Query a count of the number of cities in CITY having a Population larger than 100000.

- *Solution:*
```sql
SELECT COUNT(ID)
FROM CITY 
WHERE POPULATION > 100000;
```
----
7. Query the total population of all cities in CITY where District is California.

- *Solution:*
```sql
SELECT SUM(POPULATION)
FROM CITY 
WHERE DISTRICT = 'California';
```
----
8. Query the average population of all cities in CITY where District is California.

- *Solution:*
```sql
SELECT AVG(POPULATION)
FROM CITY 
WHERE DISTRICT = 'California';
```
----
9. Query the average population for all cities in CITY, rounded down to the nearest integer.

- *Solution:*
```sql
SELECT ROUND(AVG(POPULATION),0)
FROM CITY;
```
- *Another Solution:*
```sql
SELECT FLOOR(AVG(POPULATION))
FROM CITY;
```
----
10. Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

- *Solution:*
```sql
SELECT SUM(POPULATION)
FROM CITY 
WHERE COUNTRYCODE = 'JPN';
```
----
11. Query the difference between the maximum and minimum populations in CITY.

- *Solution:*
```sql
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY;
```
----
## STATION TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

12. Query a list of **CITY** and **STATE** from the **STATION** table.

- *Solution:*
```sql
SELECT CITY, STATE
FROM STATION;
```
----
13. Query a list of **CITY** names from **STATION** for cities that have an even **ID** number. Print the results in any order, but exclude duplicates from the answer.

- *Solution:*
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID%2=0;
```
----
14. Find the difference between the total number of **CITY** entries in the table and the number of distinct **CITY** entries in the table.

- *Solution:*
```sql
SELECT COUNT(CITY) - COUNT(DISTINCT(CITY))
FROM STATION;
```
----
15. Query the two cities in **STATION** with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

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
16. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from **STATION**. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[AEIOUaeiou]%';
```
----
17. Query the list of CITY names ending with vowels (a, e, i, o, u) from **STATION**. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '%[AEIOUaeiou]';
```
----
18. Query the list of CITY names from **STATION** which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[AEIOUaeiou]%[AEIOUaeiou]';
```
----
19. Query the list of CITY names from **STATION** that do not start with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%';
```
----
20. Query the list of CITY names from **STATION** that do not end with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '%[^AEIOUaeiou]';
```
----
21. Query the list of CITY names from **STATION** that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%' OR CITY LIKE '%[^AEIOUaeiou]';
```
----
22. Query the list of CITY names from **STATION** that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

- *Solution:*
```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE CITY LIKE '[^AEIOUaeiou]%[^AEIOUaeiou]';
```
----
23. Query the following two values from the STATION table:
    The sum of all values in LAT_N rounded to a scale of 2 decimal places.
    The sum of all values in LONG_W rounded to a scale of 2 decimal places.

- *Solution:*
```sql
SELECT CAST(SUM(LAT_N) AS Decimal(10,2))AS lat, CAST(SUM(LONG_W) AS Decimal(10,2)) AS lon
FROM STATION;
```
----
24. Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345. Truncate your answer to 4 decimal places.

- *Solution:*
```sql
SELECT CAST(SUM(LAT_N) AS DECIMAL(15,4)) 
FROM STATION 
WHERE LAT_N BETWEEN 38.7880 AND 137.2345;
```
----
25. Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345. Truncate your answer to 4 decimal places.

- *Solution:*
```sql
SELECT CAST(MAX(LAT_N) AS Decimal(15,4)) 
FROM STATION 
WHERE LAT_N < 137.2345;
```
----
26. Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in **STATION** that is less than **137.2345**. Round your answer to **4** decimal places.

- *Solution:*
```sql
SELECT CAST(LONG_W AS Decimal(10,4))
FROM STATION 
WHERE LAT_N = (SELECT MAX(LAT_N)  FROM STATION  WHERE LAT_N < 137.2345);
```
----
27. Query the smallest Northern Latitude (LAT_N) from **STATION** that is greater than **38.7780**. Round your answer to **4** decimal places.
- *Solution:*
```sql
SELECT CAST(MIN(LAT_N) AS Decimal(10,4))
FROM STATION
WHERE LAT_N > 38.7780;
```
- *Another Solution:*
```sql
SELECT TOP 1 CAST(LAT_N AS Decimal(10,4))
FROM STATION
WHERE LAT_N > 38.7780
ORDER BY LAT_N;
```
----
28. Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in **STATION** is greater than **38.7780**. Round your answer to **4** decimal places.

- *Solution:*
```sql
SELECT CAST(LONG_W AS DECIMAL(10,4))
FROM STATION
WHERE LAT_N=(SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780);
```
----
29. Consider P1(a,b) and P2(c,d) to be two points on a 2D plane.
 a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
 b happens to equal the minimum value in Western Longitude (LONG_W in STATION).
 c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
 d happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Manhattan Distance between points P1 and P2 and round it to a scale of 4 decimal places.

- *Solution:*
```sql
SELECT 
CAST((MAX(LAT_N)-MIN(LAT_N)) + (MAX(LONG_W)-MIN(LONG_W)) AS DECIMAL(10,4))AS [Manhattan Distance]
FROM STATION;
```
----
30. Consider P1(a,b) and P2(a,b) to be two points on a 2D plane where (a,b) are the respective minimum and maximum values of Northern Latitude (LAT_N) and (c,d) are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION.

Query the Euclidean Distance between points P1 and P2 and format your answer to display 4 decimal digits.

- *Solution:*
```sql
SELECT CAST(SQRT(SQUARE(MAX(LAT_N)-MIN(LAT_N))+SQUARE(MAX(LONG_W)-MIN(LONG_W))) AS DECIMAL(10,4))
FROM STATION;
```
----
## STUDENTS TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/12896/1443815243-94b941f556-1.png)

31. Query the Name of any student in **STUDENTS** who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

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

32. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

- *Solution:*
```sql
SELECT name
FROM Employee
ORDER BY name;
```
----
33. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

- *Solution:*
```sql
SELECT name
FROM Employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id;
```
----
34. Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error (i.e.: actual - miscalculated  average monthly salaries), and round it up to the next integer.

- *Solution:*
```sql
SELECT CAST (CEILING(AVG(CAST(Salary AS Float)) - AVG(CAST(REPLACE(Salary, '0', '') AS Float))) AS Int)
FROM EMPLOYEES;
```
----
35. We define an employee's total earnings to be their monthly salary x months worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.

- *Solution:*
```sql
SELECT MAX(earnings), COUNT(employee_id)
FROM(
            SELECT *,salary * months AS earnings, Dense_rank() OVER(ORDER BY salary * months Desc) as DR
             FROM Employee
) AS newtable
WHERE DR=1;
```
----
## TRIANGLES TABLE
![alt text](https://s3.amazonaws.com/hr-challenge-images/12887/1443815629-ac2a843fb7-1.png)

36. Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:
    
   - Equilateral: It's a triangle with 3 sides of equal length.
   - Isosceles: It's a triangle with 2 sides of equal length.
   - Scalene: It's a triangle with 3 sides of differing lengths.
   - Not A Triangle: The given values of A, B, and C don't form a triangle.

- *Solution:*
```sql
SELECT 
        CASE 
                WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
                WHEN A = B AND B = C THEN 'Equilateral'
                WHEN  A = B OR A = C OR B = C THEN 'Isosceles'
                ELSE 'Scalene'
        END
FROM TRIANGLES;
```
----
## CITY and COUNTRY tables
![alt text](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)
![alt text](https://s3.amazonaws.com/hr-challenge-images/8342/1449769013-e54ce90480-Country.jpg)

37. Given the **CITY** and **COUNTRY** tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
**Note**: CITY.CountryCode and COUNTRY.Code are matching key columns.

- *Solution:*
```sql
SELECT SUM(C.POPULATION)
FROM CITY C 
JOIN COUNTRY CN
ON C.CountryCode = CN.Code 
WHERE CN.CONTINENT='Asia';
```
----
38. Given the **CITY** and **COUNTRY** tables, query the names of all cities where the CONTINENT is 'Africa'.
**Note**: CITY.CountryCode and COUNTRY.Code are matching key columns.

- *Solution:*
```sql
SELECT C.NAME
FROM CITY C, COUNTRY CN
WHERE C.COUNTRYCODE = CN.CODE AND CN.CONTINENT= 'Africa';
```
----
39. Given the **CITY** and **COUNTRY** tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.
**Note**: CITY.CountryCode and COUNTRY.Code are matching key columns.

- *Solution:*
```sql
SELECT CN.CONTINENT, AVG(C.POPULATION)
FROM CITY C, COUNTRY CN
WHERE C.COUNTRYCODE = CN.CODE
GROUP BY CN.CONTINENT;
```
----
40. Generate the following two result sets:

1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
There are a total of [occupation_count] [occupation]s.
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

Note: There will be at least two entries in the table for each type of occupation.
Input Format
The OCCUPATIONS table is described as follows:
![alt text](https://s3.amazonaws.com/hr-challenge-images/12889/1443816414-2a465532e7-1.png)

Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.
Sample Input
An OCCUPATIONS table that contains the following records:
![alt text](https://s3.amazonaws.com/hr-challenge-images/12889/1443816608-0b4d01d157-2.png)

Sample Output
```sql
Ashely(P)
Christeen(P)
Jane(A)
Jenny(D)
Julia(A)
Ketty(P)
Maria(A)
Meera(S)
Priya(S)
Samantha(D)
There are a total of 2 doctors.
There are a total of 2 singers.
There are a total of 3 actors.
There are a total of 3 professors.
```
