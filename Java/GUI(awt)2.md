### 스타일 설정
```java
package com.bit.day22;

import java.awt.Button;
import java.awt.Color;
import java.awt.FlowLayout;
import java.awt.Font;
import java.awt.Frame;
import java.awt.GridLayout;
import java.awt.Label;
import java.awt.Panel;

import javax.swing.JLabel;

public class Ex09 extends Frame {
	// GUI

	Ex09() {
		Panel p = new Panel();
		Panel p2 = new Panel();

		// Color color = new Color(255,80,55); // rgb칼라 - 색 번호로 입력
		// 가능(255,255,255)
		// p2.setBackground(color);
		p2.setBackground(Color.orange); // 색 이름으로 입력하기
		p.setLayout(new GridLayout()); // 레이아웃 설정 안하면 디폴트는 FlowLayout

		Button btn1 = new Button();
		Button btn2 = new Button("btn2");
		
		btn1.setLabel("New Name");
		
		Font font = null;
		Font font2 = null;
		font = new Font("궁서", 2, 32); // (폰트명,스타일,사이즈) - 전부 되는 것은 아니다
		font2 = new Font(Font.SANS_SERIF, Font.BOLD, 35); // 특정 폰트, 스타일은 상수로 지정
		
		btn1.setFont(font2);
		
//		Label la1 = new Label(); // awt에서 한글 폰트 지원 안해서
		JLabel la1 = new JLabel(); // Swing으로 처리함 JLabel
		
		la1.setText("출력합니다"); // set으로 준비하고 get으로 구현
		la1.setFont(font);
		
		System.out.println(la1.getText());

		
		p.add(btn1);
		p.add(p2); // 패널 안에 패널 넣기
		p2.add(btn2);
		p2.add(la1);
		
		add(p);
		setLocation(200, 200);
		setSize(500, 300);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex09(); // 객체 생성
	}

}
```

<br>

### 전화번호 자판 만들기
```java
package com.bit.day22;

import java.awt.Button;
import java.awt.Frame;
import java.awt.GridLayout;
import java.awt.Panel;

public class Ex10 extends Frame {

	public Ex10() {
		Panel p = new Panel();
		p.setLayout(new GridLayout(4, 3));
		for (int i = 0; i < 12; i++) {
			String num = null;
			if (i == 9) {
				num = "*";
			} else if (i == 10) {
				num = "0";
			} else if (i == 11) {
				num = "#";
			} else {
				num = i + 1 + "";
			}
			Button btn = new Button(num);
			p.add(btn);
		}
		add(p);
		setLocation(200, 200);
		setSize(300, 400);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex10();
	}

}
```

<br>

### TextField 클래스
```java
package com.bit.day22;

import java.awt.Button;
import java.awt.Color;
import java.awt.Font;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.TextField;

public class Ex11 extends Frame {
	
	static java.awt.TextField tf1;
	
	// 디폴트 형식 FlowLayout은 초기컨텐츠 길이에 맞춰 사이즈 늘어남
	public Ex11() {
		Font font = new Font(Font.MONOSPACED, Font.BOLD, 22);
		Panel p = new Panel();
		
		p.setBackground(Color.MAGENTA);
		
		java.awt.TextField tf1 = new TextField(5); // TextField(글자개수)
		
		tf1.setText("");
		tf1.setEchoChar('*'); // 입력 문자를 *로 바꿔서 보여주기
//		tf1.setSize(200,10); // 사이즈 지정 불가
		p.add(tf1);

		Button btn = new Button("버튼버튼");
		btn.setFont(font);
//		// btn.setSize(100,100); // 사이즈 지정 불가
		p.add(btn);


		add(p);
//		// 1920*1080
		setLocation(1920 / 2 - 500 / 2, 1080 / 2 - 300 / 2); // 화면 가운데서 창 띄우기
		setSize(500, 300);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex11();
		try {
			Thread.sleep(10000);  // 10초
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		System.out.println(tf1.getText());
	}

}
```

<br>

