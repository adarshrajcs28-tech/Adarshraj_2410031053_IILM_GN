### EXPERIMENT 7
## 1. Compute the no. of days remaining in this year.
```sql
SELECT TRUNC(TO_DATE('31-DEC-' || TO_CHAR(SYSDATE,'YYYY'),'DD-MON-YYYY') - SYSDATE) 
       AS DAYS_REMAINING
FROM DUAL;
```
###
## 2. Find the highest and lowest salaries and the difference between of them.
```sql
SELECT MAX(SAL) AS HIGHEST_SAL,
       MIN(SAL) AS LOWEST_SAL,
       (MAX(SAL) - MIN(SAL)) AS DIFFERENCE
FROM EMPLOYEE;
```
###
## 3. List employee whose commission is greater than 25 % of their salaries.
```sql
SELECT *
FROM EMPLOYEE
WHERE COMM > (SAL * 0.25);
```
###
## 4. Make a query that displays salary in dollar format.
```sql
SELECT ENAME,
       TO_CHAR(SAL, '$99,999.99') AS SALARY_DOLLAR
FROM EMPLOYEE;
```
###
## 5. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading.
```sql
SELECT JOB,
       SUM(DECODE(DEPTNO,10,SAL)) AS DEPT10,
       SUM(DECODE(DEPTNO,20,SAL)) AS DEPT20,
       SUM(DECODE(DEPTNO,30,SAL)) AS DEPT30,
       SUM(DECODE(DEPTNO,40,SAL)) AS DEPT40,
       SUM(SAL) AS TOTAL
FROM EMPLOYEE
GROUP BY JOB;
```
###
## 6. Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983. Give appropriate column heading.
```sql
SELECT COUNT(*) AS TOTAL_EMP,
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1980',1,0)) AS "1980",
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1981',1,0)) AS "1981",
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1982',1,0)) AS "1982",
       SUM(DECODE(TO_CHAR(HIREDATE,'YYYY'),'1983',1,0)) AS "1983"
FROM EMPLOYEE;
```
###
## 7. Query to get the last Sunday of Any Month.
```sql
SELECT NEXT_DAY(LAST_DAY(SYSDATE) - 7, 'SUNDAY') AS LAST_SUNDAY
FROM DUAL;
```
###
## 8. Display department numbers and total number of employees working in each department.
```sql
SELECT DEPTNO, COUNT(*) AS TOTAL_EMP
FROM EMPLOYEE
GROUP BY DEPTNO;
```
###
## 9. Display the various jobs and total number of employees within each job group.
```sql
SELECT JOB, COUNT(*) AS TOTAL_EMP
FROM EMPLOYEE
GROUP BY JOB;
```
###
## 10.  Display the depart numbers and total salary for each department.
```sql
SELECT DEPTNO, SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE
GROUP BY DEPTNO;
```
