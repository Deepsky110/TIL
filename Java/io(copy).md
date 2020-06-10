### 파일 복사하기
Ex01에서 만든 파일 Ex02로 복사하기


1. 파일 만들기
```java
package com.bit.day25;

import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class Ex01 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String path = "data1.txt";
		File file = new File(path);
		
		FileWriter fw = null;
		try {
			fw = new FileWriter(file);
			while(true) {
				String msg = sc.nextLine();
				if(msg.equals("/exit")) break;
				fw.write(msg);
				fw.write("\r\n"); // 윈도우 환경에서의 개행
			}
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if(fw!=null)fw.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```

<br>

2. 파일 복사하기
```java
package com.bit.day25;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class Ex02 {
	// Ex01에서 만든 파일을 복사
	public static void main(String[] args) {
		String path = "data1.txt";
		String path2 = "copy.txt";
		File source = new File(path);
		File target = new File(path2);

		try {
			if (!target.exists())
				target.createNewFile();
		} catch (IOException e) {
			e.printStackTrace();
		}
		
		char[] cbuf = new char[5]; // 직접 버퍼 사이즈 설정
		
		FileReader fr = null;
		FileWriter fw = null;

		BufferedReader br = null; // 버퍼드클래스 적용
		BufferedWriter bw = null; // 직접 만든 버퍼 달 필요 없음

		try {
			fr = new FileReader(source); // 객체생성
			fw = new FileWriter(target);

			br = new BufferedReader(fr);
			bw = new BufferedWriter(fw);
			while (true) {
				// int su = br.read();
				int su = br.read(cbuf, 0, cbuf.length);
				// cbuf배열 사이즈 단위로, 0번부터, 배열길이만큼 읽는다
				if (su == -1)
					break;
				// bw.write(su);
				// System.out.print((char) su); // 복사한 내용을 콘솔에 띄움
				bw.write(cbuf, 0, su);
				bw.newLine(); // 개행
				// bw.write("\n");
				String msg = new String(cbuf, 0, su);
				System.out.print(msg);
			}
			System.out.println("복사완료");
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		} finally {
			try {
				if (br != null)
					br.close();
				if (bw != null)
					bw.close();
				if (fr != null)
					fr.close();
				if (fw != null)
					fw.close();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

	}

}
```
