## String 이용
```java
package com.bit.day13;

public class Ex09 {

	public static void main(String[] args) {

		java.util.Scanner sc = null;
		sc = new java.util.Scanner(System.in);
		String title = "학생성적관리 프로그램(ver 0.1.0)";
		String menu = "1.보기 2.입력 3.수정 4.삭제 0.종료>> ";
		// String input="";
		int input = 0;
		String data = "학번\t|국어\t|영어\t|수학\t|합계\t|평균\n";
		data += "----------------------------------------------\n";
		System.out.println(title);
		System.out.println("----------------------------------------------");
		int cnt = 0;
		while (true) {
			System.out.print(menu);
			// input=sc.nextLine();
			input = sc.nextInt();
			if (input == 0) {
				break;
			} // 프로그램 종료
			if (input == 1) {
				System.out.println(data);
			}
			if (input == 2) {
				cnt++; // 학번은 자동으로 카운트됨
				System.out.println("국어>> ");
				int kor = sc.nextInt();
				System.out.println("영어>> ");
				int eng = sc.nextInt();
				System.out.println("수학>> ");
				int math = sc.nextInt();
				int sum = kor + eng + math;
				double avg = sum * 100 / 3 / 100.0;
				data += cnt + "\t|" + kor + "\t|" + eng + "\t|" + math + "\t|"
						+ sum + "\t|" + avg + "\n"; // data는 data+추가정보 (누적)
			}
			if (input == 3) { // 똑같은데 학번을 입력 받아야함
				System.out.println("학번>> ");
				int num = sc.nextInt();
				System.out.println("국어>> ");
				int kor = sc.nextInt();
				System.out.println("영어>> ");
				int eng = sc.nextInt();
				System.out.println("수학>> ");
				int math = sc.nextInt();
				int sum = kor + eng + math;
				double avg = sum * 100 / 3 / 100.0;

				String msg = num + "\t|" + kor + "\t|" + eng + "\t|" + math
						+ "\t|" + sum + "\t|" + avg;
				// num(학번)을 찾아서 msg랑 교체해야한다

				int idx = data.indexOf("\n" + num); // 인덱스(위치)를 찾는다 //num만 찾으면 점수랑 구분 어려움
				String data1 = data.substring(0, idx + 1); // 0(맨 앞)에서 다음줄 숫자 앞까지
				String data2 = data.substring(data.indexOf("\n", idx + 1));
				data = data1 + msg + data2;
			}
			if (input == 4) { // 똑같은데 국영수 안받아도 됨
				System.out.println("학번>> ");
				int num = sc.nextInt();
				int idx = data.indexOf("\n" + num);
				String data1 = data.substring(0, idx + 1);
				String data2 = data.substring(data.indexOf("\n", idx + 1));
				data = data1 + data2; // 메세지를 제거해준다
			}
		}
		System.out.println("이용해주셔서 감사합니다.");

	}
}
```
<br>

