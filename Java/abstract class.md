# 추상클래스

```java
package com.bit.day14;

abstract class Lec01 {

	public abstract void func01();

}

class Lec11 extends Lec01 {
	// abstract class Lec11 extends Lec01 같은 추상클래스이거나
	public void func01() {
		System.out.println("구현했음"); // 추상클래스를 상속 받아서 구현(오버라이딩)
	}
}

public class Ex01 {
	// 추상클래스(abstract)
	// - 추상메서드를 0개 이상 갖는 클래스
	// - 추상메서드(abstract) : 메서드의 선언(o), 구현(x)

	public static void main(String[] args) {
		// Lec01 lec=new lec01(); //추상클래스는 구현되지 않아서 상속 불가
		// lec.func01();
		Lec01 you = new Lec11(); // 다형성에 따라 Lec01-Lec11
		you.func01();

	}

}
```

<br>

```java
package com.bit.day14;

abstract class Machine { // 추상클래스 - 상속 받으려면 같은 추상클래스가 되던가 오버라이딩 하던가 강제성이 생긴다
	abstract void work();

	void on() {
		System.out.println("환영합니다");
	}

	void off() {
		System.out.println("전원을 종료합니다");
	}
}

class Tv extends Machine {
	void work() {
		System.out.println("화면과 소리를 재생한다");
	}
}

class Radio extends Machine {
	void work() {
		System.out.println("주파수를 잡아 소리를 들려준다");
	}
}

class Audio extends Machine {

	@Override
	void work() {
		System.out.println("음악을 들려줍니다"); // 추상클래스를 상속 받을때 오버라이드 하지 않으면 에러
	}
}

public class Ex02 {

	public static void main(String[] args) {
		java.util.Scanner sc = new java.util.Scanner(System.in);

		Machine remote = null;
		while (true) {
			System.out.print("1.Tv 2.Radio 3.Audio 0.종료 >> ");
			int input = sc.nextInt();
			if (input == 0) {
				break;
			} else if (input == 1) {
				remote = new Tv();
			} else if (input == 2) {
				remote = new Radio();
			} else if (input == 3) {
				remote = new Audio();
			}
			
			remote.on();
			remote.work();
			remote.off();

		}

	}

}
```
```
<실행 결과>
1.Tv 2.Radio 3.Audio 0.종료 >> 1
환영합니다
화면과 소리를 재생한다
전원을 종료합니다
1.Tv 2.Radio 3.Audio 0.종료 >>
```
<br>

```java
package com.bit.day14;

abstract class Lec03 {
	
	Lec03(){
		super(); // 숨어있는 키워드
		System.out.println("조상객체 생성");
	}
	
	void func01() {
		System.out.println("구현된 정상적인 메서드 입니다");
	}
	
	abstract void func02();
	
}

class Lec33 extends Lec03{
	Lec33(){
		super(); // 숨어있는 키워드
		System.out.println("자손객체 생성");
	}

	@Override
	void func02() {
		System.out.println("자손에서 func02 구현...");
		
	}
}

class Ex03 {

	public static void main(String[] args) {
		Lec03 you = new Lec33();
		you.func01();
		you.func02();

	}

}
```
```
<실행 결과>
조상객체 생성
자손객체 생성
구현된 정상적인 메서드 입니다
자손에서 func02 구현...
```
