### DUAL 테이블

- 한 행으로 결과를 출력할 때 사용
- 산술 연산, 가상 컬럼 등의 값을 한번만 출력할 때 사용

```sql
SQL> SELECT SYSDATE FROM DUAL;
```

## 숫자 함수

숫자 데이터를 처리하기 위한 함수

### ABS

- 절대값을 구하는 함수

```sql
SELECT ABS(-5) FROM DUAL; 
```

### FLOOR

- 소수점 아래를 버리는 함수

```sql
SELECT FLOOR(3.14) FROM DUAL;
```

### ROUND

- 반올림하는 함수
- 특정 자릿수 지정 가능

```sql
SELECT ROUND(3.55) FROM DUAL;

SELECT ROUND(3.5678, 2) FROM DUAL;
```

- 특정 자릿수가 음수일 경우
1,10,100 단위 순으로 반올림

### TRUNC

- 특정 자릿수에서 잘라내는 기능
    - 두번째 인자값이 없는 경우 : 소수점 자리에서 버림
    - 두번째 인자값 2 : 소수점 이하 세번째 자리에서 버림
    - 두번째 인자값 0 : 소수점 자리에서 버림
    - 두번째 인자값 -1 : 일의 자리에서 버림

```sql
SELECT TRUNC(34.5678, 2), TRUNC(34.5678, -1), TRUNC(34.5678), TRUNC(34.5678, 0) FROM DUAL;
```

### MOD

- 나누기 연산 후 나머지를 구하는 함수

```sql
SELECT MOD(27, 2), MOD(27, 5), MOD(27, 7) FROM DUAL;
```
