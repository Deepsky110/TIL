```java
package com.bit.day25;

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;
import java.util.Scanner;

public class Ex03 {

	public static void main(String[] args) {
		// io에는 바이트 스트림과 문자열 스트림
		// 그외에 이를 돕는 필터 스트림들이 있다
		// 필터 스트림(데코레이션 패턴)
		Scanner sc = new Scanner(System.in);
		
		String path = "data1.txt";
		File file = new File(path);
		FileWriter fw = null;
		BufferedWriter bw = null;
		PrintWriter pw = null;
		
		try {
			fw = new FileWriter(file);
			bw = new BufferedWriter(fw);
			pw = new PrintWriter(bw); // 필요한 필터를 적용시키는 것
			while(true) {
				String msg = sc.nextLine();
				if(msg.isEmpty())break; // 두 번 개행하는 순간 반목문 끝
//				bw.write(msg);
//				bw.newLine();
				pw.println(msg);
			}
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if(pw!=null)pw.close(); // close는 필터 적용의 역순으로!
				if(bw!=null)bw.close(); // (객체 생성의 역순으로)
				if(fw!=null)fw.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}

}
```

<br>

### 문자열을 바이트 스트림으로
```java
package com.bit.day25;

import java.io.BufferedOutputStream;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.PrintStream;
import java.util.Scanner;

public class Ex04 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		String path = "data1.txt";
		File file = new File(path);
		
		FileOutputStream fos = null;
		BufferedOutputStream bos = null;
		PrintStream ps = null; // 바이트스트림의 프린트스트림
		
		try {
			
			fos = new FileOutputStream(file);
			bos = new BufferedOutputStream(fos);
			ps = new PrintStream(bos);
			
			while(true) {
				String msg = sc.nextLine();
				if(msg.isEmpty())break;
				byte[] by = msg.getBytes();
//				fos.write(by);
//				fos.write("\r\n".getBytes());
//				bos.write(by);
				ps.println(msg);
//				System.out.println(Arrays.toString(by));
			}
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if(ps!=null)ps.close();
				if(bos!=null)bos.close();
				
				if(fos!=null)fos.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```
