

Q1. 주민번호 확인(한글 지원)

주민번호>>000000-0000000

```java
package com.bit.day18;

import java.text.DateFormat;

public class Ex01 {

	public static void main(String[] args) {
		// 주민번호 확인
		java.util.Scanner sc = null;
		sc = new java.util.Scanner(System.in);
		String msg = null;

		char[] origin = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9' };
		char[] target = { '공', '일', '이', '삼', '사', '오', '육', '칠', '팔', '구' };
		int age = 1;
		char gender = '#';
		// 선언부분은 while 밖으로 꺼내줌

		while (true) {
			System.out.print("주민등록번호를 입력하시오 >> ");
			msg = sc.nextLine();
			
			if (msg.length() != 14) { // 입력값의 길이가 14가 아니면
				System.out.println("입력을 다시 확인하세요.");
				continue;
			}
			if(msg.charAt(6) != '-') { // 왜 exception이 발생하지?
				System.out.println("입력을 다시 확인하세요.");
				continue;
			}
			
			// 000사오육 - 일이삼사오육칠
			for (int i = 0; i < msg.length(); i++) { // 입력값의 길이만큼 반복
				if (i == 6) {
					continue;
				}
				if (!Character.isDigit(msg.charAt(i))) {
					// msg에서 i번째 t값이 숫자가 아니면?
					for (int j = 0; j < target.length; j++) {
						if (msg.charAt(i) == target[j]) {
							// target 배열의 문자들과 비교 -일치할 때 j값은?
							String before = msg.substring(0, i);
							// 한글 자리 i 전까지 추출
							String after = msg.substring(i + 1);
							// 한글 발견 i 이후 문자 출력
							msg = before + origin[j] + after;
							// 한글 자리에 해당 숫자 j 넣기
						}// 한 글자씩 문자를 숫자로 바꿔준다 (반복)
					}
				}
			}
			boolean boo = false;
			for(int i = 0; i<msg.length(); i++) {
				if(i == 6) {continue;}
				char temp = msg.charAt(i);
				if(!Character.isDigit(temp)){
//					전 단계에서 한글은 다 숫자로 변경시킴
//					한글도 숫자도 아닌 값이 입력됐을 때는?
					System.out.println("입력을 다시 확인하세요.");
					boo = true;
					break;
				}
			}
			if(boo){continue;}
			// 123456-1234567
			// ('1'-'0')*10 + ('2'-'0'); 숫자의 연속성 // but 한글은 연속성이 없다
			// 000000-0000000 ==> 한글로 입력 받으려면?

			// validation을 통해 확인 작업

			int year = Integer.parseInt(msg.substring(0, 2)); // 정수형으로 변환 연도 추출
			java.util.Date now = new java.util.Date();
			java.text.DateFormat.getInstance();

			DateFormat now2 = java.text.DateFormat.getInstance();
			String result = now2.format(now);
			// System.out.println(result); // e.g. 20.5.29 오전 10:00

			int nowYear = Integer.parseInt(result.substring(0, 2)); // nowYear
																	// 선언
			age = nowYear - year + 1;
			gender = msg.charAt(7); // 6번째 char 값을 뽑다

			if (gender == '1' || gender == '2') {
				age = (2000 + nowYear) - (year + 1900) + 1;
			} else {
				age = (2000 + nowYear) - (year + 2000) + 1;
			}

			if (gender == '1' || gender == '3') {
				gender = '남';
			} else if (gender == '2' || gender == '4') {
				gender = '여';
			}
			break;
		}
		System.out.println("당신은 " + age + "세 " + gender + "성입니다.");

	}
}
```

```java
package com.bit.day18;

import java.text.DateFormat;

public class Ex02 {

	public static void main(String[] args) {
		// 주민번호 확인
		java.util.Scanner sc = null;
		sc = new java.util.Scanner(System.in);
		String msg = null;

		char[] origin = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9' };
		char[] target = { '공', '일', '이', '삼', '사', '오', '육', '칠', '팔', '구' };
		int age = '1';
		char gender = '#';

		while (true) {
			System.out.print("주민등록번호를 입력하시오 >> ");
			msg = sc.nextLine();
			// 000사오육 - 일이삼사오육칠
			System.out.println(msg);
			// 123456-1234567
			// ('1'-'0')*10 + ('2'-'0'); 숫자의 연속성 // but 한글은 연속성이 없다
			// 000000-0000000 ==> 한글로 입력 받으려면?

			// validation을 통해 확인 작업

			int year = 0;
			try {
				year = Integer.parseInt(msg.substring(0, 2)); // 정수형으로 변환 연도 추출
			} catch (NumberFormatException e) {
				// 뽑아낸 문자열이 숫자가 아닐때 발생
				String temp = msg.substring(0, 2); //0,1번째를 추출
				char[] temp2 = new char[2];
				for (int i = 0; i < temp.length(); i++) {
					char ch = temp.charAt(i);
					for (int j = 0; j < target.length; j++) {
						if (target[j] == ch) {
							temp2[i] = origin[j];
						} // 한글을 변환
					}
				}
				try { // 한글이 아니었다면?
					year = Integer.parseInt(new String(temp2));
				} catch (NumberFormatException ex) {
					System.out.println("입력을 다시 확인하세요.");
					continue;
				}
			}
			java.util.Date now = new java.util.Date();
			DateFormat now2 = java.text.DateFormat.getInstance();
			String result = now2.format(now);
			// System.out.println(result); // e.g. 20.5.29 오전 10:00

			int nowYear = Integer.parseInt(result.substring(0, 2));
			age = nowYear - year + 1;
			gender = msg.charAt(7); // 6번째 char 값을 뽑다

			if (gender == '1' || gender == '2' || gender == '일' || gender == '이') {
				age = (2000 + nowYear) - (year + 1900) + 1;
			} else { // 3,4 => 2000년대 출생
				age = (2000 + nowYear) - (year + 2000) + 1;
			}

			if (gender == '1' || gender == '3' || gender == '일' || gender == '삼') {
				gender = '남';
			} else if (gender == '2' || gender == '4' || gender == '이' || gender == '사') {
				gender = '여';
			}
			break;
		}
		System.out.println("당신은 " + age + "세 " + gender + "성입니다.");
	}
}
```

