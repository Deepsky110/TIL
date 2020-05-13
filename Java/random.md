## 랜덤 - 가위바위보 게임
```java
class Ex32{

	public static void main(String[] args){
		// 실수타입
		// 0<=random<1

		System.out.println("랜덤한 숫자를 생성하겠습니다");
		double random = Math.random();

		System.out.println("숫자:"+random);

	} //main end

} //class end
```


```java
/*
가위, 바위, 보 게임
-------------------
1.가위 2.바위 3.보 0.종료>>2
당신 : 바위, 컴퓨터 : 보
당신이 이겼습니다

1.가위 2.바위 3.보 0.종료>>3
당신 : 보, 컴퓨터 : 가위
컴퓨터가 이겼습니다

1.가위 2.바위 3.보 0.종료>>3
당신 : 보, 컴퓨터 : 보
비겼습니다

1.가위 2.바위 3.보 0.종료>>0
전적 1승 1무 1패
게임을 종료합니다
*/
```

```java
<방법1 결과>
class Test3{
	
	public static void main(String[] args){
		java.util.Scanner sc=new java.util.Scanner(System.in);
		System.out.println("\n가위바위보 게임(ver 0.0.1)");
		System.out.println("-----------------------------\n\n");

		int input=1;
		int cnt=0;
		String my="가위";
		String pc="가위";
		String result="비";
		int win=0;
		int lose=0;
		int draw=0;


		while(input!=0){
		// com 0. 가위  1.바위  2.보
		// 정수 0~2

			double random = Math.random();
			// double을 쓰면 0.0 ~ 0.9999999999 결과가 범위로 나온다
			// (int)(random*10) ==> 0 ~ 9
			int com = (int)(Math.random()*10);

			while(com>2){
				com = (int)(Math.random()*10);
			}

	
		System.out.print("1.가위 2.바위 3.보 0.종료 >>>");
			input = sc.nextInt();
			if(input!=0){
				if(input==1){
					my="가위";
					if(com==0){
						pc="가위";
						result="비";
						draw++;
					}else if(com==1){
						pc="바위";
						result="컴퓨터가 이";
						lose++;
					}else if(com==2){
						pc="보";
						result="당신이 이";
						win++;
					}
				}else if(input==2){
					my="바위";
					if(com==0){
						pc="가위";
						result="당신이 이";
						win++;
					}else if(com==1){
						pc="바위";
						result="비";
						draw++;
					}else if(com==2){
						pc="보";
						result="컴퓨터가 이";
						lose++;
					}
		}
		}else if(input==3){
					my="보";
					if(com==0){
						pc="가위";
						result="컴퓨터가 이";
						lose++;
					}else if(com==1){
						pc="바위";
						result="당신이 이";
						win++;
					}else if(com==2){
						pc="보";
						result="비";
						draw++;
					}
				}
		}
		System.out.println("당신 : "+my+" , 컴퓨터 : "+pc);
				System.out.println(result+"겼습니다\n");
				cnt++;
				
			} // if end
			}
		} //out while end
		System.out.println("(전적) 총"+cnt+"게임 중");
		System.out.println(win+"승 "+draw+"무 "+lose+"패");

	} //main end

} //class end
```

```java
<방법2 결과>
class Test4{

	public static void main(String[] args){
		java.util.Scanner sc=new java.util.Scanner(System.in);
		System.out.println("\n가위바위보 게임(ver 0.0.2)");
		System.out.println("------------------------------\n\n");
		int draw=0;
		int loss=0;
		int win=0;
		int input=0;
		int com=0; // 0~2
		boolean boo=true;
		
		while(boo){
			System.out.print("1.가위 2.바위 3.보 0.종료 >>> ");
			input=sc.nextInt()-1;
			String msg="당신:";
			if(input==0){
				msg+="가위";
			}else if(input==1){
				msg+="바위";
			}else if(input==2){
				msg+="보";
			}

			msg+=", 컴퓨터:";
			// com : 0~2
			com = (int)(Math.random()*3);

			if(com==0){
				msg+="가위";
			}else if(com==1){
				msg+="바위";
			}else if(com==2){
				msg+="보";
			}
            
			if(input==-1){
				boo=false; // 강제종료
			}else{
				System.out.println(msg);
				if(input==com){
					System.out.println("비겼습니다");
					draw++;
				}else if((input==0&&com==2)||(input==1&&com==0)||(input==2&&com==1)){
					System.out.println("당신이 이겼습니다");
					win++;
				}else{
					System.out.println("컴퓨터가 이겼습니다");
					loss++;
				}
			}
		}
		System.out.println("(전적)"+win+"승"+draw+"무"+loss+"패");

	} //main end

} //class end
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTc1MDY4NDM5XX0=
-->