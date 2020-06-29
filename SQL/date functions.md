# 날짜 함수

- DATA(날짜)형에 사용하는 함수
- 날짜 또는 기간을 결과로 얻는다.
- SYSDATE
    - 현재 날짜를 반환
    - 시스템 시간을 현재 날짜로 출력
        - SQL> SELECT SYSDATE FROM DUAL;

        ![Untitled 1](https://user-images.githubusercontent.com/58853370/86020345-c3a2a900-ba62-11ea-8b7f-d94db24101d2.png)

- 날짜 연산
    - 날짜 + 숫자 : 숫자만큼 지난 날짜 계산
    - 날짜 - 숫자 : 숫자만큼 이전 날짜 계산
    - 날짜 - 날짜 : 두 날짜 사이의 기간 계산
    - SYSDATE + 1 : 내일 날짜
    - SYSDATE -1 : 어제 날짜

- 지난 개월 수 구하기 MONTHS BETWEEN
    - 두 날짜 사이 개월수 계산
    - E.G. 각 직원들이 근무한 개월 수를 구하시오
        - SQL> SELECT ENAME, SYSDATE, HIREDATE, MONTHS_BETWEEN(SYSDATE, HIREDATE) 근속월수 FROM EMP;

        ![Untitled 2](https://user-images.githubusercontent.com/58853370/86020349-c4d3d600-ba62-11ea-952e-df3d394019f7.png)
        
    - 소수점 제거하기
        - SQL> SELECT ENAME, SYSDATE, HIREDATE, TRUNC(MONTHS_BETWEEN(SYSDATE, HIREDATE) ) 근속월수 FROM EMP;

        ![Untitled 3](https://user-images.githubusercontent.com/58853370/86020351-c4d3d600-ba62-11ea-8117-921519501da0.png)
        
    - ADD_MONTHS
        - 특정 개월수 더한 날짜 구하는 함수
        - 특정 개월 수 에 더한 날짜를 구하는 함수
            - SQL> SELECT ENAME, HIREDATE, ADD_MONTHS(HIREDATE, 4) FROM EMP;

    - NEXT_DAY
        - 해당 날짜로부터 시작하여 입력한 요일을 만나면.
        해당 날짜 반환
            - SQL> SELECT SYSDATE, NEXT_DAY(SYSDATE, '토요일') FROM DUAL;

    - LAST_DAY
        - 해당 달의 마지막 날짜 반환
            - SQL> SELECT HIREDATE, LAST_DAY(HIREDATE) FROM EMP;
