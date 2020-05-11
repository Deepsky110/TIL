```java
class Ex21{
		public static void main(String[] args){
			
			int a=78; //국어
			int b=86; //영어
			int c=45; //수학
			int d=a+b+c; //총점
			double avg=d*100/3/100.0;
			int grade=10-(int)avg/10;

			System.out.println("성적관리 프로그램(ver 0.0.2)");
			System.out.println("------------------------------------");
			System.out.println("국어"+" "+a);
			System.out.println("영어"+" "+b);
			System.out.println("수학"+" "+c);
			System.out.println("------------------------------------");
			System.out.println("합계"+" "+d);
			System.out.println("------------------------------------");
			System.out.println("평균"+" "+avg);
			System.out.println("------------------------------------");

			
			switch(grade){
				case 0: case 1:
			System.out.println("학점"+" "+"A학점");
				break;
				case 2:
			System.out.println("학점"+" "+"B학점");
				break;
				case 3:
			System.out.println("학점"+" "+"C학점");
				break;
				case 4:
			System.out.println("학점"+" "+"D학점");
				break;
				default:
			System.out.println("학점"+" "+"F학점");

			}
		}

}
```
```java
<Ex21 결과>
C:\javaWorkspace>java Ex21
성적관리 프로그램(ver 0.0.2)
------------------------------------
국어 78
영어 86
수학 45
------------------------------------
합계 209
------------------------------------
평균 69.66
------------------------------------
학점 D학점
```

<br>

```java
class Ex22{

		public static void main(String[] args){

			//int su=1234;
			String msg=args[0];
			System.out.println("input>>>"+msg);
			System.out.println("-------------------");
			if(msg=="java"){
				System.out.println("같다");
			}else{
				System.out.println("다르다");
			}
			System.out.println("------------------");
			switch(msg){
				case "java":
				System.out.println("같다");
				break;

				default:
				System.out.println("다르다");

			}
		}
}
```
```java
<Ex22 결과>
C:\javaWorkspace>javac -encoding utf8 Ex22.java

C:\javaWorkspace>java Ex22 java
input>>>java
-------------------
다르다
------------------
같다

C:\javaWorkspace>java Ex22 asd
input>>>asd
-------------------
다르다
------------------
다르다
```
```java
class Ex23{

		public static void main(String[] args){

			// 입력받기 ex)java Ex23 ~~~~ 바로 입력해야함
			//String input1;
			//input1=args[0];
			//System.out.println("result1>"+ input1);

			// 입력 사전 준비
			java.util.Scanner sc
			=new java.util.Scanner(System.in);

			// 입력받기
			System.out.print("문자열입력>"); //한 칸 아래가 아닌 바로 옆에 입력
			String input2=sc.nextLine();
			System.out.println("result2>"+ input2+1);

			System.out.print("숫자입력>");
			int su=sc.nextInt();
			System.out.println("result3>"+ (su+1));
			
			
	}

}
```

```java
class Ex24{

		public static void main(String[] args){
			java.util.Scanner sc=new java.util.Scanner(System.in);
			int kor=0;
			int eng=0;
			int math=0;
			System.out.print("국어>");
			kor=sc.nextInt();
			System.out.print("영어>");
			eng=sc.nextInt();
			System.out.print("수학>");
			math=sc.nextInt();

		String msg="";
		msg+="\n\n\n성적관리 프로그램(ver 0.0.2)";
		msg+="\n-----------------------------------";
		msg+="\n국어 "+kor;
		msg+="\n영어 "+eng;
		msg+="\n수학 "+math;
		msg+="\n-----------------------------------";
		int sum=kor+eng+math;
		msg+="\n합계 "+sum;
		msg+="\n-----------------------------------";
		double avg=sum*100/3/100.0;
		msg+="\n평균 "+avg;
		msg+="\n-----------------------------------";
		char grade='F';
		
		/*
			A 65
			B 66
			C 67
			D 68
			E 69
			F 70
		*/

		int tmp=sum/30;		//(sum/3/10)
		switch(tmp){
			case 10:
			case 9: grade-=1;
			case 8: grade-=1;
			case 7: grade-=1;
			case 6: grade-=2;
			default:
		}
	msg+="\n학점 "+grade+"학점";
	System.out.println(msg);

	}
	

}
```
```java
<Ex24 결과>
C:\javaWorkspace>java Ex24
국어>40
영어>77
수학>68



성적관리 프로그램(ver 0.0.2)
-----------------------------------
국어 40
영어 77
수학 68
-----------------------------------
합계 185
-----------------------------------
평균 61.66
-----------------------------------
학점 D학점
```

```java
class Ex25{

		public static void main(String[] args){

			//제어문(반복문)
			//for반복문

			int su;
			su=100;

			System.out.println("su="+su);
			su++;
			System.out.println("su="+su);
			su++;
			System.out.println("su="+su);
			su++;
			System.out.println("su="+su);
			su++;
			System.out.println("su="+su);

			System.out.println("-----------------");

			/*
				for(초기화;조건문;증감식){
					실행문;
				}
			초기화 > 조건검사(true) > 실행문 > 증감식 > 조건검사 (true)....
			...실행문 > 증감식> 조건검사(false) > out

			*/
			
			for(int i=100;i<105;i++){
				System.out.println("i="+i);

		}

						

	}

}
```

```java
<Ex25 결과>
C:\javaWorkspace>java Ex25
su=100
su=101
su=102
su=103
su=104
-----------------
i=100
i=101
i=102
i=103
i=104
```

```java
class Ex26{

		public static void main(String[] args){
			// 구구단을 출력하시오

			java.util.Scanner sc
			=new java.util.Scanner(System.in);
			System.out.print("몇 단?");
			int a=sc.nextInt();
			for(int i=1; i<=9; i++){
				System.out.println(a+" X "+i+" = "+a*i);

			}
		}

}
```

```java
<Ex26 결과>
C:\javaWorkspace>java Ex26
몇 단?8
8 X 1 = 8
8 X 2 = 16
8 X 3 = 24
8 X 4 = 32
8 X 5 = 40
8 X 6 = 48
8 X 7 = 56
8 X 8 = 64
8 X 9 = 72
```
