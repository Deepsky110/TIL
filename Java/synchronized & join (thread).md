### Synchronized
```java
package com.bit.day26;

public class Ex06 extends Thread {
	// 스레드의 동기화

	static int sum;
	int begin;
	int end;
	static Object key = new Object();

	public Ex06(int begin, int end) {
		this.begin = begin;
		this.end = end;
		// this.key = key;
	}

	public void sum(int i) { // 동기화 하지 않고 회피하는 방법
		sum += i + 1;
		System.out.println();
	}

	// 방법1(권장) - 블럭 동기화 (문제 되는 특정 부분을 알아야 가능)
	// 숨어있는 this 살려서 확인, 대입연산자가 있는 부분 확인 등
	// public void sum(int i) {
	// int hap = i + 1;
	// synchronized (key) { // 키가 있어야 스레드 작업 가능, 다른 스레드가 멈춰있는 시간 최소화
	// sum = sum + hap;
	// }
	// }

	// 방법2 - 메서드 동기화 (메서드 작업 동안에 다른 메서드를 쓸 수 없다)
	// public static synchronized void sum(int i) {
	// int hap = i + 1;
	// sum = sum + hap;
	// }

	// @오버라이드
	public void run() {
		for (int i = begin; i < end; i++) {
			sum(i);

		}
	}

	public static void main(String[] args) {
		// 스레드
		// 1~10000 까지의 합계를 구하시오
		// 1~5000 까지의 합계를 구하시오
		// 5001~10000 까지의 합계를 구하시오

		int sum = 0;
		for (int i = 0; i < 5000; i++) {
			sum += i + 1;
		}
		for (int i = 5000; i < 10000; i++) {
			sum += i + 1;
		}
		System.out.println("1~10000까지의 합계: " + sum);
		// Object key = new Object();
		// 작업을 스레드 두 개에 나눠서 시킴
		Ex06 me = new Ex06(0, 5000);
		Ex06 you = new Ex06(5000, 10000);
		me.start();
		you.start();
		try {
			me.join();
			you.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		System.out.println("me+you:" + Ex06.sum);

		// 왜 오차가 발생할까? 왜 항상 같은 값이 나오지 않을까?
		// 동기화 문제 때문에
		// 메서드 호출이 끝나기 전에 다음 메서드로 넘어가는 경우 문제

	}

}
```

<br>

### Thread.join()
```java
package com.bit.day26;

public class Ex07 extends Thread {
	Ex07 ex07;

	public void setEx07(Ex07 me) {
		ex07 = me;
	}

	public void run() {
		System.out.println(getName() + " start...");
		if (ex07 != null) { // 필드값이 있으면
			try {
				ex07.join();
			} catch (InterruptedException e) {
				// e.printStackTrace();
			}
		}
		System.out.println(getName() + " end...");
	}

	public static void main(String[] args) {
		System.out.println("main start...");
		Ex07 me = new Ex07();
		Ex07 you = new Ex07();
		
		me.setEx07(you);
		you.setEx07(me); // join을 걸면 상대가 끝나기를 기다림
		me.start();
		you.start();
		try {
			Thread.sleep(1000); // 1초 기준 스레드 전환
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		me.interrupt(); // 슬립 깨우기
		System.out.println("main end...");

	}

}
```

