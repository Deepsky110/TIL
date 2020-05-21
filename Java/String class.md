# String 클래스



```java
package com.bit.day12;

public class Ex13 {

	public static void main(String[] args) {
		// String class
		String msg1="java";
		String msg2="Web";
		String msg3=msg1.concat(msg2); // + 같은 역할
		System.out.println(msg3); // javaWeb
		
		String msg4="JavaWebSpring";
		
		String msg5=msg4.substring(4); // 4번 자리~ WebSpring 특정 위치에서 문자를 뽑아냄
		String msg6=msg4.substring(4,7); // 4~7번 자리 Web (앞은 포함 뒤는 포함하지 않음)
		String msg7=msg4.substring(0,4); // 0~4번 자리 Java
		String msg8=msg4.substring(4,msg4.length()); // msg4.length = 13 // WebSpring 출력
		
		String msg9=msg4.replace("Web", "DB"); // 전자를 후자로 교체함 // JavaDBSpring 출력
		String msg10=msg4.replace("Web", "");
		String msg11=msg4.replace('W', 'w');
		String msg12=msg4.replace("Java", "");
		
		char ch=msg4.charAt(0); // 인덱스에 해당하는 문자를 찾아냄 // 0번 자리 J를 찾아냄
		int idx=msg4.indexOf('W'); // 문자에 해당하는 인덱스를 찾아냄
		idx=msg4.indexOf("Web"); // 시작 지점의 인덱스를 찾아냄
		idx=msg4.indexOf("a"); // JavaWebSpring에 a가 2개면 앞에 있는 a의 인덱스를 찾는다
		idx=msg4.indexOf("a",2); // 2번 이후 인덱스부터 다시 a를 찾는다
		
		String msg13=msg4.substring(0,msg4.indexOf("Web")); // 0~Web시작 인덱스 전까지 = Java
		String msg14=msg4.substring(msg4.indexOf("Web")+"Web".length());
		String msg15=msg4.replace("a", "A"); //JAvAWebSpring - a가 2개가 모두 바뀐다.
        	// Ja,va로 묶어서 바꾸자
		
		System.out.println(msg13+"DB"+msg14);
		
	}
}
```

```java
package com.bit.day12;

public class Ex14 {

	public static void main(String[] args) {
		String msg = "JavaWebFramework"; 	// 16자리
		String msg2="	java	";
		int su=msg.indexOf("web");  // 있으면 인덱스 번호, 없으면 -1 (boolean-contains 비슷함)
		String st1=msg.replace('z', 'Z'); // 없는 것을 바꾸더라도 에러x, 아무일도 일어나지 않음
		char ch=msg.charAt(0);  // 0~범위까지 인덱스 범위를 넘어가면
        				// StringIndexOutOfBoundsException 에러
		boolean boo1=msg.contains("Web"); // 해당 문자를 포함되어있는가? (true/false)
		boolean boo2=msg.startsWith("Ja");	// 해당 문자로 시작하는가? (true/false)
		boolean boo3=msg.endsWith("Work");	// 해당 문자로 끝나는가? (true/false) // 대소문자 구별

		String st2=msg.toLowerCase();	// 문자를 전부 소문자로 교체
		String st3=msg.toUpperCase();	// 전부 대문자로
		
//		int lnag=msg2.length(); // 길이가 0인가? => 비어있는가? 
		boolean boo4=msg2.isEmpty();	//비어있는가? //null의 경우 객체가 없는 것으로 오류 발생
		String st4=msg2.trim();	// 앞뒤의 공백을 제거해준다(글자 사이 공백x) "java"
		
		System.out.println(msg2);	// "	java	"
		System.out.println(st4);	// "Java"
	}

}
```

```java
package com.bit.day12;

public class Ex15 {

	public static void main(String[] args) {
		String msg1="abcd";
		String msg2="abcd";
		String msg3="abc";
		String msg4="abcaddadwab";
		
		System.out.println(msg1.compareTo(msg2));	// 0
        	// 같으면 0 같지 않으면 이격을 표현 => 연산 시작
		System.out.println(msg1.compareTo(msg3));	// 1
        	//'abcd'->'abcd'aacdd 문자는 차이가 없고 길이에서 부터 달라지기 시작하면 길이 차이를 return
		System.out.println(msg1.compareTo(msg4));	// 3
        	// abc'd'->'abc'a'dacc 서로 다른 값의 차이를 먼저 (아스키)연산해서 return	
	}
}
```

```java
package com.bit.day12;

public class Ex16 {

	public static void main(String[] args) {
		String msg="java DB web framework";
		
		String[] arr=msg.split(" ");	// "" 사이의 문자를 기준으로 나눈다
					// 하나의 문자열이 여러개의 데이터로 나눠진다
		
		for(int i=0; i<arr.length; i++){
			System.out.println(arr[i]);
			System.out.println();
		}
	}
}
```
