### EXPERIMENT 9
## 1. Display the name of emp name who earns highest salary.
```sql
SELECT ENAME
FROM EMP
WHERE SAL = (SELECT MAX(SAL) FROM EMP);
```
###
## 2. Display the employee number and name of employee working as clerk and earning highest salary among clerks.
```sql
SELECT EMPNO, ENAME
FROM EMP
WHERE JOB = 'CLERK'
AND SAL = (SELECT MAX(SAL) FROM EMP WHERE JOB = 'CLERK');
```
###
## 3. Display the names of the salesman who earns a salary more than the highest salary of any clerk.
```sql
SELECT ENAME
FROM EMP
WHERE JOB = 'SALESMAN'
AND SAL > (SELECT MAX(SAL) FROM EMP WHERE JOB = 'CLERK');
```
###
## 4. Display the names of clerks who earn salary more than that of james of that of sal lesser than that of scott.
```sql
SELECT ENAME
FROM EMP
WHERE JOB = 'CLERK'
AND SAL > (SELECT SAL FROM EMP WHERE ENAME = 'JAMES')
AND SAL < (SELECT SAL FROM EMP WHERE ENAME = 'SCOTT');
```
###
## 5. Display the names of employees who earn a sal more than that of james or that of salary greater than that of scott.
```sql
SELECT ENAME
FROM EMP
WHERE SAL > (SELECT SAL FROM EMP WHERE ENAME = 'JAMES')
OR SAL > (SELECT SAL FROM EMP WHERE ENAME = 'SCOTT');
```
###
## 6. Display the names of the employees who earn highest salary in their respective departments.
```sql
SELECT ENAME, DEPTNO, SAL
FROM EMP E
WHERE SAL = (
    SELECT MAX(SAL)
    FROM EMP
    WHERE DEPTNO = E.DEPTNO
);
```
###
## 7. Display the names of employees who earn highest salaries in their respective job groups.
```sql
SELECT ENAME, JOB, SAL
FROM EMP E
WHERE SAL = (
    SELECT MAX(SAL)
    FROM EMP
    WHERE JOB = E.JOB
);
```
###
## 8. Display the employee names who are working in accounting dept.
```sql
SELECT ENAME
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO
    FROM DEPT
    WHERE DNAME = 'ACCOUNTING'
);
```
###
## 9. Display the employee names who are working in chicago.
```sql
SELECT ENAME
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO
    FROM DEPT
    WHERE LOC = 'CHICAGO'
);
```
###
## 10. Display the job groups having total salary greater than the maximum salary for managers.
```sql
SELECT JOB
FROM EMP
GROUP BY JOB
HAVING SUM(SAL) > (
    SELECT MAX(SAL)
    FROM EMP
    WHERE JOB = 'MANAGER'
);
```
