**그룹 함수**

- 하나 이상의 행을 그룹으로 묶어 연산하여, 하나의 결과를 나타내는 함수이다.
- **SUM**
    - 해당 컬럼 값들에 대한 총합을 구하는 함수이다.
    - 사원의 급여를 출력하되 단일행 함수 ROUND로 천단위 이하를 반올림하는 쿼리문

        > SQL> SELECT DEPTNO, SAL, ROUND(SAL, -3) FROM EMP;  단일행 함수는 각 행에 대해서 함수의 결과가 구해지기 때문에 결과가 여러 개의 로우로 구해진다.

        ![https://wikidocs.net/images/page/3941/1.PNG](https://wikidocs.net/images/page/3941/1.PNG)

    - 그룹 함수를 이용해서 사원의 총 급여를 구하는 쿼리문

        > SQL> SELECT SUM(SAL) FROM EMP;  그룹함수의 결과는 사원이 총 14명인데도 결과는 하나의 행으로 출력된다.

        ![https://wikidocs.net/images/page/3941/2.PNG](https://wikidocs.net/images/page/3941/2.PNG)

- **AVG**
    - 해당 컬럼 값에 대해 평균을 구하는 함수이다.
    - 예) 급여 평균을 구하는 쿼리문

        > SQL> SELECT AVG(SAL) FROM EMP;

        ![https://wikidocs.net/images/page/3941/5.PNG](https://wikidocs.net/images/page/3941/5.PNG)

---

- **MAX/MIN**
    - MAX : 지정한 컬럼 값 중에서 최대값을 구하는 함수이다.
    - MIN: 해당 컬럼 값들의 최소값을 구하는 함수이다.
        - 예) 가장 높은 급여와 가장 낮은 급여를 구하는 쿼리문

            > SQL> SELECT MAX(SAL), MIN(SAL) FROM EMP;

            ![https://wikidocs.net/images/page/3941/6.PNG](https://wikidocs.net/images/page/3941/6.PNG)

    - 만약 사원들의 최대 급여와 최대 급여를 받는 사원의 이름도 함께 구하려면 어떻게 해야할까?
    - [SELECT ENAME, MAX(SAL) FROM EMP;]를 실행해보자. 오류가 날 것이다.
    - 그 이유는 **그룹 함수의 결과값은 하나인데, 그룹 함수를 적용하지 않은 단순 컬럼의 로우의 개수는 14개이기 때문에 산출되는 로우의 수가 달라 둘을 매치 시킬 수 없기 때문이다.**

    ---

- **COUNT**
    - 테이블에서 조건을 만족하는 행위 개수를 반환하는 함수이다.
    - COUNT 함수에 특정 컬럼을 기술하는 경우 해당 컬럼 값을 갖고 있는 로우의 개수를 계산하여 반환한다.
    - COUNT 함수는 NULL값에 대한 개수를 세지 않는다.
    - [SELECT JOB FROM EMP ORDER BY JOB;]를 실행하면 같은 내용이 중복되어 있고, 중복된 로우까지 카운트 하고 있다는 것을 알 수 있다. 이럴땐 중복행 제거 키워드인 **DISTINCT** 함수를 사용하면 된다.
    - 예) 사원 테이블의 사원들 중에서 커미션(COMM)을 받은 사원의 수를 구하는 쿼리문

        > SQL> SELECT COUNT(COMM) FROM EMP;

        ![https://wikidocs.net/images/page/3941/7.PNG](https://wikidocs.net/images/page/3941/7.PNG)

    - 예) 중복 제거를 반영하여 담당업무의 개수를 구하는 쿼리문

        > SQL> SELECT COUNT(DISTINCT JOB) 업무수 FROM EMP;

        ![https://wikidocs.net/images/page/3941/8.PNG](https://wikidocs.net/images/page/3941/8.PNG)
