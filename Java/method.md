# 메서드

- public static void 메서드명(){}
- 메서드명은 반드시 소문자로 시작
- 띄어쓰기 불가능
- int와 같은 예약어 사용 불가
- 호출,실행 - 메서드명();
- 호출은 매개변수(인자), 개수, 타입이 일치해야 가능

```java
class Ex03{

	// 메서드
	// 클래스메서드, static메서드 (함수,function)
	// 재사용성

	public static void func01(){

		System.out.println("01기능을 실행합니다");
	} //func01 end 펑션을 만든다

	public static void func02(){
		int a=1234;
		System.out.println("a="+a);
	}

	public static void func03(int a){
		// int a=??? 해서 선언한 것과 같다. 중괄호 안에서만 사용가능
		a=9999; // 값을 재설정 해주는 것은 가능
		System.out.println("전달받은 데이터:"+a);
	}

	public static void main(String [] args){
		int a=1111; // func02와 int a 중복 사용이지만 compile 가능 : 메모리 때문
		System.out.println("프로그램 시작"+a);
		func03(a); // 메서드를 소환시킨다
		System.out.println("프로그램 종료"+a);
	} //main end

} //class end
```

```
c:\javaWorkspace\day06>javac -encoding utf8 Ex03.java

c:\javaWorkspace\day06>java Ex03
프로그램 시작1111
전달받은 데이터:9999
프로그램 종료1111
```

<br>

```java
	public static void func04(int a, int b){
		int c=a+b;
		System.out.println(a+"+"+b+"="+c);
	}

	public static void main(String [] args){
		int a=1111; // func02와 int a 중복 사용이지만 compile 가능 : 메모리 때문
		System.out.println("프로그램 시작"+a);
		func04(2,3); // 메서드를 소환시킨다
		System.out.println("프로그램 종료"+a);
```

```
프로그램 시작1111
2+3=5
프로그램 종료1111
```

> public static void main(String[] args) 에서 args는 변수명이다 ==> 변경 가능하다.



```java
class Ex04{

	public static void main(String[] args){
		System.out.println("main start");
		func01();
		func02();
		System.out.println("main end");
	} //main end

	public static void func01(){
		System.out.println("func01 start");
		System.out.println("void method...");
		func02();
		System.out.println("func01 end");
	} //main end

	public static void func02(){
		System.out.println("func2 start");
		System.out.println("func2 run");
		System.out.println("func2 end");
	} //main end

} //class end
```

```
main start
func01 start
void method...
func2 start
func2 run
func2 end
func01 end
func2 start
func2 run
func2 end
main end
```

<br>

```java
class Ex05{

	public static void main(String[] args){
		// Java의 main에서 가상머신을 사용하기 때문에 return 값이 필요 없다.
		// ==> main 무조건 void 사용
		int su = func01();
		func02();

		if(su>5){
			return; // func03에서 su값이 5이상이 나오게 하자 리턴되고 출력이 안됨.
		}
		System.out.println("su="+su);   
	} //main end

	public static void func02(){
		System.out.println("void method run...");
		return; // return이 존재하지만 값이 없어서 생략 ==> void
	} //func02 end

	public static int func01(){
		// void가 아닌 int를 사용, 리턴값의 타입과 일치시킨다.
		
		System.out.println("func01 method run");
		int a=3;
		int b=4;
		int c=a+b;
		return c;
	} //func01 end

} //class end
```

```java
<실행 결과>
c:\javaWorkspace\day06>javac -encoding utf8 Ex05.java

c:\javaWorkspace\day06>java Ex05
func01 method run
void method run...
```



***모든 메서드는 return가 존재한다.***  
***다만 return 값에 따라 void를 쓸지 int와 같은 타입을 적어줄지 결정된다***
