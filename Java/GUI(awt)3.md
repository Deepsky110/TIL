### Toolkit
```java
package com.bit.day23;

import java.awt.Dimension;
import java.awt.Frame;
import java.awt.Toolkit;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

import javax.swing.ImageIcon;
import javax.swing.JButton;

public class Ex01 extends Frame {
	// Toolkit (추상클래스 - 직접 객체생성은 불가, 상속 받아야함)
	public Ex01() {

		Toolkit tool = Toolkit.getDefaultToolkit();
		byte[] data = null;
		File file = new File(".\\game01.png");
		FileInputStream fis = null;

		if (file.exists()) {
			try {
				data = new byte[(int) file.length()]; // length의 리턴값은 long타입
				// 파일 length만큼 배열 길이 확보
				fis = new FileInputStream(file);
				for (int i = 0; i < file.length(); i++) {
					data[i] = (byte) fis.read(); // read의 결과는 int타입
				}
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			} finally {
				if (fis != null) {
					try {
						fis.close();
					} catch (IOException e) {
						e.printStackTrace();
					}
				}
			}

		}

		java.awt.Image img = tool.createImage(data);
		javax.swing.Icon icon = new ImageIcon(data);
		javax.swing.JButton btn01 = new JButton(icon);

		add(btn01);

		setSize(500, 300);
		Dimension dim = tool.getScreenSize();
		// System.out.println(dim.getWidth()); // 1920.0
		// System.out.println(dim.getHeight()); // 1080.0
		// System.out.println(tool.getScreenSize().width); // 1920
		System.out.println(dim.width); // 1920
		System.out.println(dim.height); // 1080

		// 1920*1080
		setLocation(dim.width / 2 - getWidth() / 2, dim.height / 2
				- getHeight() / 2);

		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex01();

	}

}
```

<br>

### 메뉴바 만들기
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.CheckboxMenuItem;
import java.awt.Frame;
import java.awt.Menu;
import java.awt.MenuBar;
import java.awt.MenuItem;

public class Ex02 extends Frame{
// 메뉴바 만들기
	public Ex02(){
		java.awt.Menu mn1 = new Menu();
		mn1.setLabel("File");
		
		java.awt.MenuItem mn1_1 = new MenuItem();
		mn1_1.setLabel("New");
		mn1.add(mn1_1);
		MenuItem mn1_2 = new MenuItem("Save");
		mn1.add(mn1_2);
		
		mn1.addSeparator(); // Save와 Exit 사이에 구분선 추가
		
		MenuItem mn1_3 = new MenuItem("Exit");
		mn1.add(mn1_3);
		
		MenuItem mn2_1 = new java.awt.CheckboxMenuItem("item1");
		MenuItem mn2_2 = new CheckboxMenuItem("item2", true); // 기본 체크 상태로 시작
		MenuItem mn2_3 = new CheckboxMenuItem("item3");
		
		Menu mn2_4 = new Menu("상위메뉴"); // 왜 초기 메뉴로 안들어가지? add 위치가 달라서
		MenuItem mn2_4_1 = new MenuItem("하위메뉴1");
		MenuItem mn2_4_2 = new MenuItem("하위메뉴2");
		mn2_4.add(mn2_4_1);
		mn2_4.add(mn2_4_2);
		
		Menu mn2 = new Menu("Help");
		mn2.add(mn2_1);
		mn2.add(mn2_2);
		mn2.add(mn2_3);
		mn2.add(mn2_4);
		
		java.awt.MenuBar mb = new MenuBar(); // 메뉴바 객체 생성
		
		mb.add(mn1);
		mb.add(mn2);
		
		setMenuBar(mb); // 메뉴바는 add로 집어넣으면 안된다!
		Button btn = new Button("test");
		add(btn);
		
		setSize(500,300);
		setLocation(200, 200);
		setVisible(true);
	}
	
	
	public static void main(String[] args) {
		new Ex02();
	}

}
```

<br>

### 종속된 창 만들기
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.Dialog;
import java.awt.FileDialog;
import java.awt.Frame;

public class Ex03 extends Frame {
	// 종속된 창 만들기
	public Ex03() {
		setSize(800, 600);
		setLocation(200, 200);
		setVisible(true);

//		 java.awt.Dialog dia = new Dialog(this, "새 창"); // 주체는 나 자신 this
		java.awt.FileDialog dia = new FileDialog(this, "새 창", FileDialog.SAVE);
//		java.awt.FileDialog dia = new FileDialog(this, "새 창", FileDialog.LOAD);
		
		// 주체는 나 자신 this, FileDialog.SAVE 대신 숫자 사용 가능
		// dia.add(new Button("버튼"));

		dia.setSize(200, 100);
		// dia.setLocation(200,200); // 부모 창이랑 똑같은 위치에서 시작
		dia.setLocation(200 + 800 / 2 - 200 / 2, 200 + 600 / 2 - 100 / 2);
		dia.setVisible(true);
		System.out.println(dia.getDirectory()); // 경로 출력
		System.out.println(dia.getFile()); // 작업한 파일 제목

	}

	public static void main(String[] args) {
		new Ex03();

	}

}
```

