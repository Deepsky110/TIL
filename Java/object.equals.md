```java
package com.bit.day13;

public class Ex05 {
	// equals 메소드!
	int su;
	int su2;

	Ex05(int su) {
		this.su = su;
	}

	public boolean equals(Object me2) {
		// return true; // 강제로 true 리턴 시킴
		Ex05 me = (Ex05) me2; // me2라는 오브젝트를 Ex05로 캐스팅
		return this.su == me.su; // this는 참조변수를 나타냄
									// su가 value값이 됨
	}

	public static void main(String[] args) {
		Object obj = new Object();
		Object obj2 = obj;
		Object obj3 = new Object();

		System.out.println(obj.toString());
		System.out.println(obj.hashCode());
		System.out.println(obj.equals(obj2));
		System.out.println(obj.equals(obj3));
		System.out.println("--------------------------------");

		// obj.clone(); protected clone라 안된다

		// Ex05 me = new Ex05(11);
		// Ex05 me2 = new Ex05(11);
		// System.out.println(me == me2); // 왜 둘다 래퍼런스 비교를 할까?
		// System.out.println(me.equals(me2)); // value값을 결정해주지 않아서
		//
		// String msg = "java";
		// String msg2 = new String("java");
		// System.out.println(msg == msg2); // == 레퍼런스 비교
		// System.out.println(msg.equals(msg2)); // euqlas 밸류값 비교
		//
		// Integer su1 = new Integer(100);
		// Integer su2 = new Integer(100);
		// System.out.println(su1 == su2);
		// System.out.println(su1.equals(su2));

		// 객체의 비교대상 value를 무엇으로 결정할 것인가?

		try {
			Object me3 = (Ex05) me.clone();
			System.out.println(me == me3);
		} catch (CloneNotSupportedException e) {
			e.printStackTrace();
		}
	}
}
```