## 이중 배열 이용
```java
package com.bit.day13;

public class Ex10 {

	public static void main(String[] args) {
		java.util.Scanner sc = null;
		sc = new java.util.Scanner(System.in);
		String title = "학생성적관리 프로그램(ver 0.1.0)";
		String menu = "1.보기 2.입력 3.수정 4.삭제 0.종료>> ";
		// 학번 국어 영어 수학
		// 전부 숫자라는 공통점 => int
		System.out.print("총인원: ");
		int su = sc.nextInt(); // 총인원 입력

		int[][] data = null;
		data = new int[su][]; // 이중배열 생성
		System.out.println(title);
		System.out.println("---------------------------------------------");

		int input = 0;
		int idx = 0;
		int cnt = 0; // 학번

		while (true) {
			System.out.print(menu);
			input = sc.nextInt();
			if (input == 0) {
				break; // 반복문을 빠져나감 => 프로그램 종료
			}
			if (input == 2 && su > cnt) {
				int[] stu = new int[4];
				data[idx++] = stu;
				cnt++;
				stu[0] = cnt;
				System.out.print("국어>> ");
				stu[1] = sc.nextInt();
				System.out.print("영어>> ");
				stu[2] = sc.nextInt();
				System.out.print("수학>> ");
				stu[3] = sc.nextInt();
			}
			if (input == 1) {
				System.out.println("학번\t|국어\t|영어\t|수학\t|합계\t|평균");
				System.out.println("---------------------------------------------");
				for (int i = 0; i < data.length; i++) {
					int[] stu = data[i];
					if (stu == null) {
						continue;
					} // stu 값이 지워져서 없으면 다시 반복문으로
					System.out.print(stu[0] + "\t|");
					System.out.print(stu[1] + "\t|");
					System.out.print(stu[2] + "\t|");
					System.out.print(stu[3] + "\t|");
					System.out.print(stu[1] + stu[2] + stu[3] + "\t|");
					System.out.println((stu[1] + stu[2] + stu[3]) * 100 / 3 / 100.0);
				}
			}
			if (input == 4) {
				int tmp = -1;
				System.out.print("학번>> ");
				int num = sc.nextInt();
				for (int i = 0; i < data.length; i++) {
					int[] stu = data[i];
					if (stu == null) {
						continue;
					}
					if (stu[0] == num) {
						tmp = i;
					}
					if (tmp != -1) {
						data[tmp] = null;
					}
				}
			}
			if (input == 3) { // 3.수정
				int tmp = -1;
				int[] stu = new int[4];
				System.out.print("학번>> ");
				int num = sc.nextInt();
				for (int i = 0; i < data.length; i++) {
					int[] stu2 = data[i];
					if (stu2 == null) {
						continue;
					}
					if (stu2[0] == num) {
						tmp = i;
					}
					
				}
				if (tmp != -1) {
					data[tmp] = stu;
				}
				stu[0] = num;
				System.out.print("국어>> ");
				stu[1] = sc.nextInt();
				System.out.print("영어>> ");
				stu[2] = sc.nextInt();
				System.out.print("수학>> ");
				stu[3] = sc.nextInt();
			}
		}
		System.out.println("이용해주셔서 감사합니다.");
	}
}
```
<br>

## 배열 이용
```java
package com.bit.day14;

public class Ex11 {

	public static void main(String[] args) {
		// 학생성적관리 프로그램(ver 0.1.1) - 배열을 이용
		// 학번 이름 국어 영어 수학
		
		java.util.Scanner sc = new java.util.Scanner(System.in);
		String[] data = null;
		System.out.print("총원>> ");
		int limit = Integer.parseInt(sc.nextLine()); // 문자형을 받아서 정수형으로
		data = new String[limit];
		int err = 0; // 에러를 카운팅 할 것이다
		int cnt = 0; // 학번 자동 카운팅을 위한 초기화
		
		while(true){
			System.out.print("1.보기 2.입력 3.수정 4.삭제 0.종료>> ");
			String input = sc.nextLine();
			if(input.equals("0")){break;}
			if(input.equals("1")){err=0; // 제대로 입력하면 에러 카운팅 초기화
				// 보기
				System.out.println("------------------------------------------------");
				System.out.println("학번\t|이름\t|국어\t|영어\t|수학\t|평균");
				System.out.println("------------------------------------------------");
				for(int i=0; i<data.length; i++){
					if(data[i]==null){continue;} //null일 경우 가장 가까운 반복문으로
					String msg = data[i];
					String[] stu = msg.split(","); // , 기준으로 자르기
					int num = Integer.parseInt(stu[0]);
					String name = stu[1];
					int kor = Integer.parseInt(stu[2]);
					int eng = Integer.parseInt(stu[3]);
					int math = Integer.parseInt(stu[4]);
					double avg = (kor+eng+math)*100/3/100.0; // 소수점 구하기
					System.out.println(num+"\t|"+name+"\t|"+kor+"\t|"+eng+"\t|"+math+"\t|"+avg);
				}
				System.out.println("------------------------------------------------");
				
			}else if(input.equals("2")){err=0;
				// 입력
				if(cnt < limit){
					cnt++; // 학번 자동 카운팅
					System.out.print("이름>> ");
					String name = sc.nextLine();
					System.out.print("국어>> ");
					int kor = Integer.parseInt(sc.nextLine());
					System.out.print("영어>> ");
					int eng = Integer.parseInt(sc.nextLine());
					System.out.print("수학>> ");
					int math = Integer.parseInt(sc.nextLine());
					data[cnt-1] = cnt +","+ name +","+ kor +","+ eng +","+ math;
				}else{
					System.out.println("입력할 학생이 없습니다");
				}
				
			}else if(input.equals("3")){err=0;
				// 수정
				System.out.print("학번>> ");
				int num = Integer.parseInt(sc.nextLine());
				System.out.print("이름>> ");
				String name = sc.nextLine();
				System.out.print("국어>> ");
				int kor = Integer.parseInt(sc.nextLine());
				System.out.print("영어>> ");
				int eng = Integer.parseInt(sc.nextLine());
				System.out.print("수학>> ");
				int math = Integer.parseInt(sc.nextLine());
				data[num-1] = num +","+ name +","+ kor +","+ eng +","+ math;
				
			}else if(input.equals("4")){err=0;
				// 삭제
				System.out.print("학번>> ");
				int num = Integer.parseInt(sc.nextLine());
				data[num-1] = null;
				
			}else{
				err++;
				System.out.println("메뉴를 확인하시고 입력하세요\n\n");
				if(err>3){
					System.out.println("이용방법을 다시 확인해주세요");
					break;
				}
			}
		} // while end
		System.out.println("이용해주셔서 감사합니다");	
	} // main end
}
```
<br>

