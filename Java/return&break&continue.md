```java
package com.bit.day07;

class Ex06{

	public static int func(int a){
		System.out.println("func run...");
		return func(a);
	}

	public static void main(String[] args){
		// 메서드의 재귀적 활용
		// 함수 - 재귀함수
		func(0);

	}

}
```

```
<실행 결과>
func run...
```

<br>

```java
package com.bit.day07;

class Ex07{

	public void func(){

	}

	public static void main(String[] args){
		Ex07 me;
		me = new Ex07(); //객체 만들기
		System.out.println(me);
		
		Ex01 you;
		you = new Ex01();
		System.out.println(you);

	}

}
```

```
<실행 결과>
C:\javaWorkspace>javac -d . -encoding utf8 .\day07\Ex07.java

C:\javaWorkspace>java com.bit.day07.Ex07
com.bit.day07.Ex07@15db9742 
com.bit.day07.Ex01@6d06d69c // 클래스에 대한 정보가 나온다
```

<br>

```java
package com.bit.day07;

class Ex07{

	public Ex07 func(Ex07 me){
		System.out.println("func run...");
		return me;
	}
    
	public static void main(String[] args){
		Ex07 me;
		me = new Ex07(); //객체 만들기
		me.func(me).func(me).func(me).func(me).func(me);
	}
}
```

```
<실행 결과>
C:\javaWorkspace>javac -d . -encoding utf8 .\day07\Ex07.java

C:\javaWorkspace>java com.bit.day07.Ex07
func run...
func run...
func run...
func run...
func run...
```

<br>

## return과 break

```java
package com.bit.day07;

class Ex08{

	public static void main(String[] args){
		System.out.println("main start...");
		for(int i=0; i<5; i++){
			System.out.println("반복"+(i+1));
			if(i==2){return;} // 리턴을 만나 메소드가 종료되면서 프로그램도 종료
		}
		System.out.println("main end..."); // 출력 안된다
	} //main end

} //class end
```

```java
package com.bit.day07;

class Ex08{

	public static void main(String[] args){
		System.out.println("main start...");
		for(int i=0; i<5; i++){
			System.out.println("반복"+(i+1));
			if(i==2){break;} // 리턴과 다르게 반복문만 빠져나간다
            				// main은 끝까지 실행
		}
		System.out.println("main end...");  // 출력된다
	} //main end

} //class end
```

<br>

```java
package com.bit.day07;

class Ex08{

	public static void main(String[] args){
		System.out.println("main start...");
		for(int i=0; i<5; i++){
         	System.out.print("확인 ");
            if(i>2){continue;} // 조건 만족하면 continue 밑을 실행하지 않고 증감식으로 바로 간다.
			//if(i>2){break;} // 반복문만 빠져나간고 메인 실행
			//if(i>2){return;} // 메소드가 종료되면서 프로그램도 종료
			System.out.println("반복"+(i+1));

		}
		System.out.println("main end..."); // 출력 안된다
	} //main end

} //class end
```

```
<continue로 실행시>
main start...
확인 반복1
확인 반복2
확인 반복3
확인 확인 main end...

<break로 실행시>
main start...
확인 반복1
확인 반복2
확인 반복3
확인 main end...

<return으로 실행시>
main start...
확인 반복1
확인 반복2
확인 반복3
확인
```
