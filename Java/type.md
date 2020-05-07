# 3. 자료형
- 자바의 자료형 
	- 기본 자료형
		- 정수형
			- byte
			- short
			- int
			- long
			- char  
      
		- 실수형
			- float
			- double  
      
		- 논리형
			- boolean	 					

```
class Ex02{
	public static void main(String[] args){
		System.out.println('A'-'A');	
		System.out.println('B'-'A');
		System.out.println('C'-'A');
		System.out.println('a'-'A');
	}
}
```
```
C:\javaWorkspace>javac Ex02.java

C:\javaWorkspace>java Ex02
0
1
2
32
```

자바에서는 소문자와 대문자를 구별한다.  
<br> 
# 3-2 정수형

- 문자 정수형 : 하나의 문자를 나타낼 수 있는 char
	- 자바의 문자는 <u>16비트 유니코드</u>로 구성  

```
class Ex02{
	public static void main(String[] args){
		System.out.println('가'-0);	
	}
}
```
결과는 44032(10진수 정수)  
'가'가 어떤 유니코드로 구성되어 있는지 확인할 수 있다.  
<br>

```
class Ex02{
	public static void main(String[] args){
		char ch;
		ch='\uac00';
		System.out.println(ch);
	}
}
```
ac00(16진법)을 집어넣어도 결과는 '가'가 나온다.  
\u는 유니코드 문자표에서 불러오라는 뜻  

***\는 뒤에 오는 문자에 따라 다른 기능을 한다. ([이스케이프 문자](https://en.wikipedia.org/wiki/Escape_character) 참고)***  
***ex) '를 인쇄하고 싶을 때 '''로 쓰는 것이 아니라 '\''로 표기***  

한자 유니코드를 처리했을 때 cmd 상에 '?'로 표기되는 이유  
폰트가 한자를 지원하지 않기 때문이다.  
<br>

```
class Ex03{
	public static void main(String[] args){
		System.out.println("한글출력");
	}

}
```
한글을 출력할 수 없어 compile이 에러가 난다.  
메모장은 UTF-8로 작성되었기 때문에 cmd에서 옵션을 설정해야 한다.  

```
C:\javaWorkspace>javac -encoding utf8 Ex03.java

C:\javaWorkspace>java Ex03
한글출력
```
한글이 정상적으로 출력되는 것을 볼 수 있다.  
<br>
# 3-3 실수형

| **DataType** | **Byte** | **Min** | **Max** |
| ----- | --- | --- | --- |
| **byte** | 1byte |	-128 | 127 |
| **short** | 2byte | -32768 | 32767 |
| **int** | 4byte | -2147483648 | 2147483647 |
| **long** | 8byte | -9223372036854775808 | 9223372036854775807 |
| **float** | 4byte | 1.4E-45 | 3.4028235E38 |
| **double** | 8byte | 4.9E-324 | 1.7976931348623157E308 |  
<br>  

float가 long보다 더 넓은 범위를 나타낸다.  
float는 근사값을 크게 가지기 때문에.  
더 적은 메모리로 더 넓은 범위를 커버하지만 정확도가 떨어진다.  
<br>

# 4 형변환
정수와 실수는 연산이 불가능하다.  
실수를 정수로 바꿔서 연산하면 소수점 이하가 소실된다.  
정수를 실수로 바꿔서 연산해야 한다. -> 형변환

```
class Ex06{

	public static void main(String[] args){
		System.out.println('\uac00');
		System.out.println((int)'\uac00');
		int a;
		a=1234;
		double b;
		b=a; 	// 강제 형변환이 일어나서 a 앞에 (double)을 생략한다.
		System.out.println("b="+b);
	}

}
```
```
C:\javaWorkspace>java Ex06
가
44032
b=1234.0
```
<br>

```
class Ex06{

	public static void main(String[] args){
		int a;
		double b;
		b=3.14;
		a=(int)b;
		System.out.println("a="+a);
	}

}
```
```
C:\javaWorkspace>java Ex06
a=3
```
b=a를 a=b로 바꾸면 강제 형변환이 일어나지 않는다.  
int로 형 변환을 해야만 한다.  

<br>

```
class Ex06{

	public static void main(String[] args){
		char c;
		c='a';
		c=65;
		System.out.println("c="+c);
	}

}
```
```
C:\javaWorkspace>java Ex06
c=A
```

65가 강제 형변환되어 A로 나타난다.  
강제 형변환은 원하지 않는 값이 나올 수도 있다.  
ex) 이진법에서 4와 -4의 값이 같다. 

<br>

```
class Ex07{

	public static void main(String[] args){
		byte a;
		a=127;
		a++;	// a=a+1;
		System.out.println("a="+a);
		int b;
		b=321;
		a=(byte)b;
		System.out.println("a="+a);
	}

}
```
```
C:\javaWorkspace>java Ex07
a=-128
a=65
```
byte는 -128~127까지 표현이 가능하다.  
a가 1씩 증가하다 127을 넘어가는 순간 -값으로 돌아간다.(-128)  
a=b 라고 대입했을 때 321이라는 범위를 표현할 수 없음으로  
b를 byte로 형변환해준다.  
int 321를 byte로 형변환하면 65가 된다.
