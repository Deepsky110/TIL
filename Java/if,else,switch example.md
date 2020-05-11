```java
class Ex19{

		public static void main(String[] args){
			//변수(선언&초기화)
			//자료형, 변수명; // 변수의 선언
			//변수명=초기값; // 변수의 초기화
			int a=4321;	// 동시
			System.out.println("a="+a);
			// 자료형 \uac0000
			// 숫자 (10진수 정수)
			byte su1;
			su1=127;
			short su2;
			su2=127;
			int su3;
			su3=2147483647;
			long su4;
			su4=2147483648L;

			byte su5=1;
			su1=1+2;

			System.out.println("su1="+su1);
			System.out.println("su2="+su2);
			System.out.println("su3="+su3);
			System.out.println("su4="+su4);

			//숫자(실수)
			float su11=3.141235f;
			double su12=3.141235;

			System.out.println("su11="+su11);
			System.out.println("su12="+su12);

			//문자형(char)
			char ch1;
			ch1='A';
			System.out.println("ch1="+(int)ch1);
			System.out.println("65="+(char)65);
			System.out.println("66="+(char)66);
			System.out.println("67="+(char)67);

			String msg;
			msg="문자열";
			System.out.println(msg);

			// 제어문-조건문-if
			// if(조건){실행문;}
			// 조건이 true이라면 실행문 실행
			int su21; // su21값 초기화 필요
			int su22=2;
			if(su22%2==0){
				su21=1234; // su21값 초기화를 if문 안에서 해주면 false의 경우 초기화 불가
			}else{
				su21=4321; // else로 false의 경우 초기화를 해준다. 처음에 미리 초기화 해주는게 좋다.
			}
			System.out.println("su21="+su21);
			int su=1;
			if(su==0){
				System.out.println("0입니다");
			}
			if(su!=0&&su<2){
				System.out.println("1입니다");
			}
			if(su!=0&&su>2&&su<3){
				System.out.println("2입니다");
			}

		}

}
```

```java
C:\javaWorkspace>javac -encoding utf8 Ex19.java

C:\javaWorkspace>java Ex19
a=4321
su1=3
su2=127
su3=2147483647
su4=2147483648
su11=3.141235
su12=3.141235
ch1=65
65=A
66=B
67=C
문자열
su21=1234
1입니다
```

```java
class Ex20{

		public static void main(String[] args){

			//제어문 (조건문)
			// switch문

			/*조건-값 (if는 boolean이 들어가는 것이 차이점)
				switch(조건){
					case 값:
					실행문;
					break;
					...
					case 값:
					실행문;
					break;
					default:
					실행문;
				}
			*/

			int su=1;
			switch(su){
				case 0:
				System.out.println("0입니다");
				break;
				case 1:
				System.out.println("1입니다");
				break;
				case 2:
				System.out.println("2입니다");
				break;
				case 3:
				System.out.println("3입니다");
				break;
				default:
				System.out.println("0~3은 아닙니다");

				
			}


		}

}
```
