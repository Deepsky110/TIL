# 인터페이스

```java
package com.bit.day14;

interface Inter01 {
	// 오직 추상메서드만을 갖는다
	// 객체 생성이 불가능(?)하고 따라서 생성자와 필드도 없다.
	// 예외) public static final 변수만 가능
	// 예외) 메서드 앞에 public abstract 생략 가능

	public static final int su1 = 1111;
	static final int su2 = 2222;
	final int su3 = 3333;
	int su4 = 4444;

	public abstract void func01();

	public void func02(); // abstract 생략가능 - 어차피 추상메서드니까

	void func03(); // default(x), public(o) 퍼블릭 생략 가능
	// private void func03(); // 상속을 통해 접근해야해서 접근제한자 private 불가
}

interface Inter02{}
interface Inter03{}
// {} 왜 비워둘까?
// 클래스에 대한 정보 보충
// 분류, 제약

public class Ex04 extends Object implements Inter01, Inter02{ //extends Object 생략
	// class는 다중상속 불가능하지만 인터페이스는 가능

	public static void main(String[] args) {
		Inter01 me = new Ex04();
		me.func01();
		me.func02();
		me.func03();
		System.out.println(Inter01.su1);
		System.out.println(Inter01.su2);
		System.out.println(Inter01.su3);
		System.out.println(Inter01.su4);
	}

	@Override
	public void func01() {
		// TODO Auto-generated method stub

	}

	@Override
	public void func02() {
		// TODO Auto-generated method stub200525 추상클래스, 메서드

	}

	@Override
	public void func03() {
		// TODO Auto-generated method stub

	}

}
```

```
<실행 결과>
1111
2222
3333
4444
```



<br>

```java
package com.bit.day14;

interface Inter05 extends Inter04, Inter03{ // 인터페이스와 인터페이스 끼리의 상속은 implements가 아닌 extends
	// 클래스의 네이밍 규칙과 동일
	void func02();
//	void func01(); // Inter04에서 이미 void로 지정해놓음
//	int func01(int a); 인자값을 다르게 해서는 가능
}

public class Ex05 implements Inter05{

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}

	@Override
	public void func02() {
		// TODO Auto-generated method stub
		
	}

	@Override
	public void func01() {
		// TODO Auto-generated method stub
		
	}

}
```

```java
(Inter 04 조상클래스)
package com.bit.day14;

public interface Inter04 { // 외부에 만들면 인터페이스도 public으로 만들 수 있다
	int su = 1234; // public static final 생략

	void func01(); // public abstract 생략

}
```



<br>

```java
package com.bit.day14;

interface Remote {
	void on();
	void off();
	void work();
}

class Tv2 implements Remote {
	@Override
	public void on() {
		System.out.println("전원을 공급한다");
	}

	@Override
	public void off() {
		System.out.println("전원을 차단한다");
	}

	@Override
	public void work() {
		System.out.println("화면을 띄운다");
	}
}

class Radio2 implements Remote {

	@Override
	public void on() {
		System.out.println("배터리를 통해 전원을 공급한다");
	}

	@Override
	public void off() {
		System.out.println("배터리 전원 공급을 차단한다");
	}

	@Override
	public void work() {
		System.out.println("주파수를 찾아 소리를 출력한다");
	}

}

public class Ex06 {

	public static void main(String[] args) {

		Remote remote = null; // 객체를 생성
		remote = new Tv2();
		remote.on();
		remote.work();
		remote.off();
		remote = new Radio2();
		remote.on();
		remote.work();
		remote.off();
	}

}
```

```
<실행 결과>
전원을 공급한다
화면을 띄운다
전원을 차단한다
배터리를 통해 전원을 공급한다
주파수를 찾아 소리를 출력한다
배터리 전원 공급을 차단한다
```
