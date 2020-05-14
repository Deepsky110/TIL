```
	Q1. A~Z 출력하세요
	Q2. a~z 출력하세요
	Q3. A(a), B(b), C(c), ... Z(z) 출력하세요
			
	다음을 출력하세요
	Q4.	★★★★
		★★★★
		★★★★
	Q5.	1 2 3
		4 5 6
		7 8 9
	Q6.	1 2 3
		2 3 4
		3 4 5
```

```java
<나의 풀이>
class Ex09{

	public static void main(String[] args){
		int i = 'A';

		// Q1. A~Z 출력하세요
		System.out.println("Q1. A~Z를 출력하세요");
		
		while(i<='Z'){
			System.out.print((char)i+" ");
			i++;
			
		}

		// Q2. a~z 출력하세요
		System.out.println("\n\nQ2. a~z를 출력하세요");
		i = 'a';
		while(i<='z'){
			System.out.print((char)i+" ");
			i++;
		}

		// Q3. A(a), B(b), C(c), ... Z(z) 출력하세요
		System.out.println("\n\nQ3. A(a), B(b), C(c), ... Z(z)를 출력하세요");
		i = 'A';
		int li = 'a';
		while(i<='Z'&&li<='z'){
			System.out.print((char)i+"("+(char)li+") ");
			i++;
			li++;
		}

		// Q4.	★★★★
		//	★★★★
		//	★★★★
		System.out.println("\n\nQ4.★★★★ 세줄을 출력하세요");
		for(i=1; i<4; i++){
			for(int u=1; u<5; u++){
				System.out.print("★");
			}
			System.out.println();
		}
		System.out.println();

		// Q5.	1 2 3
		//	4 5 6
		//	7 8 9
		for(i=0; i<9; i+=3){
			for(int u=1; u<4; u++){
				System.out.print(i+u+" ");
			}
			System.out.println();
		}

		System.out.println();

		// Q6.	1 2 3
		//	2 3 4
		//	3 4 5
		for(i=0; i<3; i++){
			for(int u=1; u<4; u++){
				System.out.print(i+u+" ");
			}
			System.out.println();
		}		

	} //main end

} //class end
```
<br>

```java
<다른 풀이>
package com.bit.day07;

class Ex09{

	public static void main(String[] args){
		//Q1. A~Z 출력하세요
		for(int i=0; i<'Z'-'A'+1; i++){
			char tmp=(char)('A'+i);
			System.out.print(tmp +" ");
		}
		System.out.println("\n-----------------------\n");
		
		//Q2. a~z 출력하세요
		for(int i=0; i<'z'-'a'+1; i++){
			char tmp=(char)('a'+i);
			System.out.print(tmp +" ");
		}
		System.out.println("\n-----------------------\n");

		// Q3. A(a), B(b), C(c), ... Z(z) 출력하세요
		for(int i=0; i<'Z'-'A'+1; i++){
			char tmp=(char)('A'+i);
			char tmp2=(char)(tmp+'a'-'A');
			System.out.print(tmp+"("+tmp2+") ");
		}
		System.out.println("\n-----------------------\n");

		// Q4.	★★★★ 4줄 출력	
		for(int i=1; i<21; i++){ // 별 16개, (4번 ★+1번 공백)*4
			if(i%5!=0){
				System.out.print('★');
			}else{
				System.out.println();
			}
		}
		System.out.println("\n-----------------------\n");

		// Q5.	1 2 3
		//		4 5 6
		//		7 8 9
		int su=1;
		for(int i=1; i<13; i++){
			if(i%4!=0){ //4번째 문자 자리를 \n으로 처리
				System.out.print(su++);
				System.out.print(' ');
			}else{
				System.out.println();
			}
		}
		System.out.println("\n-----------------------\n");

		su=1;
		for(int i=0; i<3; i++){
			for(int j=0; j<3; j++){
				System.out.print(su++);
				// System.out.print(su+j+3*i);
				System.out.print(' ');
			}
			System.out.println();
		}

		System.out.println("\n-----------------------\n");

		// Q6.	1 2 3
		//		2 3 4
		//		3 4 5
		int limit = 3; // Q6. 1번 풀이
		for(int i=1; ; i++){
			System.out.print(i);
			System.out.print(' ');
			if(limit==i){
				limit++;
				i-=2;
				System.out.println();
				if(limit==6){break;}
			}
		}		
        
		System.out.println("\n-----------------------\n");
        
		for(int i=0; i<3; i++){ // Q6. 2번 풀이
			for(int j=0; j<3; j++){
				System.out.print(j+1+i);
				System.out.print(' ');
			}
			System.out.println();
		}
	}//main end

}//class end
```

```java
package com.bit.day07;

// Q4.	★★★★
//		★★★★
//		★★★★

class Ex10{

	public static void main(String[] args){
		for(int i=0;i<3;i++){
			for(int j=0;j<4;j++){
				System.out.print('★');
			}
			System.out.println();
		}






//Q6. 	1 2 3
//		2 3 4
//		3 4 5
		for(int i=0; i<3; i++){
			for(int j=0; j<3; j++){
				System.out.print(j+1+i);
				System.out.print(' ');
			}
			System.out.println();
		}

	} //main end

} //class end
```
