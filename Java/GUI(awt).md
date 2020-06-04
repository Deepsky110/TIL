# GUI

```java
package com.bit.day21;

public class Ex12 {
// GUI (AWT) - 운영체제에 요청, 운영체제의 기본틀로 구현
	
	public static void main(String[] args) {
		// 배치 관리자 필요
		// 컴포넌트 구성요소 확인 필요
		// 이벤트 처리 필요
		
		java.awt.Frame frame = new java.awt.Frame(); // awt 창 객체 생성
//	javax.swing.JFrame frame = new javax.swing.JFrame(); // swing 창 객체 생성
		
		java.awt.Button btn01 = new java.awt.Button(); // 버튼1 객체 생성
		btn01.setLabel("버튼1입니다"); // 버튼에 이름 붙이기
		frame.add(btn01); // 프레임에 버튼 붙이기
		
		java.awt.Button btn02 = new java.awt.Button(); // 버튼2 객체 생성
		btn02.setLabel("버튼2입니다"); // 동일 크기라 버튼1 위에 덮어씌어짐
		frame.add(btn02);
		
		frame.setSize(500,300); // 사이즈 지정(단위는 픽셀)
		frame.setLocation(700,300); // 초기 위치 설정
		frame.setVisible(true); // 창 구현
		
	}

}
```

<br>

```java
package com.bit.day21;

import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.Frame;
import java.awt.GridLayout;
import java.awt.Panel;

public class Ex13 {
// 배치관리자
	public static void main(String[] args) {
		
		Frame frame = new Frame(); // 창 객체 생성
		java.awt.Panel p = new Panel(); // 패널 객체 생성
//		java.awt.FlowLayout layout = new FlowLayout(); // 구현시 자리가 부족하면 자동개행
		java.awt.GridLayout layout = new GridLayout(2,2);
		// GirdLayout(행, 열) - 우선순위 : 행, 자리가 부족하면 열을 늘림
		p.setLayout(layout);
		
		Button btn01 = new Button();
		btn01.setLabel("버튼1");
		Button btn02 = new Button();
		btn02.setLabel("버튼2");
		Button btn03 = new Button();
		btn03.setLabel("버튼3");
		Button btn04 = new Button();
		btn04.setLabel("버튼4");
		Button btn05 = new Button();
		btn05.setLabel("버튼5");
		
		p.add(btn01); // 패널에 버튼 붙이기
		p.add(btn02);
		p.add(btn03);
		p.add(btn04);
		p.add(btn05);
		
		frame.add(p);
		frame.setLocation(200, 200);
		frame.setSize(400, 200);
		frame.setVisible(true);
	}

}
```

<br>

```java
package com.bit.day21;

import java.awt.Button;
import java.awt.CardLayout;
import java.awt.Frame;
import java.awt.Panel;
import java.util.Scanner;

public class Ex14 extends Frame {
	// 다 만들어 놓고 생성시점에 setVisible

	static CardLayout layout; // 어디서든 사용할 수 있도록 static

	Ex14() {
		layout = new CardLayout(); // 카드 레이아웃 만들기(창은 그대로 컨텐츠만 전환)
		setLayout(layout);

		Panel p1 = new Panel();
		Button btn1 = new Button();
		btn1.setLabel("첫번째");
		p1.add(btn1); // 패널에 버튼 붙이기

		Panel p2 = new Panel();
		Button btn2 = new Button();
		btn2.setLabel("두번째");
		p2.add(btn2);

		Panel p3 = new Panel();
		Button btn3 = new Button();
		btn3.setLabel("세번째");
		p3.add(btn3);

		this.add(p1);
		this.add(p2);
		this.add(p3);

		setSize(500, 300); // 앞에 this. 생략
	}

	public static void main(String[] args) {

		Ex14 me = new Ex14(); // 객체 생성
		me.setVisible(true);

		Scanner sc = new Scanner(System.in);
		while (true) {
			System.out.print("1.다음 0.종료 >> ");
			int su = sc.nextInt();
			if (su == 0) {
				break;
			} else if (su == 1) {
				layout.next(me);
			}
		}

		// layout.next(me); // "두번째"
		// layout.next(me); // "세번째"
		// layout.next(me); // "첫번째"
		// layout.next(me); // "두번째"

	}

}
```

