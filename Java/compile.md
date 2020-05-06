# 3-1 컴파일(compile) 기법
<br>

우리가 보는 언어를 컴퓨터가 이해할 수 있는 언어로 컴파일 해야 한다.  
사람은 자연어를 사용하지만 컴퓨터는 0, 1로 구성된 기계어를 사용한다.  

javac(java컴파일러)  
cmd에서 javac 실행시켜도 실행이 안 된다.  
왜? 위치가 틀려서 그렇다!  
cd(change diretory)로 bin 안에 있는 javac를 찾아가야 한다.  
매번 하기 힘들기 때문에 path 설정 필요

	c:\javaWorkspace>set path="C:\Program Files\Java\jdk1.8.0_251\bin"

설정 후 javac 실행  
컴파일을 하면 class 확장자를 가진 파일이 생성된다.  
그러나 set path는 임시 설정이라 재부팅하면 원래대로 돌아가있다.  

_"2주간 eclipse 쓰지 않고 노트패드로 진행할 것이다...!"_  

javaWorkspace에 노트패드 생성
```
class Ex01
{
    public static void main(String[] args){
	System.out.println("Hello java world~~");
    }
}
```
생성 후 txt 확장자를 java로 변경한다.  

cmd에서 실행시킨다.  
```
c:\javaWorkspace>javac Ex01.java  
c:\javaWorkspace>java Ex01  
Hello java world~~  
```
**<u>내용을 바꿀 때마다 컴파일을 다시 해줘야 한다.</u>**