<br>

### 이미지 처리
```java
package com.bit.day23;

import java.awt.Canvas;
import java.awt.Color;
import java.awt.Frame;
import java.awt.Graphics;

public class Ex04 extends Frame {
	// 이미지를 처리하는 방식 - 비트맵/백터

	class MyCanvas extends Canvas {
		// 캔버스를 상속받는 클래스 생성
		public void paint(Graphics g) {
			g.drawString("환영합니다", 800 / 2, 600 / 2);
			g.setColor(Color.MAGENTA);
			g.drawLine(100, 100, 200, 200); // 선
//			g.drawRect(300, 100, 100, 100); // 사각형
//			g.setColor(Color.BLUE);
//			g.drawOval(500, 100, 100, 150); // 원
//			g.drawArc(100, 400, 100, 100, 0, 180);

			g.fillRect(300, 100, 100, 100); // fill 채우기
			g.setColor(Color.BLUE);
			g.fillOval(500, 100, 100, 150);
			g.fillArc(100, 400, 100, 100, 0, 180);
		}
	}

	public Ex04() {
		java.awt.Canvas can = new MyCanvas();
		add(can);

		setSize(800, 600);
		setLocation(200, 200);
		setVisible(true);

	}

	public static void main(String[] args) {
		new Ex04();
	}

}
```

<br>

### 이벤트 - 창 
```java
package com.bit.day23;

import java.awt.Frame;
import java.awt.event.WindowEvent;
import java.awt.event.WindowListener;

public class Ex05 extends Frame implements WindowListener {
	// 이벤트 - 창 프레임 제어

	public Ex05() {
		addWindowListener(this); // 상속 받은 나 자신을 입력
		setSize(500,300);
		setLocation(200,200);
		setVisible(true);
	}

	
	public static void main(String[] args) {
		new Ex05();
	}

	@Override
	public void windowOpened(WindowEvent e) {
		System.out.println("창 열림");
	}

	@Override
	public void windowClosing(WindowEvent e) {
		System.out.println("닫기 버튼을 눌렀을 때 행동");
		dispose(); // 상속 받아서 바로 호출 가능
//		System.exit(0); // 권장하지 않음
	}

	@Override
	public void windowClosed(WindowEvent e) {
		System.out.println("창 닫힘"); // 클로징시 호출됨
	}

	@Override
	public void windowIconified(WindowEvent e) {
		System.out.println("최소화 - 아이콘화");
	}

	@Override
	public void windowDeiconified(WindowEvent e) {
		System.out.println("아이콘에서 활성화"); // 아이콘에서 창으로 활성화됨
	}

	@Override
	public void windowActivated(WindowEvent e) {
		System.out.println("창 비활성화");
	}

	@Override
	public void windowDeactivated(WindowEvent e) {
		System.out.println("창 비활성화"); // 최소화 시키거나, 다른 창을 켜거나 
	}

}
```

### 번외 - swing jframe 창 닫기
```java
package com.bit.day23;

import javax.swing.JFrame;

public class Ex06 extends JFrame {
// 번외 swing jframe 창 닫기
	
	public Ex06() {
		setDefaultCloseOperation(EXIT_ON_CLOSE);
		setSize(500,300);
		setVisible(true);
	}
	
	
	public static void main(String[] args) {
		new Ex06();
	}

}
```

