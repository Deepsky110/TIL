# notepad를 이용한 Java
```
C:\Users\user>cd C:\javaWorkspace

C:\javaWorkspace>notepad Ex02.java

C:\javaWorkspace>javac
'javac'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는
배치 파일이 아닙니다.

C:\javaWorkspace>path
PATH=C:\Program Files (x86)\Common Files\Oracle\Java\javapath;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\Users\user\AppData\Local\Microsoft\WindowsApps;
```
set path로 경로를 지정하자니 기존 path가 다 사라진다.  
어떻게 해야할까?

### path 설정
```
C:\javaWorkspace>set path=%path%

C:\javaWorkspace>path
PATH=C:\Program Files (x86)\Common Files\Oracle\Java\javapath;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\Users\user\AppData\Local\Microsoft\WindowsApps;

C:\javaWorkspace>set path=C:\Program Files\Java\jdk1.8.0_251\bin;%path%
```
기존 path에 jdk의 bin 경로를 추가해준다.

```
C:\javaWorkspace>javac Ex02.java

C:\javaWorkspace>java Ex02
print test ok?
```
javac로 compile 해주고 실행시켜보면 정상적으로 출력되는 것을 볼 수 있다.  
<br>

# 자료형

**notepad**  

```
class Ex02{
	public static void main(String[] args){
		System.out.println("a");
	}
}
```  
**cmd**

```
C:\javaWorkspace>javac Ex02.java

C:\javaWorkspace>java Ex02
a
```

정상적으로 출력된다.  

"a"를 'a'로 바꿔도 정상적으로 출력.
but 'abc'를 넣으면 compile이 되지 않는다.  
"" 는 문자열,  '' 는 문자 하나만 가능.  
"" 안에는 아무것도 없어도 compile 가능  
'' 안에 아무것도 없으면 compile 오류  

' ' 안에 띄어쓰기만 있어도 문자로 인식한다.  
<br>
### 연산
```
class Ex02{
	public static void main(String[] args){
		System.out.println(3.14+1);
	}
}
```
compile후 실행시켜보면 4.140000000000001가 나온다.  
프로그래밍에서 실수의 연산은 정확하지 않다.  
컴퓨터의 실수의 연산은 **about**이다. 
<br>

```
class Ex02{
	public static void main(String[] args){
		System.out.println('A'+'B');
	}
}
```
문자와 문자를 연산하면 131이라는 숫자가 나온다.  
<br>

```
class Ex02{
	public static void main(String[] args){
		System.out.println("A"+1+2);
	}
}
```
```
class Ex02{
	public static void main(String[] args){
		System.out.println(1+2+"A");
	}
}
```
순서만 달라졌을 뿐인데 그 결과는 A12와 3A로 다르다.  
<br>

```
class Ex02{
	public static void main(String[] args){
		System.out.println('B'-1);
	}
}
```
65라는 결과가 나온다.  
but 'B'-1를 "B"-1로 바꾸면 compile 오류가 발생한다.  
<br>

```
class Ex02{
	public static void main(String[] args){
		System.out.println("ABC"+"abc");
	}
}
```
ABCabc라는 결과값이 나온다.  
문자열끼리의 덧셈은 산수의 덧셈과 다르다. 문자열끼리 이어주는 역할.  
그러므로 문자열끼리의 뺄셈은 쓸 수 없다.  
<br>
***덧셈, 뺄셈, 곱셈과 다르게 나눗셈은 일반적인 개념과 차이가 있다.***  

```
class Ex02{
	public static void main(String[] args){
		System.out.println(5/2);	//2
		System.out.println(4.5/2);	//2.25
	}
}
```
정수와 정수의 나눗셈의 결과는 정수로 나오고  
실수와의 연산값은 실수로 나온다.  

	System.out.println(5%2); 을 사용하면 나머지 연산을 할 수 있다.
<br>

### 변수

```
class Ex02{
	public static void main(String[] args){
		System.out.println(a);	
		
	}
}
```
compile 해보면  

```
C:\javaWorkspace>javac Ex02.java
Ex02.java:3: error: cannot find symbol
                System.out.println(a);
                                   ^
  symbol:   variable a
  location: class Ex02
1 error
```  
***variable a*** 변수 a를 알 수 없다는 오류가 나온다.  
<br>

```
class Ex02{
	public static void main(String[] args){
		int a;		
		a=1234;
		System.out.println(a);	
		
	}
}
```
변수를 선언하고 실행하면  1234라는 값이 나온다.  
<br>
>10진수를 표현할 수 있는 자료형  
>> int, byte, long, short - 자료형을 달리하면 표현할 수 있는 범위가 달라진다.  
