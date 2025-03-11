# HackerRank-SQL
## 1. Binary Tree Nodes

You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

![alt text](https://s3.amazonaws.com/hr-challenge-images/12888/1443818507-5095ab9853-1.png)

- Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

   * Root: If node is root node.
   * Leaf: If node is leaf node.
   * Inner: If node is neither root nor leaf node.

- *Sample Input:*

![alt text](https://s3.amazonaws.com/hr-challenge-images/12888/1443818507-5095ab9853-1.png)

- *Sample Output:*
```
1 Leaf
2 Inner
3 Leaf
5 Root
6 Leaf
8 Inner
9 Leaf
```
- *Explanation:*
The Binary Tree below illustrates the sample:

![alt text](https://s3.amazonaws.com/hr-challenge-images/12888/1443773633-f9e6fd314e-simply_sql_bst.png)

- *Solution:*
```sql
SELECT 
    N,
    CASE
    WHEN P IS NULL THEN 'Root'
    WHEN N IN (SELECT DISTINCT P FROM BST WHERE P IS NOT NULL) THEN 'Inner'
    ELSE 'Leaf'
    END
FROM BST
ORDER BY N;
```
----
## 2. New Companies

Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy:

![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458531031-249df3ae87-ScreenShot2016-03-21at8.59.56AM.png)

- Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

- Note:

  * The tables may contain duplicate records.
  * The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the 
  * ascending company_codes will be C_1, C_10, and C_2.

- *Input Format:*

  * Company: The company_code is the code of the company and founder is the founder of the company.

   ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458531125-deb0a57ae1-ScreenShot2016-03-21at8.50.04AM.png)

  * Lead_Manager: The lead_manager_code is the code of the lead manager, and the company_code is the code of the working company.

   ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458534960-2c6d764e3c-ScreenShot2016-03-21at8.50.12AM.png)

  * Senior_Manager: The senior_manager_code is the code of the senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company.

   ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458534973-6548194998-ScreenShot2016-03-21at8.50.21AM.png)

  * Manager: The manager_code is the code of the manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company.

   ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458534988-7fc0af46ce-ScreenShot2016-03-21at8.50.29AM.png)

  * Employee: The employee_code is the code of the employee, the manager_code is the code of its manager, the senior_manager_code is the code of its senior manager, the lead_manager_code is the code of its lead manager, and the company_code is the code of the working company.

   ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458535002-d47f63cbb4-ScreenShot2016-03-21at8.50.41AM.png)

