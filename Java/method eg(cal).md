```
계산기(ver 0.0.1)
---------------------

1번째 >>2
2번째 >>3
1.+ 2.- 3.× 4.÷ >>1
결과:	2+3=5
1.계속 0.종료>>1

1번째 >>4
2번째 >>2
1.+ 2.- 3.× 4.÷ >>4
결과:	4÷2=2
1.계속 0.종료>>1

1번째 >>5
2번째 >>2
1.+ 2.- 3.× 4.÷ >>4
결과:	5÷2=2.5
1.계속 0.종료>>0

감사합니다

```

```java
<1. while 사용>
class Ex08{

	public static void main(String[] args){
		java.util.Scanner sc = new java.util.Scanner(System.in);
		System.out.println("\n\n계산기(ver 0.0.1)");
		System.out.println("----------------------\n\n");
		int su1=0;
		int su2=0;
		int su3=1; // su3=0으로 초기화하면 while문에 바로 false가 나와서 안됨


		while(su3!=0){
			System.out.print("1번째 >>");
			su1=sc.nextInt();
			System.out.print("2번째 >>");
			su2=sc.nextInt();
			System.out.print("1.+ 2.- 3.× 4.÷ >>");
			su3=sc.nextInt();

			int result=0;
			if(su3==1){
				su3='+';
				result=su1+su2;
			System.out.println("결과:"+su1+(char)su3+su2+"="+result);
			}else if(su3==2){
				su3='-';
				result=su1-su2;
			System.out.println("결과:"+su1+(char)su3+su2+"="+result);
			}else if(su3==3){
				su3='×';
				result=su1*su2;
			System.out.println("결과:"+su1+(char)su3+su2+"="+result);
			}else if(su3==4){
				su3='÷';
				if(su1%su2==0){
					result=su1/su2;
					System.out.println("결과:"+su1+(char)su3+su2+"="+result);
					}else{
					System.out.println("결과:"+su1+(char)su3+su2+"="+(su1*1.0/su2));
					}
				}
				System.out.print("1.계속 0.종료 >>");
				su3=sc.nextInt(); // 위에서 사용 끝나서 사용 가능
            	System.out.println("\n감사합니다");
			
		} //while end

	} //main end

} //class end
```


```java
<2. do-while 사용>
class Ex08{

	public static void main(String[] args){
		java.util.Scanner sc = new java.util.Scanner(System.in);
		System.out.println("\n\n계산기(ver 0.0.1)");
		System.out.println("----------------------\n\n");
		int su1=0;
		int su2=0;
		int su3=1; // su3=0으로 초기화하면 while문에 바로 false가 나와서 안됨


		do{
			System.out.print("1번째 >>");
			su1=sc.nextInt();
			System.out.print("2번째 >>");
			su2=sc.nextInt();
			System.out.print("1.+ 2.- 3.× 4.÷ >>");
			su3=sc.nextInt();

			int result=0;
			if(su3==1){
				su3='+';
				result=su1+su2;
			System.out.println("결과:"+su1+(char)su3+su2+"="+result);
			System.out.print("1.계속 0.종료 >>");
			}else if(su3==2){
				su3='-';
				result=su1-su2;
			System.out.println("결과:"+su1+(char)su3+su2+"="+result);
			System.out.print("1.계속 0.종료 >>");
			}else if(su3==3){
				su3='×';
				result=su1*su2;
			System.out.println("결과:"+su1+(char)su3+su2+"="+result);
			System.out.print("1.계속 0.종료 >>");
			}else if(su3==4){
				su3='÷';
				if(su1%su2==0){
				result=su1/su2;
				System.out.println("결과:"+su1+(char)su3+su2+"="+result);
				}else{
				System.out.println("결과:"+su1+(char)su3+su2+"="+(su1*1.0/su2));
			}

		}while(sc.nextInt()!=0);
		System.out.println("\n감사합니다");            

	} //main end

} //class end
```

```java
<3.메서드 사용>
class Ex08{

	public static int func1(int su1, int su2, int su3){
		int result=0;
		if(su3==1){
			result=su1+su2;
		}else if(su3==2){
			result=su1-su2;
		}else if(su3==3){
			result=su1*su2;
		}else if(su3==4){
			result=su1/su2;
		}
		return result;
	} //func1 end

	public static char func2(int su3){
		char result='A';
		if(su3==1){
			result='+';
		}else if(su3==2){
			result='-';
		}else if(su3==3){
			result='×';
		}else if(su3==4){
			result='÷';
		}
		return result;
	} //func2 end
		
	public static int inputPrint(String msg){
		java.util.Scanner sc = new java.util.Scanner(System.in);
		System.out.print(msg);
		int su=sc.nextInt();
		return su;
	
	} //inputPrint end

	public static void main(String[] args){
		java.util.Scanner sc = new java.util.Scanner(System.in);
		System.out.println("\n\n계산기(ver 0.0.1)");
		System.out.println("----------------------\n\n");
		int su1=0;
		int su2=0;
		int su3=1; // su3=0으로 초기화하면 while문에 바로 false가 나와서 안됨

		do{
			
			su1=inputPrint("1번째 >>");
			su2=inputPrint("2번째 >>");
			su3=inputPrint("1.+ 2.- 3.× 4.÷ >>");

			resultPrint(su1,su2,su3);
									
		}while(inputPrint("1.계속 0.종료 >>")!=0); // do-while 조건 검사를 맨 나중에 함
		System.out.println("\n감사합니다");

	} //main end

	public static void resultPrint(int su1, int su2, int su3){
		if(su3==1||su3==2||su3==3||(su3==4&&su1%su2==0)){
			System.out.println("결과:"+su1+func2(su3)+su2+"="+func1(su1,su2,su3));
		}else{ // if(su3==4&&su1%su2!=0))
			System.out.println("결과:"+su1+func2(su3)+su2+"="+(su1*1.0/su2));
		}

	} //resultPrint end

} //class end    
```