### TextArea
```java
package com.bit.day22;

import java.awt.Button;
import java.awt.Color;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.TextArea;

public class Ex12 extends Frame {

	public Ex12() {
		Panel p = new Panel();
		p.setBackground(Color.MAGENTA);
//		TextArea ta = new TextArea(3, 20); // (행,열)
//		TextArea ta = new TextArea("초기값",10,30,3); // (초기값,행,열,스크롤제어)
		TextArea ta = new TextArea("초기값",10,30,TextArea.SCROLLBARS_NONE);
//		ta.setText("출력\n두번째줄");
//		ta.setVisible(false);
//		ta.setEditable(false); // 타이핑만 안됨, 선택,복사 가능
		ta.setEnabled(false); // 타이핑, 선택 안됨
		ta.setColumns(50); // 열 사이즈
		ta.setRows(20); // 행 사이즈
		p.add(ta);
		
		Button btn = new Button("버튼");
//		btn.setVisible(false);
		btn.setEnabled(false); // 버튼 비활성화
		

		p.add(btn);
		add(p);
		setLocation(200, 200);
		setSize(500, 400);
		setVisible(true);

	}

	public static void main(String[] args) {
		new Ex12();
	}

}
```

<br>

### Checkbox, CheckboxGroup
```java
package com.bit.day22;

import java.awt.Checkbox;
import java.awt.CheckboxGroup;
import java.awt.Font;
import java.awt.Frame;
import java.awt.Panel;

public class Ex13 extends Frame {

	public Ex13() {

		Panel p = new Panel();
		Font font = new Font("궁서체", 0, 22); // 사이즈 조절

		CheckboxGroup cbg = new CheckboxGroup();
		// 옵션을 다 추가해야 그룹화 가능
		// 옵션중 하나만 선택 가능하게 하기 위해서

//		Checkbox chk01 = new Checkbox("item1");
		Checkbox chk01 = new Checkbox("item1", false, cbg);
		Checkbox chk02 = new Checkbox("item2", false, cbg); // true - 체크된 상태로 시작
		Checkbox chk03 = new Checkbox("", false, cbg);
		chk03.setLabel("item3"); // 나중에 chk03 이름 설정

		chk01.setFont(font);
		chk02.setFont(font);
		chk03.setFont(font);

		p.add(chk01);
		p.add(chk02);
		p.add(chk03);

		add(p);
		setLocation(200, 200);
		setSize(500, 300);
		setVisible(true);
	}

	public static void main(String[] args) {

		new Ex13();
	}

}
```

<br>

### choice
```java
package com.bit.day22;

import java.awt.Choice;
import java.awt.Dimension;
import java.awt.Frame;
import java.awt.Panel;

public class Ex14 extends Frame {

	public Ex14() {
		
		Panel p = new Panel();
		Choice cho = new Choice();
		cho.addItem("item1");
		cho.addItem("item2");
		cho.addItem("item3");
		cho.addItem("item4");
		
		cho.select(1); // 처음 보여지는 값 설정 (0부터)
		
		p.add(cho);
		add(p);
	
		setSize(500, 300);
		// 1920*1080
		Dimension dim = getSize();
		int w = dim.width;
		int h = dim.height;
		setLocation(1920 / 2 - w / 2, 1080 / 2 - h / 2);
		setVisible(true);
		System.out.println(cho.getSelectedIndex()); // 선택된 인덱스
		System.out.println(cho.getSelectedItem()); // 인덱스가 가르키는 값

	}

	public static void main(String[] args) {
		new Ex14();

	}

}
```

<br>

### List(java.awt.List)
```java
package com.bit.day22;

import java.awt.Dimension;
import java.awt.Frame;
import java.awt.List;
import java.awt.Panel;

public class Ex15 extends Frame {

	public Ex15() {
		Panel p = new Panel();

		java.awt.List list = new List(5, true); // (디폴트목록개수, 다중선택여부);
		list.addItem("item1"); // 혼동을 방지하기 위해 add 대신 사용
		list.addItem("item2");
		list.addItem("item3");
		list.addItem("item4"); // new List(); 미입력시 디폴트는 4개까지
		list.addItem("item5");
		// list.add("item1"); // 자료구조의 list와 흡사
		// list.add("item2"); // import할 때 awt, util 구분 주의
		// list.add("item3");
		// list.add("item4");
		list.select(2); // 인덱스2번을 초기선택 상태로 시작

		p.add(list);
		add(p);
		
		Dimension dim = new Dimension();

		setSize(500, 400);
		setLocation(200, 200);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex15();
	}

}
```

