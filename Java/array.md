# 배열
```java
package com.bit.day09;

public class Ex05{

    public static void main(String[] args){
        int a1=1;
        int a2=3;
        int a3=5;
        int a4=7;
        int a5=9;

        int[] a;
        // 정적할당 (한번 지정된 개수는 변경 불가)
        // 자료형[] 배열명=new 자료형[개수]; (자료형은 일치해야 한다)
        // 배열명[인덱스번호]
        // 인덱스번호
        // 0부터 자동부여
        // 번호는 연속됨
        // 인덱스번호의 끝은 : 개수-1

        a=new int[5];
        a[0]=2;
        a[1]=4;
        a[2]=6;
        a[3]=8;
        a[4]=10;

        
        int[] b = new int[]{1,3,5,7,9}; // 이렇게 쓰는걸 추천!

        //int[] c = {10,11,12,13,14}; 더 축약된 형태

        for(int i=0; i<5; i++){
            System.out.println(b[i]);
        }    
    }
}
```

## 예제
```java
package com.bit.day09;

public class Ex06 {
    public static void main(String[] args){
        //다음 배열의 값을 +2씩 연산하여 출력하시오
        int[] su1={1,4,6,7,9};
        System.out.println("배열의 길이:"+su1.length);
        for(int i=0; i<su1.length; i++){
            su1[i]+=2;
        }
        for(int i=0; i<su1.length; i++){
            System.out.print(su1[i]+" ");
        }   
        System.out.println("\n----------------------------");

        // 0~10중 홀수를 담는 배열을 생성하고 출력하시오
        int[] su2=new int[5];
        int idx=0;
        for(int i=0; i<11; i++){
            if(i%2==1){su2[idx++]=i;}
        }
        for(int i=0; i<su2.length; i++){
            System.out.print(su2[i]+" ");
        }
        System.out.println("\n----------------------------");

        // 방법2
        int cnt=0;
        for(int i=0; i<11; i++){
            if(i%2==1){cnt++;}
        }
        // 홀수의 개수를 카운트
        int[] su3=new int[cnt]; 
        System.out.println("cnt="+cnt);
        int idxx=0;
        for(int i=0; i<11; i++){
            if(i%2==1){
               su3[idxx++]=i;
            }
        }
        for(int i=0; i<su3.length; i++){
            System.out.print(su3[i]+" ");
        }
        System.out.println("\n----------------------------");

        // 알파벳 대문자를 담는 배열을 만들고 출력하시오
        char[] ch=new char['Z'-'A'+1];
        for(int i=0; i<ch.length; i++){
            ch[i]=(char)('A'+i);
        }
        for(int i=0; i<ch.length; i++){
            System.out.print(ch[i]+" ");
        }
        System.out.println("\n----------------------------");
        // 다음을 오름차순으로 정렬하시오
        int[] su4={7,2,4,8,3};
        int temp=0;
        for(int i=0; i<su4.length-1; i++){
            for(int j=i+1; j<su4.length; j++){
                if(su4[i]>su4[j]){
                    temp=su4[i];
                    su4[i]=su4[j];
                    su4[j]=temp;
                }
            }
        }
        for(int i=0; i<su4.length; i++){
            System.out.print(su4[i]+" ");
        }
    }

}
```