<br>



Q2. 성적관리 프로그램(배열, 동적할당)

배열 사이즈는 고정 

사이즈가 더 커져야하면 신규 배열 만들어서 복사

```java
package com.bit.day18;

import java.util.Arrays;
import java.util.Scanner;

class Student { // 클래스 생성
	int num, kor, eng, math;
}

public class Ex03 {

	public static void main(String[] args) {
		// 학생 성적관리 프로그램 (ver 0.2.0) - 동적할당
		// 학번 국어 영어 수학
		Scanner sc = new Scanner(System.in);
		System.out.println("학생 성적관리 프로그램 (ver 0.2.0)");
		System.out.println("------------------------------------------------");
		Student[] data = new Student[0]; // 초기에 값을 모르니 길이 0
		String input = null;
		while (true) {
			System.out.print("1.보기 2.입력 3.수정 4.삭제 0.종료 >> ");
			input = sc.nextLine();

			if (input.equals("0")) {
				break; // input이 0이면 반복문 탈출
			} else if (input.equals("1")) { // nextLine 문자열로 입력 받아서
				System.out
						.println("------------------------------------------------");
				System.out.println("학번\t국어\t영어\t수학");
				System.out
						.println("------------------------------------------------");
				for (int i = 0; i < data.length; i++) {
					Student stu = data[i]; // Student타입을 갖는 stu 객체 생성
					System.out.print(stu.num);
					System.out.print("\t");
					System.out.print(stu.kor);
					System.out.print("\t");
					System.out.print(stu.eng);
					System.out.print("\t");
					System.out.println(stu.math);
					System.out
							.println("------------------------------------------------");
				}
			} else if (input.equals("2")) {
				Student stu = new Student(); // 학생을 만들자
				System.out.print("학번 >> ");
				stu.num = Integer.parseInt(sc.nextLine());
				System.out.print("국어 >> ");
				stu.kor = Integer.parseInt(sc.nextLine());
				System.out.print("영어 >> ");
				stu.eng = Integer.parseInt(sc.nextLine());
				System.out.print("수학 >> ");
				stu.math = Integer.parseInt(sc.nextLine());

				// Student[] temp = new Student[data.length + 1];
				// 기존에 비해서 한사이즈 큰 배열 선언

				// // 기존
//				for (int i = 0; i < data.length; i++) { // temp에 기존 입력 자료를
//				앞부분부터 복사
//				temp[i] = data[i]; // 방법1
//				}
//				System.arraycopy(data, 0, temp, 0, data.length); // 방법2
//				data = temp; // length를 하나 늘린 temp가 data가 됨
				data = Arrays.copyOf(data, data.length + 1);
				// e.g. data[0]에서 data[1]로 1 늘린 배열에다 복사

				// 신규
				data[data.length - 1] = stu;
				// 완성된 학생을 data[]에 입력

			} else if (input.equals("3")) {
				Student stu = new Student();
				System.out.print("학번 >> ");
				stu.num = Integer.parseInt(sc.nextLine());
				System.out.print("국어 >> ");
				stu.kor = Integer.parseInt(sc.nextLine());
				System.out.print("영어 >> ");
				stu.eng = Integer.parseInt(sc.nextLine());
				System.out.print("수학 >> ");
				stu.math = Integer.parseInt(sc.nextLine());
				int i = -1; // 임의의 값으로 초기화
				for (i = 0; i < data.length; i++) {
					Student target = data[i];
					if (target.num == stu.num) {
						break;
					}
				}
				if (i < data.length) { // 행의 길이가 넘어가지 않도록
					data[i] = stu;
				} else {
					System.out.println("수정할 학번이 없습니다.");
				}
			} else if (input.equals("4")) {
				System.out.print("학번 >> ");
				int num = Integer.parseInt(sc.nextLine());
				int idx = -1;
				for (int i = 0; i < data.length; i++) {
					if (data[i].num == num) {
						idx = i;
					}
				}
				if (idx > -1) { // 인덱스 번호는 0부터~
					Student[] temp = new Student[data.length - 1];
					// before
//					for(int i = 0; i < idx; i++) {
//						temp[i] = data[i];
//					}
					System.arraycopy(data, 0, temp, 0, idx);
					// after
//					for (int i = idx; i < temp.length; i++) {
//						temp[i] = data[i + 1]; // i가 +1 부터 시작해서 -1 해줌
//					}
					System.arraycopy(data, idx+1, temp, idx, temp.length-idx);
					data = temp;
				}
			}

		}
		System.out.println("이용해주셔서 감사합니다");

	}

}
```
