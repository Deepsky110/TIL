```java
package com.bit.day10;

public class Ex04 {
    static String msg2; //String은 클래스 타입 => 참조변수 => default값은 null
    public static void main(String[]args){
        String msg1;
        msg1="문자열";
        String msg3="";
        String msg4=new String(); // 힙 영역에 객체 찍어냄
        char[] ch={'문','자','열'};
        String msg5=new String(ch);
        String msg6=new String("문자열");
        String msg7="문자열";
        System.out.println(msg1==msg7); // 주소가 동일해서 true
                                        // Class-문자열 영역에 미리 문자를 저장해놓고 불러온다.
        System.out.println(msg6==msg7); // 결과는 false '==' 레퍼런스 비교, 주소값 비교=> 같은 객체냐
        String msg8="문자";
        String msg9=msg8+"열"; // 처리 시점에서 힙에 새로운 객체가 나오게 된다
        String msg10="문자"+"열"; //원칙적으로는 새로운 객체인데 문자 상수들 끼리의 연산은
                                 //미리 처리하고 클래스 문자열 영역에 올림
        System.out.println(msg7==msg9); //flase
        System.out.println(msg7==msg10); //true

        //번외-유니코드
        byte[] by={65,66,67,68};
        String msg11=new String(by);
        System.out.println(msg11); // ABCD

        byte[] by2=new byte[128];
        for(int i=0; i<by2.length; i++){
            by2[i]=(byte)i;
        }
        String msg12=new String(by2);
        System.out.println(msg12);

    }
    
}
```

```
<실행 결과>
true
false
false
true
ABCD
 
123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijklmnopqrstuvwxyz{|
}~
```



<br>

```java
package com.bit.day10;

public class Ex05 {

    public static void main(String[] args){
        String msg1="java";
        String msg2="Framework";
        String msg3=msg1+msg2;
        String msg4=msg1.concat(msg2); //msg1 참조변수를 통해 concat 메서드 호출
        System.out.println(msg4);
        System.out.println("----------------------");
        
        String msg5="ja"+"va";
        String msg6="ja".concat("va"); // ja 참조변수를 통해 concat호출 (합치기)
        System.out.println(msg1==msg5); //true
        System.out.println(msg1==msg6); //flase
        System.out.println("----------------------");
        
        String msg7="ABCD EFG";
        System.out.println(msg7.length()); //String에서 length()는 메서드다
        for(int i=0; i<msg7.length(); i++){
            System.out.println(msg7.charAt(i));
        }
        System.out.println("----------------------");
        System.out.println(msg7.charAt(0));
        System.out.println(msg7.charAt(4));
        System.out.println(msg7.charAt(1));
        System.out.println("----------------------");

        char[] ch1={'A','B','C','D'}; //char배열 활용해 문자열 만들기
        String msg8=new String(ch1);
        System.out.println(msg8);
        char[] ch2=msg8.toCharArray(); //문자열을 활용해 char배열을 만들기
        for(int i=0; i<ch2.length; i++){
            System.out.println(ch2[i]);
        }
    }
}
```

```
<실행 결과>
javaFramework
----------------------
true
false
----------------------
8
A
B
C
D

E
F
G
----------------------
A

B
----------------------
ABCD
A
B
C
```