<br>

### 마우스 제어
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

public class Ex07 extends Frame implements MouseListener {
// 이벤트 - 마우스 제어
	
	public Ex07() {
		Panel p = new Panel();
		Button btn = new Button("버튼");
		
		btn.addMouseListener(this); // 내 자신이 가지고 있어서 this
		p.add(btn);
		
		add(p);
		setSize(500,500);
		setLocation(200,200);
		setVisible(true);
	}
	
	
	public static void main(String[] args) {
		new Ex07();
	}


	@Override
	public void mouseClicked(MouseEvent e) {
		System.out.println("클릭 입력");
	}


	@Override
	public void mousePressed(MouseEvent e) {
		System.out.println("버튼 누르는 순간");
	}


	@Override
	public void mouseReleased(MouseEvent e) {
		System.out.println("버튼 떼는 순간");
	}


	@Override
	public void mouseEntered(MouseEvent e) {
		System.out.println("마우스 in");
	}


	@Override
	public void mouseExited(MouseEvent e) {
		System.out.println("마우스 out");
	}

}
```

<br>

### 이벤트 - 마우스 모션
```java
package com.bit.day23;

import java.awt.Frame;
import java.awt.Panel;
import java.awt.event.MouseEvent;
import java.awt.event.MouseMotionListener;

public class Ex08 extends Frame implements MouseMotionListener {
	// 이벤트 - 마우스 모션
	// 배치관리자 - 상대좌표

	public Ex08() {
		Panel p = new Panel();
		p.addMouseMotionListener(this);
		add(p);
		setSize(500, 500);
		setLocation(200, 200);
		setVisible(true);
		System.out.println(p.getWidth()+","+p.getHeight() );
		// 500,500 사이즈로 안나오는 이유 - 프레임 사이즈 포함이라서
	}

	public static void main(String[] args) {
		new Ex08();
	}

	@Override
	public void mouseDragged(MouseEvent e) {
		int x = e.getX();
		int y = e.getY();
		System.out.println("드래그 x=" + x + " ,y=" + y);
	}

	@Override
	public void mouseMoved(MouseEvent e) {
		// System.out.println("마우스 움직임");
	}

}
```

<br>

### 절대좌표
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.TextField;

public class Ex09 extends Frame {
	// 절대좌표 - 배치관리자 없이 직접 좌표 설정 (로케이션, 사이즈)

	public Ex09() {
		// setResizable(false); // 사이즈 조절 불가
		Panel p = new Panel();
		p.setLayout(null);// 입력 안하면 절대좌표
		Button btn1 = new Button("버튼1");
		btn1.setSize(200, 200);
		btn1.setLocation(0, 0); // 패널이 있으면 0,0을해도 제목표시줄에 안가려짐

		TextField tf1 = new TextField(5);
		tf1.setLocation(200, 0);
		tf1.setSize(100,50);
		
		p.add(tf1);
		p.add(btn1);
		add(p);

		setSize(500, 500);
		setLocation(200, 200);
		setVisible(true);
	}

	public static void main(String[] args) {
		
		new Ex09();

	}

}
```

### 패널에 마우스 이벤트 달기
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.event.MouseEvent;
import java.awt.event.MouseMotionListener;

public class Ex10 extends Frame implements MouseMotionListener {

	Button btn;

	public Ex10() {

		Panel p = new Panel();
		p.setLayout(null);
		p.addMouseMotionListener(this); // 패널에 이벤트 달기

		btn = new Button("#");
		btn.setSize(50, 50);
		btn.setLocation(0, 0);
		
		p.add(btn);
		add(p);

		setSize(600, 600);
		setLocation(200, 200);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex10();
	}

	@Override
	public void mouseDragged(MouseEvent e) {
		int x = e.getX();
		int y = e.getY();
		btn.setLocation(x, y);
	}

	@Override
	public void mouseMoved(MouseEvent e) {

	}

}
```

<br>

### 이벤트 - 마우스 더블클릭
```java
package com.bit.day23;

