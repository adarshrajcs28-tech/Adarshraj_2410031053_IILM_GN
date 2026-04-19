# Experiment -1
## 1. Create Employee_master table with data using Employee table.
###
```sql
CREATE TABLE EMPLOYEE_MASTER AS
SELECT * FROM EMPLOYEE;
```
## 2. Delete all record into Employee_master whose DeptNo is 10.
###
```sql
DELETE FROM EMPLOYEE_MASTER
WHERE DEPTNO = 10;
```
## 3. Update 10% in his salary of DEPTNO 20 into Employee_Master.
###
```sql
UPDATE EMPLOYEE_MASTER
SET SAL = SAL + (SAL * 0.10)
WHERE DEPTNO = 20;
```
## 4. Alter SAL with size 10,2 in Employee_Master.
###
```sql
ALTER TABLE EMPLOYEE_MASTER
MODIFY SAL NUMBER(10,2);
```
## 5. Drop Employee_master Table.
###
```sql
DROP TABLE EMPLOYEE_MASTER;
```