- *Sample Input:*

  * Company Table:
  
   ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458535049-2a207c44b3-ScreenShot2016-03-21at8.50.52AM.png)
  
  * Lead_Manager Table::
  
     ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458535073-919107f639-ScreenShot2016-03-21at8.51.03AM.png)
    
  * Senior_Manager Table:
  
     ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458535111-b1c48335b3-ScreenShot2016-03-21at8.51.15AM.png)
    
  * Manager Table:
  
     ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458535122-888f4bf340-ScreenShot2016-03-21at8.51.26AM.png)
  
  * Employee Table:
  
     ![alt text](https://s3.amazonaws.com/hr-challenge-images/19505/1458535134-878767e0d9-ScreenShot2016-03-21at8.51.52AM.png)
  



- *Sample Output:*
```
C1 Monika 1 2 1 2
C2 Samantha 1 1 2 2
```
- *Explanation:*

In company C1, the only lead manager is LM1. There are two senior managers, SM1 and SM2, under LM1. There is one manager, M1, under senior manager SM1. There are two employees, E1 and E2, under manager M1.

In company C2, the only lead manager is LM2. There is one senior manager, SM3, under LM2. There are two managers, M2 and M3, under senior manager SM3. There is one employee, E3, under manager M2, and another employee, E4, under manager, M3.

- *Solution:*
```sql
/*
Output: company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees

Condition: 
order by company_code ascending

Note:
*may contain duplicates => DISTINCT

Order: C_1, C_10, C_2
*/

select 
        c.company_code, 
        c.founder, 
        count(DISTINCT(lm.lead_manager_code)), 
        count(DISTINCT(sm.senior_manager_code)), 
        count(DISTINCT(m.manager_code)), 
        count(DISTINCT(e.employee_code))
from Company c
left join Lead_Manager lm on lm.company_code = c.company_code
left join Senior_Manager sm  on sm.lead_manager_code = lm.lead_manager_code
left join Manager m  on m.senior_manager_code = sm.senior_manager_code
left join Employee e on e.manager_code = m.manager_code
group by c.company_code, c.founder
order by company_code asc;
```
----

## 3. Weather Observation Station 20

A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to 4 decimal places.

- *Input Format:*

The STATION table is described as follows:

![alt text](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where LAT_N is the northern latitude and LONG_W is the western longitude.

- *Solution:*
```sql
select RTRIM(round(s.lat_n,4), '0')
from station s
where (select count(lat_n) from station where lat_n<s.lat_n)=(select count(lat_n) from station where lat_n>s.lat_n);
```
----

## 4. The Report
You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

![alt text](https://s3.amazonaws.com/hr-challenge-images/12891/1443818166-a5c852caa0-1.png)

Grades contains the following data:

![alt text](https://s3.amazonaws.com/hr-challenge-images/12891/1443818137-69b76d805c-2.png)

Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.


- *Sample Input:*

![alt text](https://s3.amazonaws.com/hr-challenge-images/12891/1443818093-b79f376ec1-3.png)

- *Sample Output:*
```
Maria 10 99
Jane 9 81
Julia 9 88 
Scarlet 8 78
NULL 7 63
NULL 7 68
```

- *Note:*

Print "NULL"  as the name if the grade is less than 8.

- *Explanation:*

Consider the following table with the grades assigned to the students:

![alt text](https://s3.amazonaws.com/hr-challenge-images/12891/1443818026-0b3af8db30-4.png)

So, the following students got 8, 9 or 10 grades:

Maria (grade 10)
Jane (grade 9)
Julia (grade 9)
Scarlet (grade 8)

- *Solution:*
```sql
select iif(g.grade>7, s.name, null), g.grade, s.marks 
from students s
left join grades g
on s.marks between g.min_mark and g.max_mark
order by g.grade desc, s.name asc, s.marks asc;
```
----
## 5. Top Competitors
Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.


- *Input Format:*

The following tables contain contest data:

  - Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.
  
  ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458526776-67667350b4-ScreenShot2016-03-21at7.45.59AM.png)
  
  - Difficulty: The difficult_level is the level of difficulty of the challenge, and score is the maximum score that can be achieved for a challenge at that difficulty level.
  
  ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458526915-57eb75d9a2-ScreenShot2016-03-21at7.46.09AM.png)
  
  - Challenges: The challenge_id is the id of the challenge, the hacker_id is the id of the hacker who created the challenge, and difficulty_level is the level of difficulty of the challenge.
  
  ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458527032-f9ca650442-ScreenShot2016-03-21at7.46.17AM.png)
  
  - Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge that the submission belongs to, and score is the score of the submission.
  
  ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458527077-298f8e922a-ScreenShot2016-03-21at7.46.29AM.png)

- *Sample Input:*
    
    * Hackers Table:
    
    ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458527241-6922b4ad87-ScreenShot2016-03-21at7.47.02AM.png)
    
    * Difficulty Table:
    
    ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458527265-7ad6852a13-ScreenShot2016-03-21at7.46.50AM.png)
    
    * Challenges Table:
    
    ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458527285-01e95eb6ec-ScreenShot2016-03-21at7.46.40AM.png)
    
    * Submissions Table:
    
    ![alt text](https://s3.amazonaws.com/hr-challenge-images/19504/1458527812-479a74b99f-ScreenShot2016-03-21at8.06.05AM.png)


- *Sample Output:*
```
90411 Joe
```

- *Explanation:*

Hacker 86870 got a score of 30 for challenge 71055 with a difficulty level of 2, so 86870 earned a full score for this challenge.

Hacker 90411 got a score of 30 for challenge 71055 with a difficulty level of 2, so 90411 earned a full score for this challenge.

Hacker 90411 got a score of 100 for challenge 66730 with a difficulty level of 6, so 90411 earned a full score for this challenge.

Only hacker 90411 managed to earn a full score for more than one challenge, so we print the their hacker_id and name as 2 space-separated values.

- *Solution:*
```sql
select iif(g.grade>7, s.name, null), g.grade, s.marks 
from students s
left join grades g
on s.marks between g.min_mark and g.max_mark
order by g.grade desc, s.name asc, s.marks asc;
```
----



