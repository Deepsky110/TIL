# ArrayList

```java
package com.bit.day16;

// Student 클래스의 필드를 정의하는 부분
// 필드를 정의하고 java.lang.Object의 메서드를 해당 필드에 맞추어
// 오버라이딩 하는 메서드만 들어간다.
// 데이터를 담당하는 '틀'을 우리는 Value Object 혹은 Data Transfer Object를 줄여서
// VO 혹은 DTO 클래스라고 부른다.
// 즉 이 클래스의 이름은 StudentVO 클래스가 되어야 한다.

// 우리가 코딩을 할 때 꼭 외부가 알아야 하는 메서드가 아니면
// 모두다 private 접근제한자를 설정하게 된다.
// 하지만 private 접근제한자는 외부 클래스의 접근을 다 막기 때문에
// 해당 필드 혹은 메서드에 아예 접근할 수 없다.
// 만약 해당 메서드가 이 클래스에서만 사용되면 상관이 없지만
// 만약 외부 클래스에서 필드에 값을 넣으려면?
// 더 이상 직접 접근이 불가능해진다.
// 대신 메서드를 만들어서 그 메서드에 값을 넣거나 값을 빼게 만들어 주어야 한다.

// 이렇게 외부에 클래스 내부를 전부다 공개하는게 아니라
// 꼭 필요한 메서드만 공개하게 모든 접근 제한자를 private으로 설정하고
// 메서드들로만 관리하게 만드는걸 '캡슐화'라고 한다.

public class StudentVO {
	private String name;
	private int korean;
	private int math;
	private int english;

	// 필드에 값을 넣는 메서드는 setter 메서드라고 한다.
	// 필드의 현재값을 출력하는 메서드는 getter 메서드라고 한다
	// 단 출력은 화면 출력이 아니라 그 값 자체를 리턴한다는 의미이다.

	// setter메서드
	// public void set필드명(필드타입 필드이름){
	// this.필드 = 필드;
	// }

	// getter메서드
	// public 필드타입 get필드명(){
	// return 필드명;
	// }

	public void setName(String name) {
		this.name = name;
	}

	public int getKorean() {
		return korean;
	}

	public void setKorean(int korean) {
		this.korean = korean;
	}

	public int getMath() {
		return math;
	}

	public void setMath(int math) {
		this.math = math;
	}

	public int getEnglish() {
		return english;
	}

	public void setEnglish(int english) {
		this.english = english;
	}

	public String getName() {
		return name;
	}

	// equals 메서드는
	// 파라미터로 모든 클래스의 객체가 넘어올 수 있다!
	// 그럼 어떻게 해야 우리가 모든 클래스 객체를 파라미터로 받는
	// 메서드를 선언할 수 있을까?
	// 1. 모든 클래스를 전부다 오버로딩 해준다.
	// 2. 다형성을 사용한다!
	
	public boolean equals(Object o) { // 모든 오브젝트가 매개변수(참조변수, 파라미터)로 들어감
		
		// 두 개의 객체를 비교할 때 가은지 알아보려면
		// 1. 두 개의 객체가 같은 클래스 객체인지 확인해본다.
		// 2. 두 개의 객체가 같은 클래스 객체이면 해당 클래스의 필드 중 특정 필드 혹은
		// 모든 필드를 비교해서 모두 같으면 두 개가 같은 객체이다.
		// 먼저 두 객체가 같은 클래스 객체인지 알아보자
		// 좀 더 자세하게 말하자면 파라미터로 넘어온 o가
		// null이 아니고 StudentVO 클래스의 객체인지 확인하자 (instanceof)
		// 우리는 여기서 간단하게 예약어 하나로 둘을 동시에 확인할 수 있다.
		
		if (o instanceof StudentVO) { // o가 StudentVO의 객체이다
			
			// 이 if문 안에 들어왔다는 것은 parameter로 넘어온 Object o가
			// StudentVO 클래스의 객체란 뜻이므로
			// 우리는 StudentVO의 필드를 꺼낼 수 있다.
			// 하지만 Object o이기 때문에 그 필드들을 o에서 꺼내올 수는 없고
			// 대신 명시적 형변화을 통해서 StudentVO 객체에 덮어씌울 수 있다.
			
			StudentVO s = (StudentVO) o;
			if(name.equals(s.name) && korean == s.korean && english == s.english && math == s.math){
				return true;
			}
		}
		return false;
	}

}
```