<br>

```java
package com.bit.day21;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.Frame;
import java.awt.Panel;

public class Ex15 extends Frame {
	// 배치관리자
	Ex15() {
		java.awt.BorderLayout layout = new BorderLayout(); // 가장 많이 사용되는 레이아웃
		java.awt.FlowLayout layout2 = new FlowLayout();

		Panel p = new Panel();
		p.setLayout(layout); // 패널에 레이아웃 추가

		Button btn1 = new Button("버튼1");
		Button btn2 = new Button("버튼2");
		Button btn3 = new Button("버튼3");

		Panel west = new Panel();
		west.setLayout(layout2);
		Button btn4 = new Button("버튼4");
		west.add(btn4);

		Panel center = new Panel();
		center.setLayout(layout2);
		Button btn5 = new Button("버튼5");
		center.add(btn5);

		p.add(BorderLayout.NORTH, btn1);
		p.add(BorderLayout.SOUTH, btn2);
		p.add(BorderLayout.EAST, btn3);
		p.add(BorderLayout.WEST, west);
		p.add(BorderLayout.CENTER, center);

		add(p);
		setSize(500, 300);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex15(); // 참조변수 없는 객체 생성

	}

}
```

<br>

```java
package com.bit.day21;

import java.awt.Button;
import java.awt.Frame;
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Panel;

public class Ex16 {

	public static void main(String[] args) {
		java.awt.GridBagLayout layout = new GridBagLayout();

		Frame f = new Frame(); // 프레임 객체 생성
		Panel p = new Panel(); // 패널 생성
		p.setLayout(layout); // 패널에 레이아웃 추가

		Button btn1 = new Button("btn1");
		Button btn2 = new Button("btn2");
		Button btn3 = new Button("btn3");
		Button btn4 = new Button("btn4");
		Button btn11 = new Button("btn11");
		Button btn22 = new Button("btn22");
		Button btn33 = new Button("btn33");
		Button btn44 = new Button("btn44");
		

		GridBagConstraints c = new GridBagConstraints(); // 객체 생성
		c.fill = GridBagConstraints.BOTH; // 버튼의 위 아래 양옆을 크기 만큼 채운다
//		c.fill = GridBagConstraints.HORIZONTAL; // 버튼의 양옆을 크기 만큼 채운다
		
		c.gridx = 0; // x좌표
		c.gridy = 0; // y좌표
		c.gridwidth = 1; // 너비
		c.gridheight = 1; // 높이
		c.weightx = 1.0; // 가중치
		c.weighty = 1.0;
		layout.setConstraints(btn1, c); // constraint의 뜻 : 강제
		p.add(btn1); // 패널에 버튼 달기
		
		
		c.gridx = 1; // x좌표
		c.gridy = 0; // y좌표
		c.gridwidth = 1; // 너비
		c.gridheight = 1; // 높이
		c.weightx = 1.0; // 가중치
		c.weighty = 1.0;
		layout.setConstraints(btn2, c); // btn2에 대한 정보 주기
		p.add(btn2);
		
		
		c.gridx = 2; // x좌표
		c.gridy = 0; // y좌표
		c.gridwidth = 1; // 너비
		c.gridheight = 1; // 높이
		c.weightx = 1.0; // 가중치
		c.weighty = 1.0;
		layout.setConstraints(btn3, c); // btn3에 대한 정보 주기
		p.add(btn3);
		
		c.gridx = 3; // x좌표
		c.gridy = 0; // y좌표
		c.gridwidth = 1; // 너비
		c.gridheight = 1; // 높이
		c.weightx = 1.0; // 가중치
		c.weighty = 1.0;
		layout.setConstraints(btn4, c); // btn4에 대한 정보 주기
		p.add(btn4);
		
		c.gridx = 0; // x좌표
		c.gridy = 1; // y좌표
		c.gridwidth = 2; // 너비
		c.gridheight = 1; // 높이
		c.weightx = 1.0; // 가중치
		c.weighty = 1.0;
		layout.setConstraints(btn11, c);
		p.add(btn11);
		
		f.add(p); // 프레임에 패널 집어넣기
		f.setSize(400, 300);
		f.setVisible(true); // 프레임 화면에 구현
	}

}
```
