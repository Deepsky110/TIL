### 파일 생성하고 내용에 글자 추가하기

```java
package com.bit.day21;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class Ex08 {

	public static void main(String[] args) {
		// ByteStream - output
		File file = new File("ex08.bin"); // 새 파일 만들기
		java.io.FileOutputStream fos = null;
		
		try {
			fos = new FileOutputStream(file);  // 인자로 대상인 file 집어넣음
			String msg = "hello";
			
			byte[] byt = msg.getBytes();
			for(int i = 0; i < byt.length; i++) {
				fos.write(byt[i]);
			}
		
			
//			fos.write('a');
//			fos.write('b');
//			fos.write('c');
			
			fos.close(); // io를 점유하고 있으면 다른곳에서 사용 불가
			System.out.println("작성완료");
					
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
		
	}

}
```

<br>

### 파일 input해서 읽기
```java
package com.bit.day21;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class Ex09 {

	public static void main(String[] args) {
		// ByteStream - input 읽어들임

		File file = new File("ex08.bin");
		java.io.FileInputStream fis = null;

		try {
			fis = new FileInputStream(file);

			while (true) {
				int su = fis.read();
				if (su == -1) { // read를 입력회수보다 많이 사용되면(-1) break
					break;
				}
				System.out.print((char) su); // h,e,l,l,o 반복문으로 하나씩 출력
			}

			// System.out.print((char)su);
			// su = fis.read();
			// System.out.print((char)su);
			// su = fis.read();
			// System.out.print((char)su);
			//
			// read를 입력 회수보다 많이 사용하면 -1이 추가된다

			fis.close();

		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}

	} // Ex08에서 bin파일에 65를 쓰고 생성 - 메모장으로 열어보면 A 출력

} // io 작업을 할때는 io exception 따라 try catch 하고
// io close 해주는 것을 기억할것
```

<br>

### 파일 복사하기
```java
package com.bit.day21;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class Ex10 {

	public static void main(String[] args) {
		String path1 = "C:\\Users\\Bitcamp\\Pictures\\baseball_image.jpg";
		File source = new File(path1); // 해당 폴더로부터 파일 읽기
		FileInputStream fis = null;

		String path2 = ".\\copy\\copy1.png";
		File target = new File(path2);
		FileOutputStream fos = null;
		File par = new File(target.getParent()); // 뎁스경로 - 상위 디렉토리로~
		par.mkdirs(); // 디렉토리 생성

		try {
			if (!target.exists()) {
				target.createNewFile();
			}
			fis = new FileInputStream(source);
			fos = new FileOutputStream(target);

			while (true) {
				int su = fis.read();
				if (su == -1) {
					break;
				}
				fos.write(su);
			}
			System.out.println("복사끝");

		} catch (IOException e) {
			e.printStackTrace();

		} finally {
			try {
				if (fis != null) {
					fis.close();
				} 
				if (fos != null) {
					fos.close();
				} // try 안에 있으면 exception이 발생시 close 안됨
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}

}
```
