# 예외처리

```java
package com.bit.day12;

public class Ex02 {

	public static void main(String[] args) {
		// 예외처리
		String msg="1234";
//		for(int i=0; i<msg.length(); i++){
//			if(Character.isDigit(msg.charAt(i))){
//			}else{
//				System.out.println("숫자가 아닌 문자가 들어갔습니다");
//				return;
//			}
//		}
		try{
			System.out.println("다음에서 에러가 발생할수도 있습니다");
			Integer su=new Integer(msg);
			System.out.println("다행히 에러가 없었네요");
			System.out.println("su="+su);
		}catch(NumberFormatException e){
			System.out.println("오류를 잡아냈습니다");
		}
		System.out.println("프로그램은 실행했었습니다");
	}
}
```

```java
package com.bit.day12;

public class Ex03 {

	public static void main(String[] args) {
		String msg = "20";
		int[] arr=new int[10];
		try{
			int su = Integer.parseInt(msg);
			double su2 = 10.0/su;
			arr[su]=(int)su2;
			System.out.println("10/"+msg+"="+su2);
		}catch(NumberFormatException e){
			System.out.println("숫자로만 입력하세요");
		}catch(ArrayIndexOutOfBoundsException ex){
			System.out.println("배열의 인덱스가 범위 밖으로 호출하였습니다");
		}
	}
}
```

```
<실행 결과>
다음에서 에러가 발생할수도 있습니다
다행히 에러가 없었네요
su=1234
프로그램은 실행했었습니다
```

<br>

```java
package com.bit.day12;

public class Ex04 {

	public static void main(String[] args){
		String msg="2ㅁ";
		int[] arr=new int[10];
		try{
			int su=Integer.parseInt(msg);
			double su2=10.0/su;
			arr[su]=(int)su2;
			System.out.println("10/"+msg+"="+su2);
		}catch(Exception e){
			System.out.println("에러를 회피했습니다"); // 두 오류의 부모 class오류를 입력하면 자식들 다 catch함
		}
	}
}
```

<br>

```java
package com.bit.day12;

public class Ex05 {

	public static void main(String[] args) {
		String msg = "5";	// String클래스 앞에 java.lang이 생략된것 
							// (유일하게 생략 가능 패키지)
		int[] arr = {1,2,3,4,5};
		try{
			int su = Integer.parseInt(msg);
			System.out.println(arr[su]);
		}catch(NumberFormatException e){
		}catch(ArrayIndexOutOfBoundsException e){	
		}catch(Exception e){	// 조상클래스를 가장 나중으로
		}						// 주로 Exception을 사용한다
	}
}
```

<br>

```java
package com.bit.day12;

public class Ex06 {

	public static void main(String[] args) {
		System.out.println("main start...");
		for(int i=0; i<=5; i++){
			try{
			func01(i);
			}catch(java.lang.ArrayIndexOutOfBoundsException e){
				System.out.println(e.toString());
			}
		}
		System.out.println("main end...");
	}
	
	public static void func01(int a){
		System.out.println("에러발생전");
		int[] arr = {1,2,3,4,5};
		try{
			System.out.println(arr[a]);
		}catch(ArrayIndexOutOfBoundsException e){ //java.lang 생략
			System.out.println("스스로 해결함");
		}
		System.out.println("에러발생안함");
	}

}
```

호출한 main에서 try-catch하거나  
에러 발생한 쪽에서 직접 적용하거나  

```
<실행 결과>
main start...
에러발생전
1
에러발생안함
에러발생전
2
에러발생안함
에러발생전
3
에러발생안함
에러발생전
4
에러발생안함
에러발생전
5
에러발생안함
에러발생전
java.lang.ArrayIndexOutOfBoundsException: 5
main end...
```

<br>

```java
package com.bit.day12;

public class Ex07 {

	public static void main(String[] args) {
		System.out.println("main start...");
		try{
		func01();
		}catch(Exception e){	// NumberFormatException 대신 사용, 다형성 때문에 가능
			System.out.println("회피");
			System.out.println(e); // func01에서 받은 에러를 출력
			System.out.println(e.toString()); // 시스템에게 명령하여 출력 거는 원리 - 리소스 낭비
			System.out.println(e.getMessage());
			System.out.println(e.getLocalizedMessage());
			e.printStackTrace(); // 에러 메세지 출력할 때 사용 권장, 출력은 안하고 메세지만 호출
		}
		System.out.println("main end...");

	}

	public static void func01() throws NumberFormatException{
        						//	NumberFormatException err = new NumberFormatException();
        						// 객체 생성, 호출되면 에러 객체를 가져간다
//		throw err;
		int a = Integer.parseInt("a");	// int 타입에 a를 입력해서 에러	
									// parseInt()의 기능은 String타입의 숫자(문자x)를 int타입으로 변환
	}	
}
```

```
<실행 결과>
main start...
회피
java.lang.NumberFormatException: For input string: "a"
java.lang.NumberFormatException: For input string: "a"
For input string: "a"
For input string: "a"
main end...
java.lang.NumberFormatException: For input string: "a"
	at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
	at java.lang.Integer.parseInt(Integer.java:580)
	at java.lang.Integer.parseInt(Integer.java:615)
	at com.bit.day12.Ex07.func01(Ex07.java:24)
	at com.bit.day12.Ex07.main(Ex07.java:8)
```
<br>

# 예외처리2


**try-catch의 범위를 어떻게 지정해주느냐에 따라 수행이 다르다**

```java
package com.bit.day12;

public class Ex08 {

	public static void main(String[] args) {
		int[] arr={1,2,3,4,5};
		for(int i=0; i<=10; i++){
			try{
				System.out.println(arr[i]);
			}catch(ArrayIndexOutOfBoundsException e){ // try-catch의 범위를 어떻게 지정해주느냐에 따라 수행이 다르다
				System.out.println("에러회피");
			}
		}
	}
}
```

```
<실행 결과>
1
2
3
4
5
에러회피
에러회피
에러회피
에러회피
에러회피
에러회피
```

<br>

```java
package com.bit.day12;

public class Ex08 {

	public static void main(String[] args) {
		int[] arr={1,2,3,4,5};
		try{
			for(int i=0; i<=10; i++){
				System.out.println(arr[i]);
			}
		}catch(ArrayIndexOutOfBoundsException e){ // 반복문을 벗어남
			System.out.println("에러회피");
		}
	}
}
```

```
<실행 결과>
1
2
3
4
5
에러회피
```

<br>

### 예외처리를 이용한 프로그래밍

```java
package com.bit.day12;

public class Ex09 {

	public static void main(String[] args) {
		int[] lotto = new int[6];
		int cnt=0;
		try{
			while(true){
				lotto[cnt++]=(int)(Math.random()*45)+1;
			}
		}catch(ArrayIndexOutOfBoundsException e){ //무한반복문이지만 에러-Exception 발생하면 빠져나감
		}
		for(int i=0; i<lotto.length; i++){
			System.out.println(lotto[i]);
		}
	} // main end
} // class end
```

```
<실행 결과>
24
13
9
5
28
20
```

