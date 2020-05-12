```java
class Ex30{

		public static void main(String[] args){

			//Q1. 1~50까지의 합을 구하시오
			int su1 = 1;
			int sum1 = 0;
			while(su1 < 51){
				sum1+=su1;
				//System.out.println("su1="+su1);
				su1++;
			}
			System.out.println("1~50까지의 합 = "+sum1);
			System.out.println("-------------------------\n");
		

			//Q2. 1~100까지의 짝수들의 합을 구하시오
			sum1 = 0;
			int su2 = 1;
			while(su2<=100){
				if(su2%2==0){sum1+=su2;}
				su2++;
				//sum1+=su2; (방법2)
				//su2+=2; // 2씩 늘어난다
			}
		
			System.out.println("1~100까지 짝수들의 합 = "+sum1);
			System.out.println("--------------------------\n");



			//Q3. 1+3+5+7+9=25를 출력하시오
			int sum3 = 0;
			int su3 = 1;
			while(su3<10){
				if(su3%2!=0){
					sum3+=su3;
					if(su3!=1){System.out.print('+');}
					System.out.print(su3);
				su3++;
				su3++;
				}
			}
			System.out.println("="+sum3);
			System.out.println("--------------------------\n");

			
			//Q4. 1~50까지 3의 배수를 출력하시오
			int su4 = 1;
			while(su4 < 51){
				if(su4%3==0){
					System.out.print(su4+" ");
				}
				su4++;
			}
			System.out.println("\n------------------------------------\n");
			


			//Q5. 2의1승, 2의2승, 2의3승, 2의4승, 2의5승을 출력하시오
			// 2의 1승 2=2
			// 2의 2승 4=2*2
			// 2의 3승 8=2*2*2
			// 2의 4승 16=2*2*2*2
			// 2의 5승 32=2*2*2*2*2
			
			int sum5=1;
			int su5=1;
			while(su5<6){
				sum5=sum5*2;
				System.out.println("2의"+su5+"승="+sum5);
				su5++;
			}
			System.out.println("---------------------------\n");
			// 2 = 1+1
			// 4 = 2+2
			// 8 = 4+4
			// 16 = 8+8
			// 32 = 16+16
			sum5=0;
			su5=1;
			int cnt=0;
			while(cnt<5){
				sum5=su5+su5;
				System.out.println(sum5);
				su5=sum5;
				cnt++;
			}

	}

}
```

```java
<결과>
C:\javaWorkspace>javac -encoding utf8 Ex30.java

C:\javaWorkspace>java Ex30
1~50까지의 합 = 1275
-------------------------

1~100까지 짝수들의 합 = 2550
--------------------------

1+3+5+7+9=25
--------------------------

3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48
------------------------------------

2의1승=4
2의2승=8
2의3승=16
2의4승=32
2의5승=64
---------------------------

2
4
8
16
32
```

```java
class Ex31{

	public static void main(String[] args){
		int dan=2;
		int su=1;
		while(su<10){
			dan=2;
			while(dan<10){
				System.out.print(dan+"x"+su+"="+(dan*su)+"\t");
				dan++;
			}
		System.out.println();
		su++;

		}
		
	}

}
```

```java
<결과>
2x1=2   3x1=3   4x1=4   5x1=5   6x1=6   7x1=7   8x1=8   9x1=9
2x2=4   3x2=6   4x2=8   5x2=10  6x2=12  7x2=14  8x2=16  9x2=18
2x3=6   3x3=9   4x3=12  5x3=15  6x3=18  7x3=21  8x3=24  9x3=27
2x4=8   3x4=12  4x4=16  5x4=20  6x4=24  7x4=28  8x4=32  9x4=36
2x5=10  3x5=15  4x5=20  5x5=25  6x5=30  7x5=35  8x5=40  9x5=45
2x6=12  3x6=18  4x6=24  5x6=30  6x6=36  7x6=42  8x6=48  9x6=54
2x7=14  3x7=21  4x7=28  5x7=35  6x7=42  7x7=49  8x7=56  9x7=63
2x8=16  3x8=24  4x8=32  5x8=40  6x8=48  7x8=56  8x8=64  9x8=72
2x9=18  3x9=27  4x9=36  5x9=45  6x9=54  7x9=63  8x9=72  9x9=81
```