import java.awt.Frame;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

import javafx.scene.control.Button;

public class Ex11 extends Frame implements MouseListener {
	// 이벤트 - 마우스 더블클릭 만들기

	int cnt;
	long before, after;

	@Override
	public void mouseClicked(MouseEvent e) { // 비워두면 오류 떨어짐
		cnt++;
		if (cnt == 1) {
			before = System.currentTimeMillis();
		} else if (cnt == 2) {
			after = System.currentTimeMillis();
			if (after - before < 1000) {
				System.out.println("더블 클릭");
				cnt = 0;// 3,4 넘어가면 안되니까 초기화
			} else {
				before = after;
				cnt = 1;
			}

		}

	}

	public Ex11() {
		addMouseListener(this);
		setSize(400, 300);
		setLocation(200, 200);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex11();
	}

	@Override
	public void mousePressed(MouseEvent e) {
	}

	@Override
	public void mouseReleased(MouseEvent e) {
	}

	@Override
	public void mouseEntered(MouseEvent e) {
	}

	@Override
	public void mouseExited(MouseEvent e) {
	}

}
```

<br>

### 이벤트 - 키보드 타이핑
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.TextField;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class Ex12 extends Frame implements KeyListener {
// 이벤트 - 키보드(타이핑)
	
	TextField tf;
	
	@Override // 밑에 있던 것을 위로 올림
	public void keyTyped(KeyEvent e) {
		e.getKeyCode();
		System.out.println("타이핑-밸류값에 영향"+e.getKeyChar());
	}

	@Override
	public void keyPressed(KeyEvent e) {
		System.out.println("키를 누르는 순간"+e.getKeyCode());
	}

	@Override
	public void keyReleased(KeyEvent e) {
		System.out.println("키를 떼는 순간"+e.getKeyCode());
	}
	
	
	public Ex12() {
		
		Panel p = new Panel();
		
		tf = new TextField(10);
		tf.addKeyListener(this);
		p.add(tf);
		
		Button btn = new Button();
		p.add(btn);
		
		add(p);
		setSize(500,300);
		setLocation(300,200);
		setVisible(true);
	}
	
	public static void main(String[] args) {
		new Ex12();
	}

}
```

<br>

### 이벤트 - 창에서 키보드로 문자 움직이기
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.Frame;
import java.awt.Label;
import java.awt.Panel;
import java.awt.TextField;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;

public class Ex1212 extends Frame implements KeyListener {
	// 이벤트 - 키보드(타이핑) - 창에서 문자 움직이기

	TextField tf;
	Label la;

	@Override
	// 밑에 있던 것을 위로 올림
	public void keyTyped(KeyEvent e) {
		e.getKeyCode();
		System.out.println("타이핑-밸류값에 영향" + e.getKeyChar());

	}

	@Override
	public void keyPressed(KeyEvent e) {
		System.out.println("키를 누르는 순간"+e.getKeyCode());
		
		
		int x = la.getX();
		int y = la.getY();
		if(e.getKeyCode() == 38) {
		la.setLocation(x,y-10);
		}else if(e.getKeyCode() == 40) {
			la.setLocation(x,y+10);
		}else if(e.getKeyCode() == 39) {
			if(x+10<=500-30) { // 패널 기본 사이즈 빼줌
				la.setLocation(x+10,y);
			}
		}else if(e.getKeyCode() == 37) {
			if(x-10>=0) {
				la.setLocation(x-10,y);
			}
		}
	}

	@Override
	public void keyReleased(KeyEvent e) {
		System.out.println("키를 떼는 순간" + e.getKeyCode());
	}

	public Ex1212() {

		Panel p = new Panel();
		p.setLayout(null);

		tf = new TextField(10);
		// p.add(tf);

		Button btn = new Button();
		// p.add(btn);

		la = new Label("★");
		la.setSize(50,50);
		la.setLocation(0,0);
		p.add(la);
		
		addKeyListener(this);
		add(p);
		setSize(500, 300);
		setLocation(300, 200);
		setVisible(true);
	}

	public static void main(String[] args) {
		new Ex1212();
	}

}
```
