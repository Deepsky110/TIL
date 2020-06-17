### ByteArrayStream
```java
package com.bit.day25;

import java.io.ByteArrayInputStream;
import java.io.ByteArrayOutputStream;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.Arrays;

public class Ex08 {

	public static void main(String[] args) {
		// ByteArrayStream
		// CharArrayStream
		
		// java.io.CharArrayReader
		// java.io.CharArrayWriter
		
		// 파일에 직접 쓰고 읽는 것이 아니라 byte배열에 값을 저장했다가 꺼냄
		String path = "data1.txt";
		File file = new File(path);
		FileInputStream fis = null;
		ByteArrayOutputStream baos = null;
		ByteArrayInputStream bais = null;

		try {
			fis = new FileInputStream(file);
			baos = new ByteArrayOutputStream();

			while (true) {
				int su = fis.read();
				if (su == -1) {
					break;
				}
				baos.write(su);
			}
			byte[] result = baos.toByteArray(); // 바이트 데이터를 집어넣음
			System.out.println(Arrays.toString(result));
			bais = new ByteArrayInputStream(result);
			while (true) {
				int su = bais.read();
				if (su == -1)
					break;
				System.out.print((byte) su + ",");
			}

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if (baos != null)
					baos.close();
				if (fis != null)
					fis.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```

<br>

### ObjectStream으로 쓰기
```java
package com.bit.day25;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;
import java.io.Serializable;
import java.util.ArrayList;
import java.util.Vector;

class Student implements Serializable {
	// Class는 java.io의 Serializable 상속해야 ObjectStream에서 쓸 수 있음
	int num;
}

public class Ex09 {

	public static void main(String[] args) {
		// ObjectStream 으로 쓰기
		String path = "data4.bin";
		File file = new File(path);
		try {
			if (!file.exists())
				file.createNewFile();
		} catch (IOException e) {
			e.printStackTrace();
		}

		FileOutputStream fos = null;
		ObjectOutputStream oos = null;

		try {
			fos = new FileOutputStream(file);
			oos = new ObjectOutputStream(fos);

			String msg = new String("오브젝트 작성");
			ArrayList<Integer> arr1 = new ArrayList<>();
			arr1.add(1111);
			arr1.add(2222);
			arr1.add(3333);
			arr1.add(4444);

			Vector vec = new Vector();
			vec.add(1234);
			vec.add(3.14);
			vec.add(true);
			vec.add('A');
			vec.add("문자열");

			int[] arr = { 1, 3, 5, 7, 9 };

			Vector v = new Vector();
			v.add(arr);
			v.add(vec);

			oos.writeObject(msg);
			oos.writeObject(arr1);
			oos.writeObject(vec);
			oos.writeObject(arr);
			oos.writeObject(v);
			oos.writeObject(new Student());

			System.out.println("작성완료");

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if (oos != null)
					oos.close();
				if (fos != null)
					fos.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```

### ObjectStream으로 읽어오기
```java
package com.bit.day25;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Enumeration;
import java.util.Vector;

public class Ex10 {

	public static void main(String[] args) {
		// ObjectStream 으로 쓴 것 읽어오기

		String path = "data4.bin";
		File file = new File(path);
		FileInputStream fis = null;
		ObjectInputStream ois = null;

		try {
			fis = new FileInputStream(file);
			ois = new ObjectInputStream(fis);

			String msg = (String) ois.readObject();
			ArrayList<Integer> list = (ArrayList<Integer>) ois.readObject();

			System.out.println(msg);
			for (int i = 0; i < list.size(); i++) {
				System.out.println(list.get(i));
			}

			Vector v = (Vector) ois.readObject(); // Ex09에 벡터 입력값 읽기
			Enumeration em = v.elements();
			while (em.hasMoreElements()) {
				System.out.println(em.nextElement());
			}

			int[] sus = (int[]) ois.readObject(); // Ex09 배열 입력값 읽기
			System.out.println(Arrays.toString(sus));

			Vector v2 = (Vector) ois.readObject();
			int[] ele1 = (int[]) v2.get(0); // 첫번째 것을 꺼내면?
			System.out.println(Arrays.toString(ele1));
			
			Vector v3 = (Vector) v2.get(1); // 입력했던 값이 맞춰 형변환
			em = v3.elements();
			while(em.hasMoreElements()){
				System.out.println(em.nextElement());
			}
			
			Student stu = (Student) ois.readObject(); // Student클래스 읽기
			System.out.println(stu);

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} finally {
			try {
				if (ois != null)
					ois.close();
				if (fis != null)
					fis.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```

<br>

### ObjectStream으로 쓰기2
```java
package com.bit.day26;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;
import java.io.Serializable;


public class Ex01 {
	// Object 스트림 - 쓰기
	public static void main(String[] args) {
		

		String path = "data1.bin";
		File file = new File(path);

		try {
			if (!file.exists())
				file.createNewFile();
		} catch (IOException e) {
			e.printStackTrace();
		}

		FileOutputStream fos = null;
		ObjectOutputStream oos = null;

		try {
			fos = new FileOutputStream(file);
			oos = new ObjectOutputStream(fos);

			// oos.writeObject(new Student(1,"홍길동",90,80,70));
			Student stu = new Student(1, "홍길동", 90, 80, 70);
			oos.writeObject(stu);
			stu.show();

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if (oos != null)
					oos.close();
				if (fos != null)
					fos.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```

### ObjectStream 읽어오기2
```java
package com.bit.day26;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.ObjectInputStream;

public class Ex02 {
	// Ex01 읽어오기
	public static void main(String[] args) {
		// File file = new File("data1.bin");

		FileInputStream fis = null;
		ObjectInputStream ois = null;

		try {
			fis = new FileInputStream("data1.bin"); // 직접 입력 가능
			ois = new ObjectInputStream(fis);

			Student stu = null;
			stu = (Student) ois.readObject();
			stu.show();

			System.out.println("학번:" + stu.num); // 필드에 접근하기
			System.out.println("이름:" + stu.name);
			System.out.println("국어:" + stu.kor);
			System.out.println("영어:" + stu.eng);
			// System.out.println("수학:"+stu.math);
			// private int math라 바로 접근 불가, 데이터 값은 있는데 접근 불가
			System.out.println(stu); // Student의 toString 리턴값

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} finally {
			try {
				if (ois != null)
					ois.close();
				if (fis != null)
					fis.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```
