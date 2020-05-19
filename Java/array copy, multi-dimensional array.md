# 배열의 복사



## 배열의 옅은 복사

```java
package com.bit.day10;

public class Ex06 {
    
    public static void main(String[] args){
        int su=1234; //기본자료형
        //System.out.println(su.toString()); 오류 발생
        int[] arr1={1,3,5,7,9}; //int로 만들어진 배열은 가능하다. 객체이고 참조변수이기 때문
        int[] arr2={1,3,5,7,9};
        int[] arr3=new int[]{1,3,5,7,9}; // new int[]는 생략가능
        int[] arr4=arr3; // 배열의 "옅은 복사"
        arr4[2]=10;
        System.out.println(arr1.toString()); //arr1은 객체라 그냥 넣으면 출력이 안된다. 메서드 활용
        System.out.println(arr1==arr2); // false가 나온다. 서로 다른 객체(new int[]...), 다른 주소
        System.out.println(arr3==arr4); // true
        func01(arr3); // 변수의 라이프 사이클이 main의 범위
        for(int i=0; i<arr4.length; i++){
            System.out.println(arr4[i]); // arr4[i]랑 같은 결과-서로 하나의 객체를 가리킨다
        }
    }
    public static void func01(int[] su){
        su[3]=1234; //su의 라이프사이클은 fucn01 내부지만
        //int[] su=arr3; 배열의 "옅은 복사"라서 main에서의 호출에 영향
    }
}
```

```
<실행 결과>
[I@15db9742
false
true
1
3
10
1234
9
```



<br>

## 배열의 깊은 복사

```java
package com.bit.day10;

public class Ex07 {
    
    public static void main(String[] args){
        //int[] arr; // 배열의 선언
        //arr=new int[5]; // 배열의 초기화 // int대신 String이면 default값 null이 나온다
        //for(int i=0; i<arr.length; i++){
        //    System.out.println(arr[i]); // int의 default 값인 0 5개가 나온다
        //}

        int[] arr1=new int[]{2,4,6,8};
        // 배열의 깊은 복사 (주소만 비교하는 레퍼런스 복사가 아닌 밸류값 복사!)
        int[] arr2=new int[arr1.length];
        for(int i=0; i<arr1.length; i++){
            arr2[i]=arr1[i];
        }
        arr1[1]=1234; //이미 변경전의 arr1의 값을 복사한 상태여서 영향이 없다
        for(int i=0; i<arr2.length; i++){
            System.out.println(arr2[i]);
        }
    } 
}
```

```
<실행 결과>
2
4
6
8
```
<br>

# 다중배열

```java
package com.bit.day10;

public class Ex08 {
// 다중배열 :  배열을 갖는 배열
    public static void main(String[] args){ //String[] args는 인자를 배열로 만든것
        System.out.println("몇개:"+args.length);
        for(int i=0; i<args.length; i++){
            System.out.println(args[i]);
        }// String 배열: 실행시점에 띄어쓰기, tab, 개행을 기준으로 문자를 전달
    }
}
```

```
c:\javaWorkspace\day10\target>java com.bit.day10.Ex08
몇개:0

c:\javaWorkspace\day10\target>java com.bit.day10.Ex08 aaa bbb
몇개:2
aaa
bbb

c:\javaWorkspace\day10\target>java com.bit.day10.Ex08 aaa bbb ccc
몇개:3
aaa
bbb
ccc

c:\javaWorkspace\day10\target>java com.bit.day10.Ex08 aaa
몇개:1
aaa
```

<br>

```java
package com.bit.day10;

public class Ex09 {
    public static void main(String[] args){
        int[] arr1=new int[]{1,2};
        int[] arr2=new int[]{3,4,7};
        int[] arr3=new int[]{5,6,8,9};
        int[][] arr4=new int[][]{arr1, arr2, arr3};  //~개의 배열이 ~만큼의 공간을 차지
                                    //미리 객체를 만들 수 없다
        //int[][] arr4=new int[][]{null,null,null}; 
        //int[][] arr4=new int[][]{arr1,arr2,arr3};// int배열을 갖는 배열! 길이가 동적이다!
        //arr4[0][0]=1;
        //arr4[0][1]=2;
        //arr4[1][0]=3;
        //arr4[1][1]=4;
        //arr4[2][0]=5;
        //arr4[2][1]=6;

        System.out.println(arr4.length);
        //System.out.println(arr4[0]);
        //System.out.println(arr4[1]);
        //System.out.println(arr4[2]); //공간은 셋, 셋다 null값이 나온다
        for(int i=0; i<arr4.length; i++){
            for(int j=0; j<arr4[i].length; j++){
                System.out.print(arr4[i][j]+" ");
            }
            System.out.println();
        }
    }  
}
```

```
<실행 결과>
3
1 2
3 4 7
5 6 8 9
```

