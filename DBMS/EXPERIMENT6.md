### EXPERIMENT 6
## 1. Display empno, ename, deptno from employee table. Instead of display department numbers display the related department name (Use decode function).
```sql
SELECT EMPNO, ENAME,
       DECODE(DEPTNO,
              10, 'RESEARCH',
              20, 'ACCOUNTING',
              30, 'SALES',
              40, 'OPERATIONS') AS DNAME
FROM EMPLOYEE;
```
###
## 2. Display your age in days.
```sql
SELECT TRUNC(SYSDATE - TO_DATE('01-JAN-2000','DD-MON-YYYY')) AS AGE_IN_DAYS
FROM DUAL;
```
###
## 3. Display your age in months.
```sql
SELECT MONTHS_BETWEEN(SYSDATE, TO_DATE('01-JAN-2000','DD-MON-YYYY')) AS AGE_IN_MONTHS
FROM DUAL;
```
###
## 4. Display the current date as 15th August Friday Nineteen Ninety-Seven.
```sql
SELECT TO_CHAR(SYSDATE, 'DDth Month Day YYYY') AS FORMATTED_DATE
FROM DUAL;
```
###
## 5. Display the following output for each row from employee table.
```sql
SELECT ENAME || ' has joined the company on ' ||
       TO_CHAR(HIREDATE, 'Day DDth Month YYYY') AS DETAILS
FROM EMPLOYEE
WHERE ENAME = 'SCOTT';
```
###
## 6. Scott has joined the company on Wednesday 13th August Nineteen Ninety.
```sql
SELECT ENAME || ' has joined the company on ' ||
       TO_CHAR(HIREDATE, 'Day DDth Month YYYY') AS DETAILS
FROM EMPLOYEE
WHERE ENAME = 'SCOTT';
```
###
## 7. Find the date for nearest Saturday after current date.
```sql
SELECT NEXT_DAY(SYSDATE, 'SATURDAY') AS NEXT_SATURDAY
FROM DUAL;
```
###
## 8. Display current time.
```sql
SELECT TO_CHAR(SYSDATE, 'HH:MI:SS AM') AS CURRENT_TIME
FROM DUAL;
```
###
## 9. Display the date three months Before the current date.
```sql
SELECT ADD_MONTHS(SYSDATE, -3) AS THREE_MONTHS_BEFORE
FROM DUAL;
```
###
## 10. Display those employees who joined in the company in the month of Dec.
```sql
SELECT *
FROM EMPLOYEE
WHERE TO_CHAR(HIREDATE, 'MON') = 'DEC';
```
###
## 11. Display those employees whose first 2 characters from hire date -last 2 characters of salary.
```sql
SELECT *
FROM EMPLOYEE
WHERE SUBSTR(TO_CHAR(HIREDATE,'DD'),1,2) =
      SUBSTR(TO_CHAR(SAL), -2);
```
###
## 12. Display those employees whose 10% of salary is equal to the year of joining.
```sql
SELECT *
FROM EMPLOYEE
WHERE (SAL * 0.10) = TO_NUMBER(TO_CHAR(HIREDATE,'YYYY'));
```
###
## 13. Display those employees who joined the company before 15 of the months.
```sql
SELECT *
FROM EMPLOYEE
WHERE HIREDATE < ADD_MONTHS(SYSDATE, -15);
```
###
## 14. Display those employees who has joined before 15th of the month.
```sql
SELECT *
FROM EMPLOYEE
WHERE TO_NUMBER(TO_CHAR(HIREDATE,'DD')) < 15;
```
###
## 15. Display those employees whose joining DATE is available in deptno.
```sql
SELECT *
FROM EMPLOYEE
WHERE TO_NUMBER(TO_CHAR(HIREDATE,'DD')) = DEPTNO;
```
