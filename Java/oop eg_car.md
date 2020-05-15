### 예제1

```java
package com.bit.day08;

class Car{
    
	String model="";
	int accel=10; //모닝은 accel 값 따로 설정 안해서 10 그대로 들어간다.
	int speed=0;

	public void speedUp(){
		speed+=accel;
	}

	public void speedDown(){
		speed-=accel;
	}
}


class Ex08{

	public static void main(String[] args){
		Car myCar=new Car();
		myCar.model="모닝";
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedUp();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedUp();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedDown();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedDown();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar=new Car();
		myCar.model="K3";
		myCar.accel=15;
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedUp();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedUp();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedDown();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");
		myCar.speedDown();
		System.out.println(myCar.model+" 현재속도:"+myCar.speed+"Km");

	}

}
```

```
모닝 현재속도:0Km
모닝 현재속도:10Km
모닝 현재속도:20Km
모닝 현재속도:10Km
모닝 현재속도:0Km
K3 현재속도:0Km
K3 현재속도:15Km
K3 현재속도:30Km
K3 현재속도:15Km
K3 현재속도:0Km
```

<br>

### 예제2

```java
package com.bit.day08;
// 각 차량마다 속도의 제한이 있다.
// 시속은 음수의 값을 가지지 못한다.


class Car{
    
	String model="";
	int limit=0;
	int accel=0;
	int speed=0;

	public void speedUp(){
		speed+=accel;
		if(speed>limit){speed=limit;}
	}

	public void speedDown(){
		speed-=accel+5;
		if(speed<0){speed=0;}
	}

}


class Ex08{

	public static void main(String[] args){
		Car myCar=null;
		String menu="1.차량선택 2.가속 3.감속 0.종료>>";
		java.util.Scanner sc=null;
		sc=new java.util.Scanner(System.in);
		int input=0;
		while(true){
			System.out.print(menu);
			input=sc.nextInt();
			if(input==0){break;}
			else if(input==1){
				System.out.print("차량을 선택하세요 ");
				System.out.print("1.모닝 2.K3 3.셀토스>>");
				input=sc.nextInt();
				if(input==1){
					myCar=new Car();
					myCar.model="모닝";
					myCar.accel=10;
					myCar.limit=150;
				}else if(input==2){
					myCar=new Car();
					myCar.model="K3";
					myCar.accel=14;
					myCar.limit=180;
				}else if(input==3){
					myCar=new Car();
					myCar.model="셀토스";
					myCar.accel=18;
					myCar.limit=220;
				}
			}
			else if(myCar!=null&&input==2){
				myCar.speedUp();
			}
			else if(myCar!=null&&input==3){
				myCar.speedDown();
			}
			if(myCar!=null){
				System.out.println(myCar.model+" 현재속도는 "+myCar.speed+"km입니다");
			}
		}
	}

}
```
