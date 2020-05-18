```java
package com.bit.day09;

class Ex01{
	// 메서드 (객체의 기능 표현)
		// static : 클래스 메서드(전역)
		// non-static : 인스턴스 메서드
	// 변수 (객체의 속성 표현)
		// static : 정적, 전역
		// non-static : 멤버필드
	int su=1234;
	static int su2=4321;

	// 생성자
	// 생성자의 이름 == 클래스명(바꿀 수 없다)
	// 클래스명(인자...){}
	// default 생성자의 클래스명(){} - 인자 생략
	// default 생성자의 경우는 다른 생성자가 존재하지 않을 시 생략 가능
	// public Ex01(){}
	public Ex01(){
		System.out.println("객체를 생성합니다");
		return; // 리턴은 존재하나 그 값이 없다
	}

	public static void main(String[] args){

		//변수의 선언
		Ex01 me;
		//변수의 초기화
		me = new Ex01(); // 객체를 찍어내 객체의 주소값을 me에 준다
		System.out.println("su="+me.su);
	}

	public static void func01(){
		System.out.println("static method func01()");
	}
	public void func02(){
		System.out.println("non-static method func02()");
	}

}
```

<br>

```java
package com.bit.day09;

class Ex02{ // 클래스는 public이나 default만 가능
    // 접근제한자
    // public > default > private
    // public - 어디서나 접근 허용
    // defualt - 동일 패키지에서만 접근 허용
    // private - 동일 클래스 내부에서만 접근 허용
    private int su;

    private Ex02(){}
    private void func01(){}

    private static void main(String[] args){
        Ex01.func01();
        //System.out.println(com.bit.day08.Ex01.a);
        //Math you=new Math(); // static, private으로 만들어짐, 외부에서 객체 생성 불가능
    }
}
```

<br>

```java
package com.bit.day09;

public class Ex03 {

        // default생성자는 접근제한자가 public이다!
        final static int su2=333;
        final int su;
        Ex03(int a){
            // 객체는 생성됐음
            // 객체 생성 시점에 하고 싶은 일을 처리한다
            // 해당 생성자의 호출은 객체 생성시 단 한번만 이루어짐
            /////////////////////////////////////////////////////
            // 필드의 초기화
            su = a;

    }

    public static void main(String[] args){
        // 상수형 변수
        // 이름은 대문자로만 작성한다
        final int a;
        a=1111; // 변수의 초기화
        //a=2222; // 변수 대입, 파이널은 고정이라 변경 불가

        final double PI=3.14;


        Ex03 me=new Ex03(1111);
        Ex03 you=new Ex03(2222);
        System.out.println(me.su);
        System.out.println(you.su);
    }
    
}
```

<br>

```java
package com.bit.day09;

    class Car{
        private String model; // 다른 클래스에서의 접근을 제한. 차 이름을 못 바꾸게 설정함.
        private int limit=150;
        private int speed=0;
        private int accel=5;

        Car(){
            model="승용차";
            limit=150;
            accel=10;
        }

        Car(String name, int a, int b){ //생성자를 통해 강제성을 부여했다.
            model=name;
            limit=a;
            accel=b;
        }
        void speedUp(){
            if((speed+=accel)>limit){speed=limit;}
        }
        void speedDown(){
            if((speed-=accel)<0){speed=0;}
        }
        void show(){
            System.out.println(model+"이(가) "+speed+"km로 달린다.");
        }

    }
public class Ex04 {
    public static void main(String[] args){
        Car car = new Car();
        car.show();
        for(int i=0; i<40; i++){
            car.speedUp();
            car.show();
        }
        for(int i=0; i<40; i++){
            car.speedDown();
            car.show();
        }
        car = new Car("셀토스", 180, 15);
        for(int i=0; i<40; i++){
            car.speedUp();
            car.show();
        }
        for(int i=0; i<40; i++){
            car.speedDown();
            car.show();
        }
    }
}
```
