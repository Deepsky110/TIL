# 반복문

## 2.1 for문

for문은 반복 횟수를 알고 있을 때 적합하다.

```java
for(int i=1; i<=5; i++) {
    System.out.println("Just do it")
}
```

```java
for (초기화;조건식;증감식) {
    	// 조건식이 참일 떄 수행될 문장들을 적는다.
}
```

제일 먼저 '초기화'가 수행되고,
그 이후부터는 조건식이 참인 동안 '조건식' -> '수행될 문장' -> '증감식'의 순러로 계속 반복된다.
그러다가 조건식이 거짓이 되면. for문 전체를 빠져나간다.



### 초기화

반복문에 사용될 변수를 초기화하는 부분
처음에 한번만 수행된다.



### 조건식

조건식의 값이 참(true)이면 반복을 계속하고,
거짓(false)이면 반복을 중단하고 for문을 벗어난다.



### 증감식

반복문을 제어하는 변수의 값을 증가 또는 감소시키는 식이다.
매 반복마다 변수의 값이 증감식에 의해서 점진적으로 변하다가
결국 조건식이 거짓이 되어 for문을 벗어나게 된다.

```java
for(int i=1; i<=10; i++)	{...}	// 1부터 10까지 1씩증가
for(int i=10; i>=1; i--)	{...}	// 10부터 1까지 1씩 감소
for(int i=1; i<=10; i+=2)	{...}	// 1부터 10까지 2씩 증가
for(int i=1; i<=10; i*=3)	{...}	// 1부터 10까지 3배씩 증가
```

```java
for(;;) {...} // 초기화, 조건식, 증감식 모두 생략. 조건식은 참이 된다.
```

조건식이 생략된 경우, 참(true)으로 간주되어 무한 반복문이 된다.
대신 블럭{} 안에 if문을 넣어서 특정 조건을 만족하면 for문을 빠져 나오게 해야 한다.