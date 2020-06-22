## 데이터베이스 관리 시스템 (DBMS)

- 기업이 지속적으로 유지 관리해야 하는 방대한 양의 데이터를 편리하게 저장
- 효율적으로 관리하고 검색할 수 있는 환경을 제공해주는 시스템 소프트웨어

## 관계형 DBMS

- Relational Data Base Management System (RDBMS)
- table과 table 사이에 관계 존재
- 테이블 스키마 정의를 통해 데이터를 제한

### Oracle Database 10g

설치후 cmd에 sqlplus

교육용계정 scott / tiger

## SQL의 종류

1. TCL (Transaction Control Language)
2. DDL (Data Definition Language) - 데이터 스키마를 구성
3. DCL (Data Control Language) - 컨트롤 권한을 주는 Language
4. DML (Data Manipulation Language)
    - CRUD : Create / Read / Updata / Delete


쿼리문장은 대소문자를 구분하지 않으나

value 값은 대소문자를 구분한다!

문자열은 ' ' 단일 따옴표로 표현.

날짜 단일 따옴표 안에 표시 (년/월/일)


### READ

```sql
1. 급여가 1000에서 3000 사이에 있는 사원
select ename, sal from emp where sal>=1000 and sal<=3000;
select ename, sal from emp where sal between 1000 and 3000;

2. 사원번호가 7844이거나 7654이거나 7521인 사원
select ename, empno from emp where empno in(7844, 7654, 7521);

3. 직급이 MANAGER가 아닌 사원
select ename, job from emp where job!='MANAGER';
select ename, job from emp where job<>'MANAGER';
select ename, job from emp where job^='MANAGER';
select ename, job from emp where not job = 'MANAGER';

4. 급여가 1500과 2500사이인 사원의 사번, 이름, 급여
select empno, ename, sal from emp where sal>=1500 and sal<=2500;

5. 커미션이 300 이거나 500 이거나 1400 중의 하나인 사원의 이름, 급여, 커미션
select ename, sal, comm from emp where comm in(300,500,1400);

6. 이름이 K로 시작하는 사원
select ename from emp where ename like 'K%';

7. 이름에 A를 포함하지 않는 사원의 사번, 이름
select empno, ename from emp where ename not like '%A%';

8. 자신의 사수(mgr)이 없는 사원의 이름과 직급
select ename, job from emp where mgr is null;

9. 오름 차순 정렬 (끝에 asc 생략)
select empno, ename, hiredate from emp order by hiredate;

10. 내림 차순 정렬
select empno, ename, hiredate from emp order by hiredate desc;

# select empno, ename, sal from emp order by sal where sal<2000; 순서오류
==> select empno, ename, sal from emp where sal<2000 order by sal; (O)
```

### CREATE

```sql
SQL> insert into dept values(50, '영업부', '서울');

1 개의 행이 만들어졌습니다.

SQL> select * from dept;

    DEPTNO DNAME                        LOC
---------- ---------------------------- --------------------------
        10 ACCOUNTING                   NEW YORK
        20 RESEARCH                     DALLAS
        30 SALES                        CHICAGO
        40 OPERATIONS                   BOSTON
        50 영업부                       서울
```

### UPDATE

```sql
SQL> update dept set dname = '관리부' where deptno=50;

1 행이 갱신되었습니다.

SQL> select * from dept;

    DEPTNO DNAME                        LOC
---------- ---------------------------- --------------------------
        10 ACCOUNTING                   NEW YORK
        20 RESEARCH                     DALLAS
        30 SALES                        CHICAGO
        40 OPERATIONS                   BOSTON
        50 관리부                       서울
```

### DELETE

```sql
SQL> delete from dept where deptno=50;

1 행이 삭제되었습니다.

SQL> select * from dept;

    DEPTNO DNAME                        LOC
---------- ---------------------------- --------------------------
        10 ACCOUNTING                   NEW YORK
        20 RESEARCH                     DALLAS
        30 SALES                        CHICAGO
        40 OPERATIONS                   BOSTON
```
