### EXPERIMENT 8
## 1. Display all employees with their dept name.
```sql
SELECT E.ENAME, E.DEPTNO, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D
ON E.DEPTNO = D.DEPTNO;
```
###
## 2. Display those employees whose manager names is jones, and also display their manager name.
```sql
Display those employees whose manager names is jones, and
also display their manager name.
```
###
## 3. Display employee name, his job, his dept name, his manager name, his grade and make out of an under department wise.
```sql
SELECT E.ENAME, E.JOB, D.DNAME, M.ENAME AS MANAGER, S.GRADE
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
LEFT JOIN EMPLOYEE M ON E.MGR = M.EMPNO
JOIN SALGRADE S ON E.SAL BETWEEN S.LOSAL AND S.HISAL
ORDER BY D.DNAME;
```
###
## 4. List out all the employees name, job, and salary grade and department name for everyone in the company except ‘clerk’. Sort on salary display the highest salary.
```sql
SELECT E.ENAME, E.JOB, S.GRADE, D.DNAME, E.SAL
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
JOIN SALGRADE S ON E.SAL BETWEEN S.LOSAL AND S.HISAL
WHERE E.JOB <> 'CLERK'
ORDER BY E.SAL DESC;
```
###
## 5. Display employee name, his job and his manager. Display also employees who are without manager.
```sql
SELECT E.ENAME, E.JOB, NVL(M.ENAME, 'NO MANAGER') AS MANAGER
FROM EMPLOYEE E
LEFT JOIN EMPLOYEE M
ON E.MGR = M.EMPNO;
```
###
## 6. List the employee name, job, annual salary, deptno, dept name and grade who earn 36000 a year or who are not clerks.
```sql
SELECT E.ENAME, E.JOB, (E.SAL*12) AS ANNUAL_SAL,
       E.DEPTNO, D.DNAME, S.GRADE
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
JOIN SALGRADE S ON E.SAL BETWEEN S.LOSAL AND S.HISAL
WHERE (E.SAL*12 = 36000) OR (E.JOB <> 'CLERK');
```
###
## 7. List ename, job, annual sal, deptno, dname and grade who earn 30000 per year and who are not clerks.
```sql
SELECT E.ENAME, E.JOB, (E.SAL*12) AS ANNUAL_SAL,
       E.DEPTNO, D.DNAME, S.GRADE
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
JOIN SALGRADE S ON E.SAL BETWEEN S.LOSAL AND S.HISAL
WHERE (E.SAL*12 = 30000) AND (E.JOB <> 'CLERK');
```
###
## 8. List out all employees by name and number along with their manager’s name and number also display ‘no manager’ who has no manager.
```sql
SELECT E.EMPNO, E.ENAME,
       NVL(M.EMPNO, '0') AS MGR_NO,
       NVL(M.ENAME, 'NO MANAGER') AS MANAGER
FROM EMPLOYEE E
LEFT JOIN EMPLOYEE M
ON E.MGR = M.EMPNO;
```
###
## 9. Select dept name, dept no and sum of sal.
```sql
SELECT D.DNAME, D.DEPTNO, SUM(E.SAL) AS TOTAL_SAL
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
GROUP BY D.DNAME, D.DEPTNO;
```
###
## 10.  Display employee number, name and location of the department in which he is working.
```sql
SELECT E.EMPNO, E.ENAME, D.LOC
FROM EMPLOYEE E
JOIN DEPARTMENT D
ON E.DEPTNO = D.DEPTNO;
```
###
## 11. Display employee name and department name for each employee.
```sql
SELECT E.ENAME, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D
ON E.DEPTNO = D.DEPTNO;
```