```java
package com.bit.day16;

import java.util.ArrayList;

// 우리가 왜 배열에 맞추어서 메소드를 만들어야 할까
// 부제: ArrayList는 답을 알고 있다.

// Collections Framework에는
// 같은 종류의 여러 객체를 한번에 다룰 수 있게 해주는
// 다양한 클래스들이 있다.
// 가장 대표적인 예가 바로 우리가 지금 배울 ArrayList!

public class StudentEx02 {
	public static void main(String[] args) {
		ArrayList<StudentVO> list = new ArrayList<>();
		
		// < >는 template이라고 부른다.
		// template이란 해당 콜렉션 객체가 무슨 클래스의 집합인지 지정한다.
		// 단, 템플릿 안에는 클래스만 들어갈 수 있다!
		// collection Framework는 주소값을 이용하여 집합 내의 요소들을
		// 컨트롤하기 때문에 주소값이 존재하지 않는 기본형 데이터 타입들은
		// template안에 들어갈 수 없다.
		// 그래서 자바는 이 기본형 데이터타입을 클래스의 형태로 바꾼
		// 포장 클래스(wrapper 클래스)가 존재한다.
		
		// Collection Framework는 equals() 메서드를 적극적으로 내부에서 활용한다.
		// 따라서 여러분들이 Collection Framework에 들어있는 클래스를 제대로 활용하기 위해서는
		// 여러분들의 클래스에 equals() 메서드를 정의하는 것이 매우 중요하다.
		// 왜냐! java.lang.Object의 equals 메소드는
		// return this == o;만 적혀있다! (주소값 비교)
		
		// ArrayList의 경우 크기가 자동으로 바뀐다.
		// ArrayList의 현재 크기는 size() 메서드를 실행시키면 된다.
		
		System.out.println("list의 현재크기: "+list.size()); // size : 콜렉션 프레임워크에서 length 대신 사용
		
		StudentVO s = new StudentVO();
		s.setName("홍길동");
		s.setKorean(50);
		s.setEnglish(30);
		s.setMath(60);
		
		StudentVO s2 = new StudentVO();
		s2.setName("홍길동2");
		s2.setKorean(50);
		s2.setEnglish(30);
		s2.setMath(60);
		
		StudentVO s3 = new StudentVO();
		s3.setName("홍길동3");
		s3.setKorean(50);
		s3.setEnglish(30);
		s3.setMath(60);
		
		StudentVO s4 = new StudentVO();
		s4.setName("홍길동4");
		s4.setKorean(50);
		s4.setEnglish(30);
		s4.setMath(60);
		
		StudentVO s5 = new StudentVO();
		s5.setName("홍길동5");
		s5.setKorean(50);
		s5.setEnglish(30);
		s5.setMath(60);
		
		// ArrayList에 추가할 때에는
		// add(추가할 것)를 실행하면 된다.
		list.add(s);;
		System.out.println("list의 현재크기: " + list.size());
		list.add(s2);;
		System.out.println("list의 현재크기: " + list.size());
		list.add(s3);;
		System.out.println("list의 현재크기: " + list.size());
		list.add(s4);;
		System.out.println("list의 현재크기: " + list.size());
		list.add(s5);;
		System.out.println("list의 현재크기: " + list.size());
		
		
		// 만약에 특정 위치에 끼어넣기를 하면?
		// 원래 그 번호에 있던 객체부터는 하나씩 뒤로 밀리고
		// 그 위치에 파라미터로 넘긴 객체가 들어간다.
		// 이 때는 add(index, element)로 실행한다.
		
		StudentVO s6 = new StudentVO();
		s6.setName("홍길동6");
		s6.setKorean(50);
		s6.setEnglish(30);
		s6.setMath(60);
		
		// list에서 해당 위치의 객체를 호출할 때에는
		// get(index)로 호출한다.
		System.out.println("index 2의 StudentVO의 getName(): " + list.get(2).getName()); // 0,1,'2' => 3
		list.add(2, s6); // s6을 2번 배열 자리에 끼어넣어라
		System.out.println("index 2의 StudentVO의 getName(): " + list.get(2).getName());
		
		// list에서 해당 객체의 위치를 알고 싶을때에는
		// indexOf(e) 로 호출한다.
		System.out.println("s4의 list index: "+list.indexOf(s4));
		
		// 만약 해당 객체가 리스트에 여러개 있으면 항상 제일 앞에 있는 index가 리턴된다.
		
		// 만약 가장 뒤에 있는 index가 궁금하면?
		System.out.println("s4의 list lastIndex: "+ list.lastIndexOf(s4)); // 4
		// s4가 한번만 나와서 값은 위랑 똑같다
		list.add(s4); // (s4 값을 하나 추가)
		System.out.println("s4의 list lastIndex: "+ list.lastIndexOf(s4)); // 6 (s4 s5 s4)
		
		// index까진 필요없고 리스트에 존재하는지만 알고 싶다면
		// contains()를 실행하면 된다.
		System.out.println("contains(s4)"+list.contains(s4)); // 존재한다면 true
		
		// indexOf, lastIndexOf, contains 모두
		// 존재하지 않는 객체를 찾으려고 하면
		// 각각 -1, -1, false가 리턴된다.
		
		//  list에서 삭제할 때 두 가지 방법이 가능하다.
		// 1. 해당 인덱스를 삭제
		// 2. 해당 객체와 일치하는 요소 중에서 가장 앞 번호를 삭제
		System.out.println("list의 현재크기: "+ list.size());
		list.remove(0); // 0번 배열을 삭제
		System.out.println("list의 현재크기: "+ list.size());
		
		System.out.println("contains(s6): "+ list.contains(s6)); // true (s6 있음)
		StudentVO s60 = new StudentVO(); // s60은 list에 없다
		s60.setName("홍길동6"); // 파라미터가 오버라이딩 되어있음 s6랑 값이 같음
		s60.setKorean(50);
		s60.setEnglish(30);
		s60.setMath(60);
		list.remove(s60); // 같은 값을 가진 s6가 s60보다 앞에 있으므로 remove 된다.
		System.out.println("contains(s6): "+ list.contains(s6)); // false
		
	}

}
```

