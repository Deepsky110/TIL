# 연산자

```
class Ex12{

		public static void main(String[] args){
		// 연산자
		// 사칙연산( * / % + - )
		System.out.println((3+2)*3);
		//System.out.println(0/0);
		// 증감연산자(a++, a--, ++a, --a)
		int a;
		a=100;
		a--; // a=a-1 같은 대입연산은 속도가 느리다
		a++; // a--, a++은 처음에는 값 그대로, 다음부터 +1
		++a; // ++a, --a는 처음부터 +1로 시작
		--a;
		System.out.println((a++)+1+(++a)+(a++));
		System.out.println("-----------------------");
		byte b;
		b=126;
		// b=(byte)(b+1) : byte와 int의 연산이라 형변환 필요
		b++; // b=(byte)(b+1)와 같은 표현
		b++;
		System.out.println("b="+b);
		} // main end

} // class end
```
```
C:\javaWorkspace>javac -encoding utf8 Ex12.java

C:\javaWorkspace>java Ex12
15
305
-----------------------
b=-128
```


## 관계연산자와 논리연산자

```
class Ex13{

		public static void main(String[] args){
		//관계연산자 : 사칙연산보다 후순위로 처리
			int su;
			su=5;
			System.out.println(su>3);
			System.out.println(su<3);
			System.out.println(su>=3);
			System.out.println(su<=3);
			System.out.println(su==3); // 같은가?
			// boolean d=su==2; 대입연산자는 가장 후순위로 처리
			System.out.println(su!=3); // ~같지 않은가?
			System.out.println("----------------------------------");
		//논리연산자(&&:and ||:or) boolean type만 사용 가능
			System.out.println(true && true);
			System.out.println(true && false);
			System.out.println(false && true);
			System.out.println(false && false);
			System.out.println(true || true);
			System.out.println(true || false);
			System.out.println(false || true);
			System.out.println(false || false);
			
		}

}
```
```
C:\javaWorkspace>javac -encoding utf8 Ex13.java

C:\javaWorkspace>java Ex13
true
false
true
false
false
true
----------------------------------
true
false
false
false
true
true
true
false
```


## 단항 논리 연산자 & 대입(배정) 연산자
```
class Ex14{

		public static void main(String[] args){
			// 단항 논리 연산자 : "!" 부정한다
			boolean a;
			a=true;

			System.out.println(!a);
			System.out.println(!(3>5));
			// 대입연산자, 배정연산자(=, +=, -=, *=, /=, %=) : 우선순위가 가장 낮다
			byte b;
			b=100;
			
			b+=1; //b=b+1; a++과의 차이점 : b+=2도 가능
			System.out.println(b);

		}

}
```
```
C:\javaWorkspace>javac -encoding utf8 Ex14.java

C:\javaWorkspace>java Ex14
false
true
101
```

## 비트 연산자 & 쉬프트 연산자
- 비트연산자 (&, |) : Java에서 잘 안쓴다.  
- 쉬프트 연산자 (<<, >>)  
	- 정수형데이터에서만 사용가능하고 2진수로 표현했을때 각 자리를 오른쪽 또는 왼쪽으로 이동  
	- 오른쪽으로 n비트 이동하면 피연산자를 2의 n승으로 나눈 것과 같은 결과이다.
	- '<<' 연산자의 경우, 피연산자의 부호에 상관없이 자리를 왼쪽으로 이동시킨다.
	- '>>' 연산자는 음수인 경우 부호를 유지시켜주기 위해서 빈자리를 1로 채운다.
	- '>>>' 연산자는 부호에 상관없이 항상 0으로 빈자리를 채운다.  
<br>

# 제어문
## 1. 조건문
### 1-1. if
```
class Ex15{

		public static void main(String[] args){
		// 제어문
		// 1. 조건문
		// 1-1. if문
		// 만약 ~라면 ~을 해라
		// if(조건){실행문}
		// 조건 result boolean type
			int input;
			input=1000;
			System.out.println("시작");
			if(input%2==1){
				System.out.println("홀수입니다");
			} // if end
			if(input%2==0){
				System.out.println("짝수입니다");
			} // if end	
} // main end
```
<br>

input 값이  
0입니다  
양수이고 홀수입니다  
양수이고 짝수입니다  
음수이고 홀수입니다  
음수이고 짝수입니다  
<br>
해답1)
```
class Ex16{

		public static void main(String[] args){

			int input;
			input=-31;
			System.out.println("시작");
			if(input==0){
				System.out.println("0입니다");
			} // if end
			if(input>0&&input%2==){
				System.out.println("양수이고 홀수입니다");
			} // if end
			if(input>0&&input%2==0){
				System.out.println("양수이고 짝수입니다");
			} // if end
			if(input<0&&input%2==-1){
				System.out.println("음수이고 홀수입니다");
			} // if end
			if(input<0&&input%2==0){
				System.out.println("음수이고 짝수입니다");		
			} // if end
			System.out.println("종료");

		} // main end

} // class end
```
<br>

해답2)

```
class Ex16{

		public static void main(String[] args){
		
			int input;
			input=-31;
			System.out.println("시작");
			if(input==0){
				System.out.println("0입니다");
			} // if end
			if(input!=0){			
				if(input>0){
					System.out.println("양수이고");
					} // if end
					if(input<0){
						System.out.println("음수이고");
					} // if end
					if(input>0&&input%2==0){
						System.out.println("짝수입니다");
					} // if end
					if(input>0&&input%2!=0){
						System.out.println("홀수입니다");		
					} // if end
					System.out.println("종료");
				
			}

		} // main end

} // class end
```
<br>

해답3) else를 이용
```
class Ex17{

		public static void main(String[] args){
			//
			int su;
			su=1;
			if(su==0){
				System.out.println("0입니다");
			}else{
				if(su>0){
					System.out.println("양수이고");
				}else{
					System.out.println("음수이고");
				}
				if(su%2==0){
					System.out.println("짝수입니다");
				}else{
					System.out.println("홀수입니다");
				}
			}

		} // main end

} // class end
```
<br>

### else if
```
class Ex17{

		public static void main(String[] args){
			//
			int su;
			su=3;
			
			if(su==0){
				System.out.println("0입니다");
			}else if(su==1){
				System.out.println("1입니다");
			}else if(su==2){
				System.out.println("2입니다");
			}
			
		} // main end

} // class end
```
결과로 아무것도 출력되지 않는다.  
else if는 조건을 충족하지 않으면 아무것도 출력하지 않는다.  
```
class Ex17{

		public static void main(String[] args){
			//
			int su;
			su=1;
			
			if(su==0){
				System.out.println("0입니다");
			}else if(su<2){
				System.out.println("1입니다");
			}else if(su<3){
				System.out.println("2입니다");
			}else{
				System.out.println("0~2사이가 아닙니다");
			}			

		} // main end

} // class end
```
