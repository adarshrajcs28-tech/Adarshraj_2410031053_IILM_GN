### EXPERIMENT 11
## 1. Delete those employees who joined the company before 31-dec-82 while there dept location is ‘new york’ or ‘chicago
```sql
DELETE FROM EMP
WHERE HIREDATE < '1982-12-31'
AND DEPTNO IN (
    SELECT DEPTNO
    FROM DEPT
    WHERE LOC IN ('NEW YORK', 'CHICAGO')
);
```
###
## 2. Display employee name, job, deptname, location for all who are working as managers.
```sql
SELECT E.ENAME, E.JOB, D.DNAME, D.LOC
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND E.JOB = 'MANAGER';
```
###
## 3. Display name and salary of ford if his sal is equal to high sal of his grade.
```sql
SELECT ENAME, SAL
FROM EMP
WHERE ENAME = 'FORD'
AND SAL = (
    SELECT MAX(SAL)
    FROM EMP E, SALGRADE S
    WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL
    AND S.GRADE = (
        SELECT S2.GRADE
        FROM EMP E2, SALGRADE S2
        WHERE E2.ENAME = 'FORD'
        AND E2.SAL BETWEEN S2.LOSAL AND S2.HISAL
    )
);
```
###
## 4. Find out the top 5 earner of company.
```sql
SELECT ENAME, SAL
FROM EMP
ORDER BY SAL DESC
LIMIT 5;
```
###
## 5. Display the name of those employees who are getting highest salary.
```sql
SELECT ENAME
FROM EMP
WHERE SAL = (SELECT MAX(SAL) FROM EMP);
```
###
## 6. Display those employees whose salary is equal to average of maximum and minimum.
```sql
SELECT ENAME, SAL
FROM EMP
WHERE SAL = (
    (SELECT MAX(SAL) FROM EMP) + (SELECT MIN(SAL) FROM EMP)
) / 2;
```
###
## 7. Display dname where at least 3 are working and display only dname.
```sql
SELECT D.DNAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
GROUP BY D.DNAME
HAVING COUNT(*) >= 3;
```
###
## 8. Display name of those managers names whose salary is more than average salary of company.
```sql
SELECT ENAME
FROM EMP
WHERE JOB = 'MANAGER'
AND SAL > (SELECT AVG(SAL) FROM EMP);
```
###
## 9. Display those managers name whose salary is more than an average salary of his employees.
```sql
SELECT M.ENAME
FROM EMP M
WHERE M.JOB = 'MANAGER'
AND M.SAL > (
    SELECT AVG(E.SAL)
    FROM EMP E
    WHERE E.MGR = M.EMPNO
);
```
###
## 10. Display employee name, sal, comm and net pay for those employees whose net pay are greater than or equal to any other employee salary of the company?
```sql
SELECT ENAME, SAL, COMM, (SAL + IFNULL(COMM,0)) AS NET_PAY
FROM EMP
WHERE (SAL + IFNULL(COMM,0)) >= ANY (
    SELECT SAL FROM EMP
);
```


