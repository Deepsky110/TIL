# 스레드
### 상속을 통한 스레드 만들기
```java
package com.bit.day22;

public class Ex01 extends Thread {
	// 상속을 통한 쓰레드 만들기

	public void run() { // run을 오버라이드 // 메소드명은 run만 가능
		System.out.println("thread start...");
		for (int i = 0; i < 10; i++) {
			System.out.println("thread work...");
		}
		System.out.println("thread end...");
	}

	public static void main(String[] args) {
		System.out.println("main start...");
		Ex01 me = new Ex01(); // 쓰레드 내가 상속해서 내가 쓰레드가 됨
		me.start(); // run메소드를 직접 호출하지 않는다 - 독립적인 스레드를 통해 동작시키기 위해
//		me.run(); // 새로운 쓰레드가 만들어 지지 않고 순서대로 진행됨
		
		for (int i = 0; i < 5; i++) {
			String temp = new String("test" + i); // 시간을 걸리게 하려고 객체 생성함
			System.out.println("main work...");
		}
		System.out.println("main end...");
	}

}
```

<br>

### 인터페이스 상속으로 스레드 만들기
```java
package com.bit.day22;

public class Ex01 extends Thread {
	// 상속을 통한 쓰레드 만들기

	public void run() { // run을 오버라이드 // 메소드명은 run만 가능
		System.out.println("thread start...");
		for (int i = 0; i < 10; i++) {
			System.out.println("thread work...");
		}
		System.out.println("thread end...");
	}

	public static void main(String[] args) {
		System.out.println("main start...");
		Ex01 me = new Ex01(); // 쓰레드 내가 상속해서 내가 쓰레드가 됨
		me.start(); // run메소드를 직접 호출하지 않는다 - 독립적인 스레드를 통해 동작시키기 위해
//		me.run(); // 새로운 쓰레드가 만들어 지지 않고 순서대로 진행됨
		
		for (int i = 0; i < 5; i++) {
			String temp = new String("test" + i); // 시간을 걸리게 하려고 객체 생성함
			System.out.println("main work...");
		}
		System.out.println("main end...");
	}

} // 출력 결과 me와 you가 섞여서 나옴
```

<br>

### 내부클래스 이용해서 스레드 만들기
```java
package com.bit.day22;

public class Ex03 {
// 내부 클래스 이용 스레드 만들기
	
	
	public static void main(String[] args) {
		
		// 방법 (1)
		Runnable work = new Runnable() {
			public void run() {
				System.out.println("thread1 work...");
			}
		};
		Thread thr1 = new Thread(work);
		Thread thr2 = new Thread(work);
		
		
		// 방법 (2)
//		class Inner extends Thread { // 로컬 클래스
//			public void run() {
//				System.out.println("thread work...");
//				
//			}
//		}
//		
//		Inner thr1 = new Inner();
//		Inner thr2 = new Inner();
//		thr1.start();
//		thr2.start();
		
		
		// 방법 (3)
//		Thread thr1 = new Thread() { // 익명 클래스
//			public void run() {
//				System.out.println("thread1 work...");
//			}
//		};
//		Thread thr2 = new Thread() {
//			public void run() {
//				System.out.println("thread2 work...");
//			}
//		};
//		thr1.start();
//		thr2.start();
		
	}

}
```

<br>

```java
package com.bit.day22;

public class Ex04 {

	public static void main(String[] args) {
		Thread me = Thread.currentThread();
		System.out.println(me.getName() + " start..."); // main이 static이라 바로
														// getName 사용 불가

		Thread thr = new Thread() {
			public void run() {
				System.out.println(this.getName() + " start..."); // Thread를 상속받아
																// (this.)getName
																// 사용 가능
				for (int i = 'A'; i <= 'Z'; i++) {
					System.out.print((char) i + " ");
				}
				System.out.println("\n" + getName() + " end...");
			}
		};
		thr.start();
		
		System.out.println(me.getName() + " end...");
	}
}
```
```
<실행 결과>
main start...
main end...
Thread-0 start...
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 
Thread-0 end...
```

<br>

### 스레드의 우선순위 할당
```java
package com.bit.day22;

public class Ex05 {
	// 스레드 우선순위 할당
	public static void main(String[] args) {
		Runnable work = new Runnable() {

			@Override
			public void run() {
				Thread me = Thread.currentThread();
				for (int i = 0; i < 50; i++) {
					System.out.println(me.getName() + " work" + i);
				}
				System.out.println(me.getName() + "종료");
			}

		};
		Thread thr1 = new Thread(work, "첫번째");
		Thread thr2 = new Thread(work, "두번째");
		Thread thr3 = new Thread(work, "세번째");

		// setPriority : 우선순위 (1~10), Max 10 / min 1 // 확률을 조정하는 것
		thr1.setPriority(Thread.MIN_PRIORITY); // 1
		thr2.setPriority(Thread.NORM_PRIORITY); // 5
		thr3.setPriority(Thread.MAX_PRIORITY); // 10

		thr1.start();
		thr2.start();
		thr3.start();

	}
}
```

<br>

### 스레드 슬립(sleep) 시키기
```java
package com.bit.day22;

public class Ex06 {

	public static void main(String[] args) { // main도 쓰레드다
		System.out.println("main start...");
		try {
			Thread.sleep(3000); // 3000밀리세컨드 = 3초
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		System.out.println("main end...");

	}

}
```

<br>

### 시계처럼 1초씩 가게 하기
```java
package com.bit.day22;

import java.text.SimpleDateFormat;
import java.util.Date;

public class Ex07 {
	// 1초마다 초 늘어나지만 중간 작업에 걸리는 시간 때문에 정확한 1초가 아님
	public static void main(String[] args) {
		for (int i = 0; i < 10; i++) {
			Date date = new Date(); // 객체 생성
			SimpleDateFormat sdf = new SimpleDateFormat("hh:mm:ss");
			String msg = sdf.format(date);
			System.out.println(msg);
			
			try {
				Thread.sleep(1000); // 1초
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			
		}
	}

}
```

<br>

```java
package com.bit.day22;

public class Ex08 extends Thread {
	// JOIN
	public static void main(String[] args) {
		System.out.println("main start...");
		Ex08 me = new Ex08();
		Ex08 you = new Ex08();
		me.start();
		you.start();
		
		try {
			me.join(); // me가 끝날때까지 대기
//			you.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		
		System.out.println("main end...");
	}

	@Override
	public void run() {
		for (int i = 0; i < 5; i++) {
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			System.out.println(getName() + "work" + i);
		}
	}

}
```