```java
package com.bit.day16;

import java.util.ArrayList;
import java.util.Scanner;

public class StudentEx03 {

	public static void main(String[] args) {
		ArrayList<StudentVO> list = new ArrayList<StudentVO>();
		Scanner scanner = new Scanner(System.in);
		
		while(true) {
			System.out.println("고등학교 성적 입출력 프로그램");
			System.out.print("1.입력 2.출력 3.종료 >> ");
			int choice = scanner.nextInt();
			scanner.nextLine();
			if(choice == 1) {
				// 입력할 때만 객체를 만들어서 쓰자
				// 그리고 그 객체를 리스트에 추가하면 언제든 불러올 수 있다!
				StudentVO s = new StudentVO();
				System.out.print("이름: ");
				s.setName(scanner.nextLine());
				System.out.print("국어: ");
				s.setKorean(scanner.nextInt());
				System.out.print("영어: ");
				s.setEnglish(scanner.nextInt());
				System.out.print("수학: ");
				s.setMath(scanner.nextInt());
				list.add(s);
			}else if(choice == 2) {
				for(StudentVO s : list) { // 향상된 for문
					System.out.println(s.getName()+"\t"+s.getKorean());
				}
			}else if(choice == 3) {
				System.out.println("사용해주셔서 감사합니다.");
				break;
			}
		}
		scanner.close();
	}
}
```
