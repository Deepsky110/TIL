```
class Ex18{

		public static void main(String[] args){
/*
다음을 출력하세요
평균 A:90~100 B:80~90미만 C:70~80미만 D:60~70미만 F:60미만

성적관리 프로그램(ver 0.0.1) 
-------------------------------
국어 35
영어 68
수학 70
-------------------------------
총점 0000
-------------------------------
평균 00.00
-------------------------------
학점 B학점

*/

			int a=35;
			int b=68;
			int c=70;
			int d=a+b+c;
			double avg;
			avg=d*100/3/100.0;
						
			System.out.println("성적관리 프로그램(ver 0.0.1)");
			System.out.println("-------------------------------");
			System.out.println("국어"+" "+a);
			System.out.println("영어"+" "+b);
			System.out.println("수학"+" "+c);
			System.out.println("-------------------------------");
			System.out.println("총점"+" "+d);
			System.out.println("-------------------------------");
			System.out.println("평균"+" "+avg);
			System.out.println("-------------------------------");

			if(avg>=90&&avg<100){
				System.out.println("학점"+" "+'A'+"학점");
			}else if(avg<90&&avg>=80){
				System.out.println("학점"+" "+'B'+"학점");
			}else if(avg<80&&avg>=70){
				System.out.println("학점"+" "+'C'+"학점");
			}else if(avg<70&&avg>=60){
				System.out.println("학점"+" "+'D'+"학점");
			}else{
				System.out.println("학점"+" "+'F'+"학점");
			}
		}

}
```
