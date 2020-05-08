```
class Ex10{

	public static void main(String[] args){
		System.out.println('#');
		System.out.println("문자열");
		System.out.println('문'+'자'+'열');
	}

}
```
```
C:\javaWorkspace>javac -encoding utf8 Ex10.java

C:\javaWorkspace>java Ex10
#
문자열
149692
```
notepad의 한글은 utf-8로 작성되었기 때문에  
compile에도 옵션을 주어야 한다.  
문자 하나하나를 더한다고 문자열이 되는 것이 아니다.  
<br>
```
class Ex10{
//클래스의 선언은 class 클래스명{ 코드;}
// 클래스명 명명규칙
// 첫글자 - 영문대문자
// 띄어쓰기, 특수문자 불가 (예외 _$)
// 단어와 단어 조합은 다음 단어 첫글자를 대문자로 한다.

	public static void main(String[] args){
		System.out.println('#');
		System.out.println("문자열");
		System.out.println('문'+'자'+'열');
		System.out.println("문\t자\n열");
		System.out.println("1.문"+'\t'+'자');
		System.out.println("2.문"+'\u0009'+'자');
		System.out.println("3.문"+(char)9+'자');
		System.out.println("4.문"+'	'+'자');
		System.out.println("1.첫번째문장입니다");
		System.out.println("1.두번째문장입니다");

		System.out.println("2.첫번째문장입니다\n2.두번째문장입니다");

		System.out.println("3.첫문장입니다\n"+
				"3.두번째문장입니다"); // 문장이 길어져 개행을 쓰고 싶다면 엔터가 아니라 \n을 써야한다.
		System.out.println("path=C:\\java\\jdk");	// path=C:\java\jdk
		
		
	}

}
```
```
C:\javaWorkspace>javac -encoding utf8 Ex10.java

C:\javaWorkspace>java Ex10
#
문자열
149692
문      자
열
1.문    자
2.문    자
3.문    자
4.문    자
1.첫번째문장입니다
1.두번째문장입니다
2.첫번째문장입니다
2.두번째문장입니다
3.첫문장입니다
3.두번째문장입니다
path=C:\java\jdk
```
