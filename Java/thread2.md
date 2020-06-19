```java
package com.bit.day26;

class Lec08 extends Thread {
	int tot;

	// @Override
	public void run() {
		synchronized (this) {
			for (int i = 0; i < 5; i++) {
				System.out.println(i + "을(를) 더합니다");
				tot += i;
				try {
					Thread.sleep(500);
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
			notify(); // wait상태 스레드 중 무작위 하나를 깨운다(runnable)
//			notifyAll(); // 전부 runnable 상태로 만든다
		}
	}
}

public class Ex08 {

	public static void main(String[] args) {
		Lec08 lec = new Lec08();
		lec.start();
		synchronized (lec) {
			try {
				lec.wait();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			System.out.println("tot:" + lec.tot);
		}
	}

}
```

<br>

```java
package com.bit.day26;

class Lec09 extends Thread {
	int tot;

	@Override
	public void run() {
		System.out.println(getName() + " start...");
		for (int i = 0; i < 5; i++) {
			System.out.println(i + "를 누적합니다");
			tot += i;
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		System.out.println(getName() + " end...");
	}
}

public class Ex09 {
	// getState() 스레드의 상태확인
	// Thread.State.NEW
	// Thread.State.RUNNABLE
	// Thread.State.BLOCKED
	// Thread.State.TIMED_WAITING
	// Thread.State.WAITING
	// Thread.State.TERMINATED

	public static void toggle(Lec09 lec) {
		if (lec.getState() == Thread.State.NEW) {
			lec.start();
		} else if (lec.getState() == Thread.State.RUNNABLE) {
			lec.suspend();
		} else if (lec.getState() == Thread.State.BLOCKED) {
			lec.stop();
		}
	}

	public static void main(String[] args) {
		Lec09 lec = new Lec09();
		lec.start(); // 시작
		try {
			Thread.sleep(2000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		toggle(lec);

		// lec.start(); // 스레드 시작
		//
		// try {
		// Thread.sleep(2000);
		// } catch (InterruptedException e) {
		// e.printStackTrace();
		// }
		
		// lec.suspend(); // 일시정지 (미사용 권장)
		//
		// try {
		// Thread.sleep(2000);
		// } catch (InterruptedException e) {
		// e.printStackTrace();
		// }
		// lec.resume(); // 재개 (미사용 권장)
		//
		// try {
		// Thread.sleep(2000);
		// } catch (InterruptedException e) {
		// e.printStackTrace();
		// }
		// lec.stop(); // 종료
	}

}
```

<br>

```java
package com.bit.day26;

public class Ex10 extends Thread {
	boolean running;
	boolean end = true;
	int cnt;

	@Override
	public void run() {
		while (end) {
			if (running) {
				System.out.println(getName() + " is working...");
			} else {
				// flag가 false가 되면 다른 스레드에게 실행 양보
				Thread.yield();
				// 양보하고 RUNNABLE 상태로 빠짐
			}
		}
	}

	public static void main(String[] args) {
		Ex10 me = new Ex10();
		Ex10 you = new Ex10();
		me.start();
		you.start();

		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		me.running = true;

		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		me.running = false;
		you.running = true;

		try {
			Thread.sleep(1000);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		me.end = false;
		you.end = false;
	}

}
```