<br>

### GUI, 배열을 이용한 계산기버튼 만들기
```java
package com.bit.day22;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Frame;
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Panel;
import java.awt.TextField;

public class Ex16 extends Frame {

	public Ex16() {
		Panel p = new Panel();
		Panel p2 = new Panel();
		String[] names = {
				"ac","*","/","+",
				"7","8","9",
				"4","5","6","-",
				"1","2","3","=",
				"0","."
		};
		Button[] btns = new Button[17]; // 버튼 17개 준비
		for(int i = 0; i<btns.length; i++) {
			btns[i] = new Button(names[i]);
			
		}
		GridBagLayout layout = new GridBagLayout();
		p2.setLayout(layout);
		GridBagConstraints gbc = new GridBagConstraints();
		
		gbc.fill = GridBagConstraints.BOTH;

		func(p2, layout, gbc, btns[0], 0,0,1,1);
		func(p2, layout, gbc, btns[1], 1,0,1,1);
		func(p2, layout, gbc, btns[2], 2,0,1,1);
		func(p2, layout, gbc, btns[3], 3,0,1,2);
		
		func(p2, layout, gbc, btns[4], 0,1,1,1);
		func(p2, layout, gbc, btns[5], 1,1,1,1);
		func(p2, layout, gbc, btns[6], 2,1,1,1);
		
		func(p2, layout, gbc, btns[7], 0,2,1,1);
		func(p2, layout, gbc, btns[8], 1,2,1,1);
		func(p2, layout, gbc, btns[9], 2,2,1,1);
		func(p2, layout, gbc, btns[10], 3,2,1,1);
		
		func(p2, layout, gbc, btns[11], 0,3,1,1);
		func(p2, layout, gbc, btns[12], 1,3,1,1);
		func(p2, layout, gbc, btns[13], 2,3,1,1);
		func(p2, layout, gbc, btns[14], 3,3,1,2);
		
		func(p2, layout, gbc, btns[15], 0,4,2,1);
		func(p2, layout, gbc, btns[16], 2,4,1,1);
		
		
		
		p.setLayout(new BorderLayout());
		p.add(BorderLayout.NORTH, new TextField());
		p.add(BorderLayout.CENTER, p2);
		
		add(p);
		
		setSize(500,600);
		setLocation(200, 200);
		setVisible(true);
	}

	public void func(Panel p2, GridBagLayout layout
			,GridBagConstraints gbc, Button btn, int x, int y, int w, int h) {
		
		gbc.gridx = x;
		gbc.gridy = y;
		gbc.gridwidth = w;
		gbc.gridheight = h;
		gbc.weightx = 1.0;
		gbc.weighty = 1.0;
		
		layout.setConstraints(btn, gbc);
		p2.add(btn);
	}
	
	public static void main(String[] args) {
		new Ex16();

	}

}
```

<br>

### GUI에 IO로 파일 읽어오기
```java
package com.bit.day22;

import java.awt.Frame;
import java.awt.TextArea;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.ArrayList;

// io 를 통해 파일 읽어오기
public class Ex17 extends Frame {

	TextArea ta;

	public Ex17() {
		ta = new TextArea();
		
		add(ta); // 프레임의~
		setLocation(200, 200);
		setSize(800, 600);
		setVisible(true);
	}

	public static void main(String[] args) {
		ArrayList<Character> list = new ArrayList<>();
		Ex17 me = new Ex17();
		File file = new File("text.txt");
		FileInputStream fis = null;

		if (file.exists()) {
			try {
				fis = new FileInputStream(file);
				
				while (true) {
					int su = fis.read(); // 읽어 온 내용을 int로 변환
					if (su == -1) { // 문자 없으면 -1 나옴
						break;
					}
					list.add((char) su);
				}
				Object[] arr1 = list.toArray();
				char[] arr2 = new char[arr1.length];
				for (int i = 0; i < arr1.length; i++) {
					arr2[i] = (char) arr1[i];
				}
				me.ta.setText(new String(arr2));
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			} finally {
				if (fis != null)
					try {
						fis.close();
					} catch (IOException e) {
						e.printStackTrace();
					}
			}
		}
	}
}
```
