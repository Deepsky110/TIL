# 변수



### 예제1

```java
package com.bit.day08;

class Ex02{
	
	static int su1; // 변수 선언&초기화 동시에 해주거나(e.g int su1=123;)
					// 선언만 해줘도(int su1;) 사용 가능
    				// 선언만 하면 자료형 default 값
    				// (0을 자료형으로 표현한 값) 나옴
	static String msg=""; // String도 참조변수 - 가르키는 주소가 없으면							// (String msg;) null로 나온다.
	
	public static void main(String[] args){
		System.out.println(msg+"aaa");
		Ex02 me=new Ex02();
		me.func02();
	}

	public void func02(){
		System.out.println(su1);
	}

	public static void func01(){
		System.out.println(su1);
	}

} //class end
```

```
<실행 결과>
aaa
0
```



<br>

### 예제2

```java
package com.bit.day08;

class Ex03{
	static int a; // 스태틱으로 선언

	public static void func01(){
		a++;
		System.out.println("a="+a);
	} // 스태틱 메서드에서 쓰는데 문제 없음

	public static void func02(){
		a++;
		int b=a;
		System.out.println("b="+b);
	}

	public static void main(String[] args){
		a=1234;
		func01();
		func02();
	}

} //class end
```

```
<실행 결과>
a=1235
b=1236
```



<br>

### 예제3

```java
package com.bit.day08;

class Ex04{
	int su=1234; // 논스태틱으로 선언

	public void plus(){
		su++;
	}

	public void func01(){
		System.out.println("func01 su=+"+su);
	} // 논스태틱 메서드에서는 바로 접근 가능

	public static void main(String[] args){
		Ex04 me=new Ex04();
		//System.out.println(me.su);
		me.func01();
		me.plus();
		me.func01();
		me.plus();
		me.func01();
		me=new Ex04(); // 새로운 객체 도입으로 다시 처리
		me.plus();
		me.func01();
	} // 스태틱 메서드에서는 바로 접근 불가능

} //class end
```

```
<실행 결과>
func01 su=+1234
func01 su=+1235
func01 su=+1236 // 출력 후 me=new Ex04라는 새로운 객체 도입
func01 su=+1235
```

<br>

```java
package com.bit.day08;

class Ex04{
	static int su=1234; // 스태틱으로 선언

	public void plus(){
		su++;
	}

	public void func01(){
		System.out.println("func01 su=+"+su);
	} 

	public static void main(String[] args){
		Ex04 me=new Ex04();
		//System.out.println(me.su);
		me.func01();
		me.plus();
		me.func01();
		me.plus();
		me.func01();
		me=new Ex04();
		me.plus();
		me.func01();
	}
} //class end
```

```
<실행 결과>
func01 su=+1234
func01 su=+1235
func01 su=+1236
func01 su=+1237
```

<br>

### 예제4

```java
package com.bit.day08;

class Ex05{
	int a=10; // 논스태틱 선언

	public static void main(String[] args){
		Ex05 me1=new Ex05();
		Ex05 me2=new Ex05();
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
		me1.a++;
		System.out.println("me1의 a++");
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
		me1.a++;
		System.out.println("me1의 a++");
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
	}

}
```

```
<실행 결과>
me1 a=10
me2 a=10
me1의 a++
me1 a=11
me2 a=10
me1의 a++
me1 a=12
me2 a=10
```

<br>

```java
package com.bit.day08;

class Ex05{
	static int a=10; // 스태틱 선언

	public static void main(String[] args){
		Ex05 me1=new Ex05();
		Ex05 me2=new Ex05();
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
		me1.a++;
		System.out.println("me1의 a++");
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
		me1.a++;
		System.out.println("me1의 a++");
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
	}

}
```

```
<실행 결과>
me1 a=10
me2 a=10
me1의 a++
me1 a=11
me2 a=11
me1의 a++
me1 a=12
me2 a=12
```

<br>

```java
package com.bit.day08;

class Ex05{
	static int a=10; // 스태틱 선언

	public static void main(String[] args){
		int a=1234; // 지역변수가 있으니 우선적으로 가져다 쓴다
		Ex05 me1=new Ex05();
		Ex05 me2=new Ex05();
		System.out.println("me1 a="+Ex05.a); //com.bit.day08.Ex05.a를 생략
		System.out.println("me2 a="+a);
		me1.a++;
		System.out.println("me1의 a++");
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
		me1.a++;
		System.out.println("me1의 a++");
		System.out.println("me1 a="+me1.a);
		System.out.println("me2 a="+me2.a);
	}

}
```

```
<실행 결과>
me1 a=10
me2 a=1234
me1의 a++
me1 a=11
me2 a=11
me1의 a++
me1 a=12
me2 a=12
```

<br>

### 예제5

- static일 경우

```java
package com.bit.day08;

class Bank{
	static int money;
	public void add(int a){
		money+=a;
	}
	public void minus(int a){
		money-=a;
	}
	public void print(){
		System.out.println("잔금:"+money+"원");
	}

}

class Ex07{

	public static void main(String[] args){
		Bank cd=new Bank();
		cd.add(1000);
		cd.print();
		cd.minus(500);
		cd.print();
		cd.minus(300);
		cd.add(2000);
		cd.print();	
	}

}
```

```
<실행 결과>
잔금:1000원
잔금:500원
잔금:2200원
```

<br>

- non-static일 경우

```java
package com.bit.day08;

class Bank{
	int money;
	public void add(int a){
		money+=a;
	}
	public void minus(int a){
		money-=a;
	}
	public void print(){
		System.out.println("잔금:"+money+"원");
	}

}

class Ex07{

	public static void main(String[] args){

		Bank hana=new Bank(); // 하나은행 새로운 계좌 개설
		hana.add(1000);
		hana.minus(200);
		hana.minus(250);
		Bank woori=new Bank(); // 우리은행 새로운 계좌 개설
		woori.add(10000);
		hana.minus(300);
		System.out.print("하나은행 계좌 ");
		hana.print();
		System.out.print("우리은행 계좌 ");
		woori.print();		
	}

}
```

```
결과:
하나은행 계좌 잔금:250원
우리은행 계좌 잔금:10000원
```

***non-static을 활용한 객체지향 언어로  
우리가 사용하는 언어에 가까운 코드를 만들 수 있다.***
