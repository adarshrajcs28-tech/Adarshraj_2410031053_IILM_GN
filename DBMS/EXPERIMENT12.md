### EXPERIMENT 12
## 1. Display those employees whose salary is less than his manager but more than salary of any other managers.
```sql
SELECT E.ename, E.sal
FROM employee E
JOIN employee M ON E.mgr = M.empno
WHERE E.sal < M.sal
  AND E.sal > ANY (
        SELECT sal
        FROM employee
        WHERE job = 'MANAGER'
  );
```
###
## 2. Find out the number of employees whose salary is greater than their manager salary?
```sql
SELECT COUNT(*) AS total_employees
FROM employee E
JOIN employee M ON E.mgr = M.empno
WHERE E.sal > M.sal;
```
###
## 3. Display those managers who are not working under president but they are working under any other manager?
```sql
SELECT E.ename
FROM employee E
JOIN employee M ON E.mgr = M.empno
WHERE E.job = 'MANAGER'
  AND M.job <> 'PRESIDENT';
```
###
## 4. Delete those department where no employee working?
```sql
DELETE FROM department
WHERE NOT EXISTS (
    SELECT 1
    FROM employee
    WHERE employee.deptno = department.deptno
);
```
###
## 5. Delete those records from emp table whose deptno not available in dept table?
```sql
DELETE FROM employee
WHERE deptno NOT IN (
    SELECT deptno
    FROM department
);
```
###
## 6.  Display those earners whose salary is out of the grade available in sal grade table?
```sql
SELECT ename, sal
FROM employee E
WHERE NOT EXISTS (
    SELECT 1
    FROM salgrade S
    WHERE E.sal BETWEEN S.losal AND S.hisal
);
```
###
## 7. Display employee name, sal, comm. And whose net pay is greater than any other in the company?
```sql
SELECT ename, sal, comm
FROM employee
WHERE (sal + IFNULL(comm, 0)) = (
    SELECT MAX(sal + IFNULL(comm, 0))
    FROM employee
);
```
###
## 8. Display those employees who are working in sales or research?
```sql
SELECT E.ename
FROM employee E
JOIN department D ON E.deptno = D.deptno
WHERE D.dname IN ('SALES', 'RESEARCH');
```
### 9. Display the grade of jones?
```sql
SELECT S.grade
FROM employee E
JOIN salgrade S
  ON E.sal BETWEEN S.losal AND S.hisal
WHERE E.ename = 'JONES';
```
###
## 10. Display the department name the no of characters of which is equal to no of employees in any other department?
```sql
SELECT D.dname
FROM department D
WHERE LENGTH(D.dname) IN (
    SELECT COUNT(*)
    FROM employee
    GROUP BY deptno
);
```
