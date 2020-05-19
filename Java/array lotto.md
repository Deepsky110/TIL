# 배열을 이용한 로또 숫자 뽑기

### 방법1
```java
package com.bit.day10;

public class Ex10 {
    public static void main(String[] args){
        // 로또번호생성기
        // 1~45까지 숫자 중 6개
        // 랜점, 중복불가
        // 출력, 오름차순 정렬 출력
        // 보너스번호 1개

        int[] lotto=new int[7]; //7은 배열의 길이
        // 중복검사 후 입력
        // 중복시 재입력
        for(int i=0; i<lotto.length; i++){
            int ran=(int)(Math.random()*45)+1;
            lotto[i]=ran;
            for(int j=0; j<=i-1; j++){ //새로 뽑은 값이랑 기존 뽑았던 값을 비교
                if(lotto[i]==lotto[j]){
                    i--; // 위로 올라가서 다시 검사
                    break; // 중복되는 순간 검사 진행을 멈추고 처음으로
                }
            }
        }
        // 오름차순 정렬(작->큰)
        int temp=0;
        for(int i=0; i<5; i++){
            for(int j=i+1; j<6; j++){ // 같은 값끼리 비교하는 것을 피하기 위해 j=i+1
                if(lotto[i]>lotto[j]){
                    temp=lotto[i];
                    lotto[i]=lotto[j];
                    lotto[j]=temp;
                }
            }
        }
        for(int i=0; i<6; i++){
            System.out.print(lotto[i]+" ");
        }
        System.out.print("\t보너스번호"+lotto[6]);
    }
}
```
<br>

### 방법2

```java
package com.bit.day10;

public class Ex11 {
    public static void main(String[] args){
        int[] ball = new int[45];
        for(int i=0; i<45; i++){
            ball[i]=i+1;
        }
        int temp=0;
        for(int i=0; i<100000; i++){
            temp=ball[0];
            int ran=(int)(Math.random()*44)+1;
            ball[0]=ball[ran];
            ball[ran]=temp;
        }
        for(int i=0; i<6; i++){
            System.out.print(ball[i]+" ");
        }
        System.out.print("\t보너스번호:"+ball[6]);
    }
} // 오름차순 정렬은 1번과 같음
```

