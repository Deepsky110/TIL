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
