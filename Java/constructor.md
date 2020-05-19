# 생성자
```java
package com.bit.day10;

public class Ex01{
    int su1=1234;

    public void func01(){
        int su1=1111;
        System.out.println("func01 run...");
        this.func02();  // 컴파일 과정에서 this가 자동으로 붙는다
                        // 참조 변수인 me를 대신한다
        System.out.println("su1="+this.su1); //객체 주소값 이용 필드 접근
        System.out.println("su1="+su1); // 지역변수 우선
        //논스태틱끼리 바로 접근 가능했던 이유 : this를 자동으로 생략해줌
    }
    public void func01(Ex01 ex){
        System.out.println("func01(param:me) run...");
        System.out.println(ex==this);
        System.out.println("su1="+ex.su1); // ex 생략해줌
        ex.func02(); // 원래는 이렇게 주소를 정확하게 지정해줘야 한다
    }
    public void func02(){
        System.out.println("fucn02 run...");
    }
    public Ex01 func03(Ex01 me){
        System.out.println("func03 run...");
        return me;
    }
    public Ex01 func04(){
        System.out.println("func04 run...");
        return this;
    }
    public static void main(String[] args){ //스태틱에서 논스티택 접근은 참조변수 객체 통해 가능
        Ex01 me=new Ex01();
        me.func01(me);
        me.func03(me).func03(me).func03(me);
        me.func04().func04().func04();
        // System.out.println(this); static에서는 this 존재 불가. 누군지 알 수 없음
       // this는 객체 자기 자신에 대한 주소값
    }   

}
```

```
객체가 생성되었습니다
com.bit.day10.Ex02@15db9742
com.bit.day10.Ex02@15db9742
su=321
PS C:\javaWorkspace> 
```

<br>

```java
package com.bit.day10;
class Car{
    private String model;
    private int speed;
    private int limit;
    private int accel;
    
    Car(){ // 아래 Car car=new Car() 매개변수 값을 비워도 기본 설정값이 나오게!
        this("티코",100,10);
    }
    Car(String model, int limit, int accel){
        this.model=model;
        this.limit=limit;
        this.accel=accel;
    }
    void speedUp(){
        if ((speed+=accel)>limit){
            speed=limit;
        }
    }
    void speedDown(){
        if((speed-=accel)<0){
            speed=0;
        }
    }
    void show(){
        System.out.println(model+"가(이)"+speed+"km로 달린다.");
    }
}
public class Ex03 {
    public static void main(String[] args){
        Car car=new Car("모닝",120,15);
        
        for(int i=0; i<20; i++){
            car.speedUp();
            car.show();
        }
        for(int i=0; i<20; i++){
            car.speedDown();
            car.show();
        }

    }
    
}
```
