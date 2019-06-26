SELECT STAFF_CODE,STAFF_NAME,DESIGN_CODE FROM STAFF_MASTER WHERE HIREDATE<'4-march-2000';
SELECT STAFF_NAME,DESIGN_CODE FROM STAFF_MASTER WHERE HIREDATE<'4-march-2014' AND STAFF_SAL>10000 AND STAFF_SAL<52000;
------------------------------------------------------------------------------------------------------------------------

/*1.1 2 EXP OF 18 YEARS */
SELECT STAFF_CODE,STAFF_NAME,DESIGN_CODE FROM STAFF_MASTER WHERE HIREDATE<'4-march-2000';

-----------------------------------------------------------------------------------------------------------------------------
/*1.1 3*/

SELECT * FROM STAFF_MASTER WHERE MGR_CODE IS NULL;

---------------------------------------------------------------------------------------------------------------------------
/*1.1 4*/
SELECT BOOK_MASTER.* FROM BOOK_MASTER WHERE BOOK_PUB_YEAR<2004 and BOOK_PUB_YEAR>2000;

SELECT * FROM BOOK_MASTER WHERE BOOK_NAME LIKE '%&%';

------------------------------------------------------------------------------------------------------------------------------
/*1.1 5*/
SELECT STAFF_NAME FROM STAFF_MASTER WHERE STAFF_NAME LIKE '___';
/*ORRRRRRRRRRRRR*/
SELECT STAFF_NAME FROM STAFF_MASTER WHERE STAFF_NAME NOT LIKE '____';
-----------------------------------------------------------------------------------------------------------------------------
/**2.1 1*/
SELECT staff_name,LPAD(STAFF_SAL,15,'$') from STAFF_MASTER;

--------------------------------------------------------------------------------------------------------------
/*2.1 2 */

SELECT STUD_NAME,TO_CHAR(STUD_DOB,'MONTH DD YYYY') AS "STUDEND DOB" FROM STUDENT_MASTER 
WHERE TO_CHAR(STUD_DOB,'DAY') LIKE  ('%SATURDAY%') OR TO_CHAR(STUD_DOB,'DAY') LIKE  ('%SUNDAY%') ;


-----------------------------------------------------------------------------------------------------------------
/*2.1 3*/
SELECT  STAFF_NAME ,ROUND((SYSDATE-HIREDATE)/365*12) AS " MONTHS WROKED"
FROM STAFF_MASTER ORDER BY ROUND((SYSDATE-HIREDATE)/365*12);

------------------------------------------------------------------------------------------------------------------------------------------
/*2.1 4*/

SELECT * FROM STAFF_MASTER WHERE TO_CHAR(HIREDATE,'DD') BETWEEN 1 AND 15 AND TO_CHAR(HIREDATE,'MONTH') LIKE '%DECEMBER%' ;
-------------------------------------------------------------------------------------------------------------------------------------
/*2.1 5 galt hhhh*/

SELECT STAFF_SAL,DECODE(STAFF_SAL,1000,'A',25000,'B','OTHERS') XYZ FROM STAFF_MASTER;  
----------------------------------------------------------------------------------------------------------------------------------------
/*2.1 6*/
SELECT STAFF_NAME,TO_CHAR(HIREDATE,'DD MONTH YYYY') AS HIRE_DATE,TO_CHAR(HIREDATE,'DAY')AS DAY FROM STAFF_MASTER 
ORDER BY TO_CHAR(HIREDATE,'DAY') DESC;
-------------------------------------------------------------------------------------------------------------------------------------
/*2.1 7*/

SELECT INSTR('Mississippi','i',1,3) FROM DUAL;

--------------------------------------------------------------------------------------------------------------------------------------
/*2.1 8*/
SELECT TO_CHAR(NEXT_DAY(SYSDATE,'TUESDAY'),'DD MONTH ,YYYY') AS DAY FROM DUAL WHERE NEXT_DAY(SYSDATE,'TUESDAY')<LAST_DAY(SYSDATE) ;
----------------------------------------------------------------------------------------------------------------------------------
/*2.1 9*/

SELECT STUD_CODE,STUD_NAME,DECODE(DEPT_CODE,91,'MECH',92,'ETX','OTHERS') DEPARTMENT_NAME FROM STUDENT_MASTER;
----------------------------------------------------------------------------------------------------------------------
/*2.2 1*/

SELECT MAX(STAFF_SAL) AS MAXIMUM, MIN(STAFF_SAL) AS MINIMUM, AVG(STAFF_SAL) 
AS AVERAGE ,SUM(STAFF_SAL) AS TOTAL FROM STAFF_MASTER GROUP BY DEPT_CODE;
-----------------------------------------------------------------------------------------------------------------------------------
/*2.2 2*/

SELECT DEPT_CODE,COUNT(EMP_NAME),COUNT(STAFF_NAME) FROM EMP,STAFF_MASTER,DESIGNATION_MASTER 
WHERE DESIGN_NAME='Manager';  

-------------------------------------------------------------------------------------------------------------
/*2.2 2*/
select emp.dept_code,sum(MGR) as total_number_of_manager from emp group by DEPT_CODE;

--------------------------------------------------------------------------------------------------------------------
/*2.2 3*/
SELECT DEPT_CODE,SUM(SAL) FROM EMP WHERE JOB!='Manager' GROUP BY DEPT_CODE;

------------------------------------------------------------------------------------------------------------------
/*3.1 1*/
 SELECT S.STAFF_NAME,
  D.DEPT_CODE,
  D.DEPT_NAME,
  S.STAFF_SAL
FROM STAFF_MASTER S,
  DEPARTMENT_MASTER D
WHERE S.DEPT_CODE=D.DEPT_CODE
AND STAFF_SAL    >20000;

----------------------------------------------------------------------------------------------------------------------
/*3.1 2*/

SELECT DISTINCT STAFF_CODE,STAFF_NAME,EMP.EMPNO AS " MANAGER NO",ENAME AS "MANAGER NAME "
FROM DESIGNATION_MASTER,DEPARTMENT_MASTER,EMP,STAFF_MASTER 
WHERE  EMP.MGR=STAFF_MASTER.MGR_CODE AND EMP.JOB='Manager';

  SELECT S.STAFF_CODE AS STAFF# ,
  S.STAFF_NAME      AS STAFF,
  D.DEPT_NAME,
  S.MGR_CODE AS MGR#
FROM STAFF_MASTER S,
  DEPARTMENT_MASTER D
WHERE S.DEPT_CODE=D.DEPT_CODE;
