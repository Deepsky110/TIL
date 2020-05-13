# 메서드의 오버로드



```java
class Ex06{

	public static void main(String[] args){
		// 메서드명은 중복 불가 - 객체지향이라 순서 상관 없어서
		// 중복이 가능한 경우 - 매개변수(인자)가 다른 경우
		func01();
		func01("문자열");
		func01(1);
		func01(1,3);

	} //main end


	// 메서드의 '오버로드' : 동일명의 메서드로 인자값을 다르게 함
	// 1. 매개변수(인자)의 유무
	// 2. 매개변수(인자)의 개수
	// 3. 매개변수(인자)의 타입

	//public static int func01(){
	//	return 100;
	//} //return 받은 값을 쓸지 void를 쓸지 알 수 없음.


	public static void func01(){
		System.out.println("func01()... run...");
	}

	public static int func01(String msg){
		System.out.println(">>>"+msg);
		return 100; // int, double 뭐든 상관없다. void가 아니면 return만 주면된다.
	}

	public static double func01(int a){
		System.out.println(a+"param func01()...run...");
		return 3.14; // double이라서
	}

	public static void func01(int a, int b){
		System.out.println(a+"param, "+b+"param func01()...run...");
	}

} //class end
```

```java
<실행 결과>
c:\javaWorkspace\day06>javac -encoding utf8 Ex06.java

c:\javaWorkspace\day06>java Ex06
func01()... run...
>>>문자열
1param func01()...run...
1param, 3param func01()...run...    
```



System.out.println();
System.out.println(1234);
System.out.println("출력");

지금까지 써왔던 위의 내용도 메서드의 오버로드!

<br>

### 잘못된 예시

```java
class Ex07{

	public static void main(String[] args){
		func1(123);
		func1(3.14);
	} //main end

	public static void func1(double w){
		// double w=1234; 자동 형변환이 일어난다
		System.out.println("param :"+w);
	}

	public static void func1(int w){
		System.out.println("param :"+w);
	}

} //class end
```

```java
<실행 경과>
c:\javaWorkspace\day06>javac -encoding utf8 Ex07.java

c:\javaWorkspace\day06>java Ex07
param :123
param :3.14
```

실행은 가능하나 쓰지 말자.  
**자동 형변환(오토캐스팅)** 이 일어난 것인데  
결과값만 보고 오해할 수 있다.
