## String Functions

### **UPPER**

- 대문자로 변환하는 함수

    > SQL> SELECT 'Welcome to Oracle' "적용전", UPPER('Welcome to Oracle') "UPPER적용후" FROM DUAL;



### **LOWER**

- 소문자로 변환하는 함수

    > SQL> SELECT 'Welcome to Oracle' "적용전", LOWER('Welcome to Oracle') "LOWER적용후" FROM DUAL;



### **INITCAP**

- 첫 글자만 대문자로 변환하는 함수

    > SQL> SELECT 'WELCOME TO ORACLE' "적용전", INITCAP('WELCOME TO ORACLE') "INITCAP적용후" FROM DUAL;



- **LENGTH**
    - 문자의 길이를 구하는 함수

        > SQL> SELECT LENGTH('Oracle'), LENGTH('오라클') FROM DUAL;



- **LENGTHB**
    - 바이트 수를 알려주는 함수

        > SQL> SELECT LENGTHB('Oracle'), LENGTHB('오라클') FROM DUAL;



- **INSTR**
    - 특정 문자의 위치를 구하는 함수.
    - 예) 'Welcome To Oracle'에서 'O'가 저장된 위치 값을 구하는 쿼리문

        > SQL> SELECT INSTR('Welcome To Oracle', 'O') FROM DUAL;



- **SUBSTR/SUBSTRB**
    - SUBSTR : 대상 문자열이나 컬럼의 자료에서 시작 위치부터 선택 개수만큼의 문자를 추출
    - 인덱스 4부터 시작해서 문자 3개를 추출하는 쿼리문

        (오라클에서 인덱스는 0이아닌 1부터 시작)

        > SQL> SELECT SUBSTR ('Welcome to Oracle', 4, 3) FROM DUAL;


    - 예) 사원들의 입사일에서 입사 년도와 입사 달을 출력하는 쿼리문

        > SQL> SELECT ENAME, 19||SUBSTR(HIREDATE, 1, 2)년도, SUBSTR(HIREDATE, 4, 2)달 FROM EMP;


    - 예) 9월에 입사한 사원을 출력하는 쿼리문

        > SQL> SELECT ENAME, 19||SUBSTR(HIREDATE, 1, 2)년도, SUBSTR(HIREDATE, 4, 2)달 FROM EMP WHERE SUBSTR(HIREDATE, 4, 2) = '09';


    - SUBSTRB : 명시된 개수만큼의 문자가 아닌 바이트 수를 잘라낸다.
    - SUBSTR은 한글 한자를 1바이트로 보지만 SUBSTRB는 2바이트로 보기 때문에 밑에 결과는 다르게 나타난다.

        > SQL> SELECT SUBSTR('웰컴투오라클', 3, 4), SUBSTRB('오라클오라클', 3, 4) FROM DUAL;



### **LPAD/RPAD**

- 특정 기호로 채우는 함수이다.
    - LPAD(LEFT PADDING) : 오른쪽 정렬 후 왼쪽에 생긴 빈 공백에 특정 문자를 채우는 함수이다.
    - 예) 20자리를 마련한 후 오른쪽에 대상 문자열을 출력하고, 왼쪽에 생긴 빈 공간을 '#' 기호로 채우는 쿼리문

        > SQL> SELECT LPAD('ORACLE', 20, '#') FROM DUAL;


    - RPAD(RIGHT PADDING) : 왼쪽 정렬 후 오른쪽에 생긴 빈 공백에 특정 문자를 채우는 함수이다.
    - 예) 20자리를 마련한 후 왼쪽에 대상 문자열을 출력하고, 오른쪽에 생긴 빈 공간을 '#' 기호로 채우는 쿼리문

        > SQL> SELECT RPAD('ORACLE', 20, '#') FROM DUAL;



### **LTRIM/RTRIM**

- 공백 문자를 삭제하는 함수이다.
    - LTRIM : 문자열 왼쪽(앞)의 공백 문자들을 삭제

        > SQL> SELECT LTRIM(' ORACLE') FROM DUAL;

      

    - RTRIM : 문자열 오른쪽(뒤)의 공백 문자들을 삭제

        > SQL> SELECT RTRIM('ORACLE ') FROM DUAL;



### **TRIM**

- 특정 문자를 잘라내는 함수
- 컬럼이나 대상 문자열에서 특정 문자가 첫 번째나 마지막에 위치해 있으면, 해당 특정 문자를 잘라낸 후 남은 문자열만 반환

    > SQL> SELECT TRIM('a' FROM 'aaaaORACLEaaaaa') FROM DUAL;


- 공백 문자 삭제

    > SQL> SELECT TRIM(' ORACLE ') FROM DUAL;