## 객체-배열 이용
```java
package com.bit.day14;
// 학생성적관리 프로그램 - 객체 배열 이용

class Student{
	int num;
	String name;
	int kor, eng, math;
	char gender;
	int age;
	
	Student(int num){
		this.num = num;
	}
}

public class Ex12 {

	public static void main(String[] args) {
		java.util.Scanner sc = new java.util.Scanner(System.in);
		System.out.print("총원>> ");
		int max = Integer.parseInt(sc.nextLine());
		Student[] data = new Student[max];
		int cnt = 0;
		
		while(true){
			System.out.print("1.보기 2.입력 3.수정 4.삭제 0.종료>> ");
			String input = sc.nextLine();
			if(input.equals("0")){
				break;
			}else if(input.equals("1")){ // 보기
				System.out.println("------------------------------------------------");
				System.out.println("학번\t|이름\t|국어\t|영어\t|수학\t|평균");
				System.out.println("------------------------------------------------");
				for(int i=0; i<data.length; i++){
					Student stu = data[i];
					if(stu==null){continue;}
					System.out.print(stu.num+"\t|");
					System.out.print(stu.name+"\t|");
					System.out.print(stu.kor+"\t|");
					System.out.print(stu.eng+"\t|");
					System.out.print(stu.math+"\t|");
					System.out.println((stu.kor+stu.eng+stu.math)*100/3/100.0);
				}
			} else if(input.equals("2") && cnt < max){ // 입력 // ++cnt가 아직 미적용이라 -1안함
				Student stu = new Student(++cnt);
				System.out.print("이름>> ");
				stu.name = sc.nextLine();
				System.out.print("국어>> ");
				stu.kor = Integer.parseInt(sc.nextLine());
				System.out.print("영어>> ");
				stu.eng = Integer.parseInt(sc.nextLine());
				System.out.print("수학>> ");
				stu.math = Integer.parseInt(sc.nextLine());
				data[cnt-1] = stu;
				
			}else if(input.equals("3")){ // 수정
				System.out.print("학번>> ");
				int num = Integer.parseInt(sc.nextLine());
				Student stu = new Student(num);
				System.out.print("이름>> ");
				stu.name = sc.nextLine();
				System.out.print("국어>> ");
				stu.kor = Integer.parseInt(sc.nextLine());
				System.out.print("영어>> ");
				stu.eng = Integer.parseInt(sc.nextLine());
				System.out.print("수학>> ");
				stu.math = Integer.parseInt(sc.nextLine());
				data[num-1] = stu;
			}else if(input.equals("4")){
				System.out.print("학번>> ");
				int num = Integer.parseInt(sc.nextLine());
				data[num-1] = null;
			}
				
		}

	}

}
```
