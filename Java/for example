```java
class Ex27{

		public static void main(String[] args){

			//Q1. 1~10까지의 합을 구하시오
			int sum1 = 0;
			for(int i=0; i<=10; i++){
				sum1+=i;
			}
			System.out.println("1~10까지의 합="+sum1);
			System.out.println("\n------------------------------");

			//Q2. 1~10까지의 짝수들의 합을 구하시오
			int sum2 = 0;
			for(int i=1; i<=10; i++){
				if(i%2==0){
					sum2 += i;
					if(i == 10){
						System.out.print(i + " = ");
						break;
					}
					System.out.print(i+"+");
				}
			}
			
			System.out.println("1~10까지의 짝수들의 합 "+sum2);
			
			System.out.println("\n------------------------------");

			
			//Q3. 1+3+5+7+9=25를 출력하시오
			int sum4=0;
			for(int i=1; i<10; i++){
				if(i%2!=0){
				if(i!=1){System.out.print("+");}
				System.out.print(i);
				sum4+=i;
				}
			}
			System.out.println("="+sum4);
			System.out.println("\n------------------------------");
			
			int sum5=0;
			boolean first=false;
			for(int i=1; i<10; i+=2){
			sum5+=i;
			if(first){System.out.print('+');}
			System.out.print(i);
			first=true;
			}
		
			System.out.println("="+sum5);
			System.out.println("\n------------------------------");
			
			//Q4. 1~50까지 3의 배수를 출력하시오
			boolean first2 = false;
			for(int i=1; i<=50; i++){
				if(i%3==0){
					if(first2){
						System.out.print(", ");
					}
					System.out.print(i);
					first2=true;
				}
			}
			System.out.println("\n\n------------------------------");
			boolean first3=false;
			for(int j=3; j<50; j+=3){
				if(first3)
					{System.out.print(", ");
				}
				System.out.print(j);
				first3=true;
			}
			
			System.out.println("\n------------------------------");	

			//Q5. 2의1승, 2의2승, 2의3승, 2의4승, 2의5승을 출력하시오
			// 2의 1승 2=2
			// 2의 2승 4=2*2
			// 2의 3승 8=2*2*2
			// 2의 4승 16=2*2*2*2
			// 2의 5승 32=2*2*2*2*2
			int su=1;
			for(int i=1; i<=5; i++){
				System.out.println("2의"+i+"승 = "+su*2);
				su=su*2;
			}
			System.out.println("\n------------------------------");
			for(int i=1; i<6; i++){
				int sum6=1;
				for(int j=1; j<=i ; j++){
					sum6*=2;
				}
				System.out.println(sum6);


		} 
	}		
			

}
```

```java
<Ex27 결과>
C:\javaWorkspace>javac -encoding utf8 Ex27.java

C:\javaWorkspace>java Ex27
1~10까지의 합=55

------------------------------
2+4+6+8+10 = 1~10까지의 짝수들의 합30

------------------------------
1+3+5+7+9=25

------------------------------
1+3+5+7+9=25

------------------------------
3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48

------------------------------
3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48
------------------------------
2의1승 = 2
2의2승 = 4
2의3승 = 8
2의4승 = 16
2의5승 = 32

------------------------------
2
4
8
16
32
```
