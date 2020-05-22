```java
package com.bit.day13;

public class Ex01 {

	public static void main(String[] args) {
		String msg1 = new String("JavaWebFramework");
		StringBuffer sb1 = new StringBuffer("JavaWebFramework");
		//StringBuffer sb2 = ""; //에러 발생 : 모든 문자열은 String으로 타입 불일치
		
		StringBuilder sb3 = new StringBuilder(sb1);
		StringBuffer sb4 = new StringBuffer(10); // 스트링버퍼(int값)은 버퍼의 용량을 의미함
		System.out.println(msg1.length());
		System.out.println(sb1.length());
		
		// [CRUD] Create Read Update Delete
		// 삽입, (보기), 수정, 삭제 등의 문자열 제어
		StringBuffer sb5 = new StringBuffer("Java");
		StringBuffer sb6 = new StringBuffer("Web");
		// StringBuffer sb7 = sb5+sb6; // 불가능하다. String클래스만 가능
		
		StringBuffer sb7 = sb5.append(sb6); // String의 concat과 같은 기능(문자열을 합쳐줌)
		// = sb5.append(sb6); // sb7로 받아줄 필요가 없다. 어차피 sb5 자체에 더해주는 거니까
		
		// String msg2="sb7="+sb7; // sb7=JavaWeb의 나온다 어떻게 가능하냐면 sb7을 String으로 변환해서 연산됨
		System.out.println("StringBuffer sb7="+sb7);
		System.out.println("StringBuffer sb5="+sb5); // StringBuffer는 자기 자신이 변한다
		System.out.println("StringBuffer sb6="+sb6);
		String msg2="java";
		String msg3="web";
		String msg4=msg2+msg3;
		System.out.println("String msg4="+msg4);
		System.out.println("String msg2="+msg2); // String은 연산 결과를 새로운 String으로 만든다
		System.out.println("String msg3="+msg3);
		
		sb5.append("Framework");
		System.out.println(sb5); // JavaWebFramework
		sb5.delete(4, 7);
		System.out.println(sb5); // JavaFramework
		sb5.insert(4, "DB");
		System.out.println(sb5); // JavaDBFramework
		sb5.insert(sb5.length(), "Web");
		System.out.println(sb5); // JavaDBFrameworkWeb
		sb5.replace(4, 5, "Database");
		System.out.println(sb5); // JavaDatabaseBFrameworkWeb
		
	}

}
```

<br>

```java
package com.bit.day13;

public class Ex02 {

	public static void main(String[] args) {
		StringBuffer sb1 = new StringBuffer(); // 버퍼 사이즈 16
		System.out.println("buffer size:" + sb1.capacity());
		StringBuffer sb2 = new StringBuffer(3); // 버퍼 사이즈는 3
		System.out.println("buffer size:" + sb2.capacity());
		for (int i = 0; i < 8; i++) { // 버퍼 사이즈를 초과하는 순간 필요 사이즈의 두 배 만큼 배열 사이즈를 늘린다
			sb2.append(i);
			System.out.println(sb2 + ":" + sb2.capacity());
		}
		for (int i = 0; i < 3; i++) {
			sb2.delete(sb2.length() - 1, sb2.length()); // 문자를 지워도 한 번 증가한 용량은 변하지 않는다 
			System.out.println(sb2 + ":" + sb2.capacity());
		}
		sb2.trimToSize(); // 안쓰는 버퍼 공간을 제거한다, 새로운 배열에 옮기는 것, 자주 쓰지는 말자
		System.out.println(sb2 + ":" + sb2.capacity());
	}

}
```

<br>

```java
package com.bit.day13;

public class Ex03 {

	public static void main(String[] args) {
		StringBuffer sb1 = new StringBuffer();
		System.out.println(sb1.capacity());

		StringBuffer sb2 = new StringBuffer("abc"); // 사이즈 초기값 16에 3개 추가
		System.out.println(sb2.capacity());

	}

}
```

<br>

```java
package com.bit.day13;

public class Ex04 {

	public static void main(String[] args) {
		StringBuffer sb1 = new StringBuffer("abcdefg");
		//sb1.reverse(); //순서 뒤집기
		System.out.println(sb1);

		// char[] dest = new char[sb1.length()]; // void다 (리턴값 없음)
		// sb1.getChars(0, sb1.length(), dest, 0); // StringBuffer에서 배열로 변환하는 메서드
		char[] dest = { '#', '#', '#', '#', '#', '#', '#' };
		sb1.getChars(2, 5, dest, 2);
		// sb1의 2번(시작)~5번전(4번,끝) 문자를 dest 배열의 2번 자리부터 채워라
		for (int i = 0; i < dest.length; i++) {
			System.out.println(dest[i]);

		}

	}

}
```
