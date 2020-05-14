# 논스태틱 메서드

```java
package com.bit.day07;

class Ex01{
	// 메서드
	// 1. 정적메서드, 클래스메서드, static메서드...
	// 2. 인스턴스 메서드, non-static메서드...


	public void func01(){
		System.out.println("non-static method...");
		System.out.println("인스턴스 메서드");
	}

	public static void func02(){
		System.out.println("static메서드");
		System.out.println("클래스메서드");
		System.out.println("정적메서드");
	}

	public static void main(String[] args){
		func02();		// 오버로딩 후 메서드 호출
		System.out.println("---------------------");
		// 클래스명 참조변수 = new 클래스명();
		Ex01 me=new Ex01();		//non-static메서드를 호출!
		me.func01();
		System.out.println("---------------------");
		me.func02();// 권장하지 않음 - 스태틱인지 논스태틱인지 구별 어려움
	}
    
}
```

```
<실행 결과>
C:\javaWorkspace>javac -d . -encoding utf8 .\day07\Ex01.java

C:\javaWorkspace>java com.bit.day07.Ex01
static메서드
클래스메서드
정적메서드
---------------------
non-static method...
인스턴스 메서드
---------------------
static메서드
클래스메서드
정적메서드
```

<br>

```java
package com.bit.day07;

class package com.bit.day07;

class Ex02{
	/*
		메서드 호출법칙
		1. (direct call) non-static method - static method
		2. (direct call) non-static method - non-static method
		3. (direct call) static method - static method
		4. (reference call) static method - non-static method
	*/

	public static void main(String[] args){
		//Ex02 me=new Ex02();  //me라는 참조변수를 만든다.
		//me.func02();
		func01();
	}

	public static void func01(){
		System.out.println("static mehod1");
		func11(); //스태틱에서 스태틱 메서드는 직접 호출 가능
		//func22(); //스태틱-논스태틱 호출이라 참조변수 통해 호출해야함
	}

	public void func02(){
		System.out.println("non-static method1");
		func22();
	}

	public static void func11(){
		System.out.println("static mehod2");
	}

	public void func22(){
		System.out.println("non-static method2");
	}

}Ex02{
	/*
		메서드 호출법칙
		1. (direct call) non-static method - static method
		2. (direct call) non-static method - non-static method
		3. (direct call) static method - static method
		4. (reference call) static method - non-static method
	*/

	public static void main(String[] args){
		//Ex02 me=new Ex02();  //me라는 참조변수를 만든다.
		//me.func02();
		func01();
	}

	public static void func01(){
		System.out.println("static mehod1");
		//func11(); //스태틱에서 스태틱 메서드는 직접 호출 가능
		//func22(); //스태틱-논스태틱 호출이라 참조변수 통해 호출해야함
	}

	public void func02(){
		System.out.println("non-static method1");
		func22();
	}

	public static void func11(){
		System.out.println("static mehod2");
	}

	public void func22(){
		System.out.println("non-static method2");
	}

}
```

```java
package com.bit.day07;

class Ex03{

	public static void main(String[] args){
		Ex02.func01(); //Ex02클래스에 있는 메서드
		System.out.println("--------------------");
		Ex02 ex02=new Ex02();
		ex02.func02(); //func02가 논스태틱 메서드라 참조변수 생성
		System.out.println("--------------------");
		Ex01.func02(); // 스태틱 메서드는 클래스 정보를 통해 접근
		System.out.println("--------------------");
		Ex01 ex01=new Ex01();
		ex01.func01();
	}
}
```

```
<실행 결과>
C:\javaWorkspace>javac -d . -encoding utf8 .\day07\Ex03.java

C:\javaWorkspace>java com.bit.day07.Ex03
static mehod1
static mehod2
--------------------
non-static method1
non-static method2
--------------------
static메서드
클래스메서드
정적메서드
--------------------
non-static method...
인스턴스 메서드
```

<br>

```java
package day07;

class Ex04{
	// 다른 클래스에서 가져다 쓰기만 할 것이기 때문에
    // 자동 실행해주는 main이 필요없다.

	public static void func01(){
		System.out.println("static method");
	
	}

	public void func02(){
		System.out.println("non-static method");
	}
}
```

```java
package day07;

class Ex05{

	public static void main(String[] args){

		Ex04.func01();
		Ex04 me=new Ex04();
		me.func02();

    }
}
```

둘다 컴파일 진행 후 실행시켜보면 정상 실행된다.  


클래스 파일 삭제 후

```
C:\javaWorkspace>javac -d . -encoding utf8 .\day07\Ex05.java

C:\javaWorkspace>java day07.Ex05
static method
non-static method
```

하면 Ex05만 컴파일 했는데 Ex04까지 같이 컴파일 된다.  
Ex04를 수정하고 Ex05를 다시 컴파일하면 Ex04까지 처리된다.  

<br>

### 다른 패키지에서 메서드 가져오기

```java
package com.bit.day07;

public class Ex01{

	public void func01(){
		System.out.println("non-static method...");
		System.out.println("인스턴스 메서드");
	}

	public static void func02(){
		System.out.println("static메서드");
		System.out.println("클래스메서드");
		System.out.println("정적메서드");
	}
}
```

```java
package day07;

class Ex05{

	public static void main(String[] args){

		com.bit.day07.Ex01.func02();
		com.bit.day07.Ex01 me = new com.bit.day07.Ex01();
		me.func01();
	}
}
```

package가 다르다.  
어떤 Ex01을 가져올건데?  
가져올 패키지의 클래스를 public으로 설정해주고  
작업하는 클래스에서 패키지의 주소와 함께 호출한다.  
(지금까지는 같은 패키지 안에서 처리해서 필요 없던 과정)

```
<실행 결과>
C:\javaWorkspace>javac -d . -encoding utf8 .\day07\Ex01.java

C:\javaWorkspace>javac -d . -encoding utf8 .\day07\Ex05.java

C:\javaWorkspace>java day07.Ex05
static메서드
클래스메서드
정적메서드
non-static method...
인스턴스 메서드
```
