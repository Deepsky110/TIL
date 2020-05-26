# Util - 날짜

```java
package com.bit.day14;

import java.util.Calendar;

public class Ex07 {

	public static void main(String[] args) {
									//new java.util.Calendar();
		java.util.Calendar cal = java.util.Calendar.getInstance();
//		System.out.println(cal.toString());

		System.out.println(cal.get(1));
		System.out.print(cal.get(Calendar.YEAR)+"년");
		System.out.print(1+cal.get(Calendar.MONTH)+"월"); // 0~11월 only MONTH!
		System.out.print(cal.get(Calendar.DATE)+"일");
//		System.out.print(cal.get(Calendar.DAY_OF_WEEK)); //1~7 일요일부터
		
		char ch='?';
		switch (cal.get(Calendar.DAY_OF_WEEK)){
		case 1: ch='일'; break;
		case 2: ch='월'; break;
		case 3: ch='화'; break;
		case 4: ch='수'; break;
		case 5: ch='목'; break;
		case 6: ch='금'; break;
		case 7: ch='토'; break;
		
		default:
			break;
		}
		
		System.out.print("("+ch+")");
		System.out.print("\t");
//		System.out.print(cal.get(Calendar.AM)+".");
//		System.out.print(cal.get(Calendar.AM_PM)+".");
		if(cal.get(Calendar.AM)==0){
			System.out.print("a.m.");
			System.out.print(cal.get(Calendar.HOUR)+"시 or ");// 0~11시
		}else if(cal.get(Calendar.AM)==1){
			System.out.print("p.m.");
			System.out.print(cal.get(Calendar.HOUR)+"시 or ");// 0~11시
		}
		System.out.print(cal.get(Calendar.HOUR_OF_DAY)+"시");
		System.out.print(cal.get(Calendar.MINUTE)+"분");
		System.out.println(cal.get(Calendar.SECOND)+"초");
		
		System.out.println(cal.get(Calendar.WEEK_OF_YEAR)+"주차");
		System.out.println(cal.get(Calendar.WEEK_OF_MONTH)+"주차");
		System.out.println(cal.get(Calendar.DAY_OF_YEAR)+"일째");
		
	}

}
```

```
<실행 결과>
2020
2020년5월25일(월)	p.m.8시 or 20시34분40초
22주차
5주차
146일째
```

<br>

```java
package com.bit.day14;

import java.util.Calendar;

public class Ex08 {

	public static void main(String[] args) {

		java.util.GregorianCalendar cal=null;
		cal=new java.util.GregorianCalendar(2020,5-1,25,13,11,30); // 0부터!
		System.out.println(cal.toString());
		System.out.print(cal.get(Calendar.YEAR)+"년");
		System.out.print(1+cal.get(Calendar.MONTH)+"월"); // 0~11월 only MONTH!
		System.out.print(cal.get(Calendar.DATE)+"일");
		System.out.print(cal.get(Calendar.HOUR_OF_DAY)+"시");
		System.out.print(cal.get(Calendar.MINUTE)+"분");
		System.out.println(cal.get(Calendar.SECOND)+"초");
		
	}

}
```

```
<실행 결과>
java.util.GregorianCalendar[time=?,areFieldsSet=false,areAllFieldsSet=false,lenient=true,zone=sun.util.calendar.ZoneInfo[id="Asia/Seoul",offset=32400000,dstSavings=0,useDaylight=false,transitions=30,lastRule=null],firstDayOfWeek=1,minimalDaysInFirstWeek=1,ERA=?,YEAR=2020,MONTH=4,WEEK_OF_YEAR=?,WEEK_OF_MONTH=?,DAY_OF_MONTH=25,DAY_OF_YEAR=?,DAY_OF_WEEK=?,DAY_OF_WEEK_IN_MONTH=?,AM_PM=1,HOUR=1,HOUR_OF_DAY=13,MINUTE=11,SECOND=30,MILLISECOND=?,ZONE_OFFSET=?,DST_OFFSET=?]
2020년5월25일13시11분30초
```

<br>

