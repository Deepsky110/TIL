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

<br>

### DataStream
```java
package com.bit.day25;

import java.io.BufferedOutputStream;
import java.io.DataOutputStream;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class Ex05 {

	public static void main(String[] args) {
		// DataStream
		String path = "data2.bin";
		File file = new File(path);
		try {
			if (!file.exists())	file.createNewFile();
		} catch (IOException e) {
			e.printStackTrace();
		}
		FileOutputStream fos = null;
		BufferedOutputStream bos = null;
		DataOutputStream dos = null;
		
		try {
			fos = new FileOutputStream(file);
			bos = new BufferedOutputStream(fos);
			dos = new DataOutputStream(bos);
			
			dos.write(97);
			dos.writeByte(127);
			dos.writeShort(128);
			dos.writeInt(65);
			dos.writeLong(97L);
			dos.writeFloat(3.14F);
			dos.writeDouble(3.14);
			dos.writeChar('A');
			dos.writeBoolean(true);
			dos.writeUTF("문자열");
			
			System.out.println("작성완료");
			
			
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if (dos != null) dos.close();
				if (bos != null) bos.close();
				if (fos != null) fos.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}

}
```
```java
package com.bit.day25;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.DataInputStream;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class Ex06 {

	public static void main(String[] args) {
		String path = "data2.bin";
		File file = new File(path);
		
		FileInputStream fis = null;
		BufferedInputStream bis = null;
		DataInputStream dis = null;
		
		try {
			fis = new FileInputStream(file);
			bis = new BufferedInputStream(fis);
			dis = new DataInputStream(bis);
			
			int su = 0;
			byte su1 = 0;
			short su2 = 0;
			int su3 = 0;
			long su4 = 0;
			float su5 = 0;
			double su6 = 0;
			char ch = '@';
			boolean boo = false;
			String msg = null;
			
			su = dis.read();
			su1 = dis.readByte();
			su2 = dis.readShort();
			su3 = dis.readInt();
			su4 = dis.readLong();
			su5 = dis.readFloat();
			su6 = dis.readDouble();
			ch = dis.readChar();
			boo = dis.readBoolean();
			msg = dis.readUTF();
			
			System.out.println(su);
			System.out.println(su1);
			System.out.println(su2);
			System.out.println(su3);
			System.out.println(su4);
			System.out.println(su5);
			System.out.println(su6);
			System.out.println(ch);
			System.out.println(boo);
			System.out.println(msg);
			
			
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if (dis != null) dis.close();
				if (bis != null) bis.close();
				if (fis != null) fis.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```
