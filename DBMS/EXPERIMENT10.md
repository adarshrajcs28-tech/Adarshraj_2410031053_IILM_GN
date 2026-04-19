### EXPERIMENT 10
## 1.  Display the names of employees from department number 10 with salary greater than that of any employee working in other departments.
```sql
SELECT ENAME
FROM EMP
WHERE DEPTNO = 10
AND SAL > ANY (
    SELECT SAL
    FROM EMP
    WHERE DEPTNO <> 10
);
```
###
## 2. Display the names of employee from department number 10 with salary greater than that of all employee working in other departments.
```sql
SELECT ENAME
FROM EMP
WHERE DEPTNO = 10
AND SAL > ALL (
    SELECT SAL
    FROM EMP
    WHERE DEPTNO <> 10
);
```
###
## 3. Display the details of employees who are in sales dept and grade is 3.
```sql
SELECT E.*
FROM EMP E, DEPT D, SALGRADE S
WHERE E.DEPTNO = D.DEPTNO
AND E.SAL BETWEEN S.LOSAL AND S.HISAL
AND D.DNAME = 'SALES'
AND S.GRADE = 3;
```
###
## 4. Display those who are not managers and who are managers anyone.
```sql
SELECT ENAME
FROM EMP
WHERE JOB <> 'MANAGER';
```
###
## 5.  Display those employees whose manager name is jones.
```sql
SELECT E.ENAME
FROM EMP E, EMP M
WHERE E.MGR = M.EMPNO
AND M.ENAME = 'JONES';
```
###
## 6.  Display ename who are working in sales dept.
```sql
SELECT E.ENAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND D.DNAME = 'SALES';
```
###
## 7. Display employee name, deptname, salary and comm. For those sal in between 2000 to 5000 while location is chicago.
```sql
SELECT E.ENAME, D.DNAME, E.SAL, E.COMM
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND E.SAL BETWEEN 2000 AND 5000
AND D.LOC = 'CHICAGO';
```
###
## 8. Display those employees whose salary greater than his manager salary.
```sql
SELECT E.ENAME
FROM EMP E, EMP M
WHERE E.MGR = M.EMPNO
AND E.SAL > M.SAL;
```
###
## 9. Display those employees who are working in the same dept where his manager is working.
```sql
SELECT E.ENAME
FROM EMP E, EMP M
WHERE E.MGR = M.EMPNO
AND E.DEPTNO = M.DEPTNO;
```
###
## 10. Display grade and employees name for the dept no 10 or 30 but grade is not 4, while joined the company before 31-dec-82.
```sql
SELECT S.GRADE, E.ENAME
FROM EMP E, SALGRADE S
WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL
AND E.DEPTNO IN (10, 30)
AND S.GRADE <> 4
AND E.HIREDATE < '1982-12-31';
```