```java
package com.bit.day14;

import java.util.Date;

public class Ex09 {

	public static void main(String[] args) {

		// for (int i = 0; i < 599999; i++) { // 시간이 변하는 것을 보기 위해서는 계속 생성

		java.util.Date now = new java.util.Date(); // now - 날짜 시간 다 가지고 있다
		System.out.println(now);
		System.out.print(1900 + now.getYear() + "년"); // 객체 생성시 시간으로 고정
		System.out.print(1 + now.getMonth() + "월");
		System.out.print(now.getMonth() + "일");
		System.out.print(now.getHours() + "시");
		System.out.print(now.getMinutes() + "분");
		System.out.println(now.getSeconds() + "초");

		// String msg = "";
		// for (int i = 0; i < 59999; i++) { //now와 now2 사이에 시간차를 두기 위해
		// 		msg += i;
		// }

		java.util.Date now2 = new java.util.Date(); // now - 날짜 시간 다 가지고 있다
		System.out.println(now2);
		System.out.print(1900 + now2.getYear() + "년"); // 객체 생성시 시간으로 고정
		System.out.print(1 + now2.getMonth() + "월");
		System.out.print(now2.getDate() + "일");
		System.out.print(now2.getDay() + "요일"); // 일요일이 '0'		
		System.out.print(now2.getHours() + "시");
		System.out.print(now2.getMinutes() + "분");
		System.out.println(now2.getSeconds() + "초");
		System.out.println("-----------------------------------");
		System.out.println(now.before(now2));
		System.out.println(now.after(now2));
		System.out.println(now2.before(now2));
		System.out.println(now2.after(now2));
		// System.out.println(now2-now);
		java.util.Date now3 = now;
		System.out.println(now.compareTo(now3));
		System.out.println(now.compareTo(now2));
		System.out.println(now2.compareTo(now));
		String msg = "2020/05/24 12:00:00";
		System.out.println(Date.parse(msg)); // 문자열을 날짜정보로 표시
		System.out.println(System.currentTimeMillis());
		System.out.println(now.getTime()); // long타입으로 나옴
		long t = System.currentTimeMillis();
		java.util.Date now4 = new java.util.Date(t);
		System.out.println(now4); // long 타입을 Date 타입으로
		java.util.GregorianCalendar gc = new java.util.GregorianCalendar();
		long t2 = gc.getTimeInMillis();
		java.util.Date now5 = new java.util.Date(t2);
		System.out.println(now5);
		java.util.Calendar cal = java.util.Calendar.getInstance();
		long t3 = cal.getTimeInMillis();
		java.util.Date now6 = new java.util.Date(t3);
		System.out.println(now6);

	}

}
```

```
<실행 결과>
Mon May 25 20:36:21 KST 2020
2020년5월4일20시36분21초
Mon May 25 20:36:21 KST 2020
2020년5월25일1요일20시36분21초
-----------------------------------
true
false
false
false
0
-1
1
1590289200000
1590406581313
1590406581298
Mon May 25 20:36:21 KST 2020
Mon May 25 20:36:21 KST 2020
Mon May 25 20:36:21 KST 2020
```

<br>

```java
package com.bit.day14;

public class Ex10 {

	public static void main(String[] args) {
		java.util.Date now = new java.util.Date();
		System.out.println(now);
		//(i.e., date => text)
		// 추상클래스 new로 객체 생성 불가능
		java.text.DateFormat df = java.text.DateFormat.getDateInstance(java.text.DateFormat.FULL);
		//FULL, LONG, SHORT 원하는 패턴으로 사용
		String msg = df.format(now);
		System.out.println(msg);
		System.out.println("------------------------------------------------");
		
		java.text.SimpleDateFormat sdf = null;
//		sdf = new java.text.SimpleDateFormat("yyyy.MM.dd G 'at' HH:mm:ss z");
		sdf = new java.text.SimpleDateFormat("yy-MM-dd a h:mm"); // 20-05-25 오후 3:07
		msg = sdf.format(now);
		System.out.println(msg);
		
	}

}
```

```
<실행 결과>
Mon May 25 20:36:50 KST 2020
2020년 5월 25일 월요일
------------------------------------------------
20-05-25 오후 8:36
```
