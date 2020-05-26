# Util

## Random

```java
package com.bit.day14;

public class Ex13 {

	public static void main(String[] args) {
		java.util.Random ran = new java.util.Random();
		System.out.println(Integer.MIN_VALUE + "~" + Integer.MAX_VALUE);
		System.out.println(ran.nextInt());
		System.out.println(ran.nextDouble());
		System.out.println(ran.nextInt(3)); // 0,1,2 // (0<=random<1)*3
//		System.out.println(ran.nextInt(45)+1); // 1~45까지 숫자중 랜덤
	}

}
```

```
<실행 결과>
-2147483648~2147483647
-1128854169 <== 랜덤값
0.779519682592122 <== 랜덤값
2 <== 랜덤값
```

<br>

## Scanner

```java
package com.bit.day14;

public class Ex14 {

	public static void main(String[] args) {
		java.io.InputStream inn = System.in;
		
		String msg = "java\nweb\nframework";
		
		java.util.Scanner sc = null;
		sc = new java.util.Scanner(msg);
		System.out.println(sc.nextLine()); // java // 라인 단위로 읽어준다
		System.out.println(sc.nextLine()); // web
		System.out.println(sc.nextLine()); // framework
		System.out.println(sc.nextLine()); // 더이상 나올게 없어서 에러
//		System.out.println(sc.next()); // 한 단어씩 스캔
		
//		Scanner는 io를 쉽게 쓰기 위한 util이다
	}

}
```

```
<실행 결과>
java
web
framework
Exception in thread "main" java.util.NoSuchElementException: No line found
	at java.util.Scanner.nextLine(Scanner.java:1540)
	at com.bit.day14.Ex14.main(Ex14.java:15)
```

<br>

## Array

```java
package com.bit.day14;

public class Ex15 {

	public static void main(String[] args) {
		int[] arr1 = { 1, 3, 5, 7 }; // 배열

		System.out.println(arr1); // 배열의 주소를 출력하라
//		System.out.println(arr1.toString()); 이거랑 다른 것이다
		System.out.println(java.util.Arrays.toString(arr1)); // 배열을 출력하라
		
		// 배열의 복사
		// 방법1
//		int[] arr2 = new int[arr1.length];
//		for(int i = 0; i < arr1.length; i++){
//			arr2[i] = arr1[i];
//		}
		
		int[] arr2 = new int[2];
		for(int i = 0; i < arr2.length; i++){
			arr2[i] = arr1[i+1];
		}
		System.out.println(java.util.Arrays.toString(arr2)); // 3, 5
		
				
		// 방법2
//		int[] arr3 = new int[arr1.length];
//		System.arraycopy(arr1, 0, arr3, 0, arr1.length);
		
		int[] arr3 = new int[2];
		System.arraycopy(arr1, 1, arr3, 0, 2);
		System.out.println(java.util.Arrays.toString(arr3));
		
		// 방법3
//		int[] arr4 = java.util.Arrays.copyOf(arr1, arr1.length); // 시작은 지점 설정 불가
		int[] arr4 = java.util.Arrays.copyOfRange(arr1, 1, 3); // 앞 포함 뒤 안포함
		System.out.println(java.util.Arrays.toString(arr4));
		
		int[] rans = {41, 2, 23, 10, 11, 28};
		java.util.Arrays.sort(rans);
		System.out.println(java.util.Arrays.toString(rans));
		System.out.println(java.util.Arrays.binarySearch(rans, 28)); // (sort 필수)입력값을 찾아준다
		
	}

}
```

```
<실행 결과>
[I@15db9742
[1, 3, 5, 7]
[3, 5]
[3, 5]
[3, 5]
[2, 10, 11, 23, 28, 41]
4
```
