### 아이템 리스너
```java
package com.bit.day23;

import java.awt.Checkbox;
import java.awt.CheckboxMenuItem;
import java.awt.Choice;
import java.awt.Frame;
import java.awt.List;
import java.awt.Panel;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;
import java.util.Arrays;

public class Ex13 extends Frame implements ItemListener{
// 아이템 리스너
	
	Choice cho;
	List list;
	Checkbox ch1, ch2, ch3;
	
	
	@Override
	public void itemStateChanged(ItemEvent e) {
		
//		int[] idxs = list.getSelectedIndexes(); // 선택한 인덱스-아이템을 배열에 담는다
//		String[] names = list.getSelectedItems();
		
//		System.out.println(Arrays.toString(idxs));
//		System.out.println(Arrays.toString(names));
		
//		System.out.println("이벤트 발동"+cho.getSelectedIndex());
//		System.out.println("이벤트 발동"+cho.getSelectedItem());
		////////////////////////////////////////////
//		System.out.println("ch1: "+ch1.getState()); // T/F로 결과 반환
//		System.out.println("ch2: "+ch2.getState());
//		System.out.println("ch3: "+ch3.getState());
		////////////////////////////////////////////
		
		if(e.getSource() == ch1) {
			
			Checkbox obj = (Checkbox)e.getSource(); // 리턴타입 Object - 캐스팅 필요
			System.out.println(obj.getLabel()+" : "+obj.getState()); // 객체 반환
			
			
		} else if (e.getSource() == cho) {
			
			System.out.println("이벤트 발동"+cho.getSelectedIndex());
			System.out.println("이벤트 발동"+cho.getSelectedItem());
			
			
		} else if (e.getSource() == list) {
			
			int[] idxs = list.getSelectedIndexes(); // 선택한 인덱스-아이템을 배열에 담는다
			String[] names = list.getSelectedItems();
			System.out.println(Arrays.toString(idxs));
			System.out.println(Arrays.toString(names));
		}
	}
	
	
	public Ex13() {
		
		Panel p = new Panel();
		ch1 = new Checkbox("item1"); // e.getSource하면 Checkbox 객체가 반환되는 것
		ch2 = new Checkbox("item2");
		ch3 = new Checkbox("item3");
		
		ch1.addItemListener(this);
		ch2.addItemListener(this);
		ch3.addItemListener(this);
		
		p.add(ch1);
		p.add(ch2);
		p.add(ch3);
		
		
		cho = new Choice();
		cho.addItemListener(this); // 아이템을 선택하면 이벤트 발동
		
		cho.addItem("item1");
		cho.addItem("item2");
		cho.addItem("item3");
		cho.addItem("item4");
		p.add(cho);
		
		
		list = new List(4,true); // multi_select
		list.addItemListener(this);
		list.addItem("item1");
		list.addItem("item2");
		list.addItem("item3");
		list.addItem("item4");
		p.add(list);
		
		add(p);
		setSize(500,300);
		setLocation(200,200);
		setVisible(true);
	}
	
	
	public static void main(String[] args) {
		new Ex13();

	}

}
```

<br>

### 텍스트 리스너
```java
package com.bit.day23;

import java.awt.Frame;
import java.awt.Panel;
import java.awt.TextField;
import java.awt.event.TextEvent;
import java.awt.event.TextListener;

public class Ex14 extends Frame implements TextListener{
// 텍스트 리스너
	
	public Ex14() {
		Panel p = new Panel();
		TextField tf = new TextField(15);
		tf.addTextListener(this);
		p.add(tf);
		add(p);
		setSize(500,300);
		setLocation(200,300);
		setVisible(true);
	}
	
	@Override
	public void textValueChanged(TextEvent e) {
		System.out.println(((TextField)e.getSource()).getText());
		
	}
	
	public static void main(String[] args) {
		new Ex14();

	}


}
```

<br>

### 액션 리스너
```java
package com.bit.day23;

import java.awt.Button;
import java.awt.Choice;
import java.awt.Frame;
import java.awt.List;
import java.awt.Panel;
import java.awt.TextField;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.TextEvent;
import java.awt.event.TextListener;


public class Ex15 extends Frame implements ActionListener {
	// 액션 리스너
	

	public Ex15() {
		Panel p = new Panel();

		TextField tf = new TextField(15);
		tf.addActionListener(this);
		p.add(tf);
		
		
		List list = new List();

		list.addActionListener(new ActionListener() { // 익명클래스
			
			@Override 
			public void actionPerformed(ActionEvent e) {
				System.out.println("list의 이벤트");
				
			}
		});
		
		list.addItem("item1");
		list.addItem("item2");
		list.addItem("item3");
		list.addItem("item4");
		p.add(list);

		Button btn = new Button("버튼");
		btn.addActionListener(this);
		p.add(btn);

		add(p);
		setSize(500, 300);
		setLocation(200, 300);
		setVisible(true);
		
	}

	public static void main(String[] args) {
		new Ex15();
	}
	
	public void actionPerformed(ActionEvent e) {
		System.out.println("이벤트발생");
	}
	
}
```

<br>

### 윈도우리스너 - 윈도우어댑터
```java
package com.bit.day23;

import java.awt.Frame;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.awt.event.WindowListener;

class Lec16 implements WindowListener{
	// WindowAdapter 메서드를 열어보면 똑같이 생김, 상속만 받음
  // 윈도우에서 기본적으로 제공하는 기능들 추가
	@Override
	public void windowOpened(WindowEvent e) {}
	public void windowClosing(WindowEvent e) {}
	public void windowClosed(WindowEvent e) {}
	public void windowIconified(WindowEvent e) {}
	public void windowDeiconified(WindowEvent e) {}
	public void windowActivated(WindowEvent e) {}
	public void windowDeactivated(WindowEvent e) {}
}

public class Ex16 extends Frame{
	
	
	public Ex16() {
		addWindowListener(new WindowAdapter(){ // 익명 클래스
			public void windowClosing(WindowEvent e) {
				dispose();
			}
		});
		setSize(500,300);
		setLocation(300,200);
		setVisible(true);
	}
	
	public static void main(String[] args) {
		new Ex16();

	}

}
```
