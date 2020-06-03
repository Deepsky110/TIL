# I/O

```java
package com.bit.day21;

import java.io.IOException;
import java.util.Arrays;

public class Ex01 {

	public static void main(String[] args) {
		// i.o
		// File
		
//		* path를 지정하는 방법
//		절대경로 (C: 와 같이 최상위 디렉토리에서 내려옴)
//		String path = "C:\\javaWorkspace\\Day21\\test"; // 없는 파일
//		String path = "C:\\javaWorkspace\\day21";
//		String path = "C:\\javaWorkspace\\day21\\test01.txt";
		
//		상대경로 (내 위치를 기준으로 ./..으로 움직임)
//		String path = "src"; // ".\\src" 현재(.)를 기준으로 아래(\\)에 src가 있다
//		String path = "test01.txt";
//		String path = ".\\test01.txt";
		String path = "."; // 현재
//		String path = ".."; // 상위 디렉토리
//		String path = "..\\day21\\test01.txt";
		
		java.io.File file = new java.io.File(path);

		// ()가로 안에 비우면 에러 : 디폴트 생성자가 없어서
		// 자바 문법에서 \는 문자와 합쳐져 기능을 가진다 => \\로 대체
		// 경로상 없는 파일을 써도 에러가 안난다 => 파일이 존재하는지 먼저 테스트
		
		System.out.println("존재하는가? " + file.exists()); // T/F
		System.out.println("파일인가? " + file.isFile());
		System.out.println("디렉토리인가? " + file.isDirectory());
		System.out.println("이름은? " + file.getName());
		System.out.println("경로는? " + file.getPath());
		System.out.println("단순 절대경로는? " + file.getAbsolutePath());
		try {
			System.out.println("일반 절대경로는? " + file.getCanonicalPath());
		} catch (IOException e) {
			e.printStackTrace();
		}
		System.out.println("Path는? " + file.getParent()); // 상위 경로까지 표시
		
		System.out.println("rxw r읽기권한? " + file.canRead()); // T/F
		System.out.println("rwx w쓰기권한? " + file.canWrite()); 
		System.out.println("rwx x실행권한? " + file.canExecute());
		System.out.println("size? " + file.length()+"byte"); // 파일 크기
		System.out.println("최종 수정시간 ? " + new java.util.Date(file.lastModified()));

		// 구성 파일 출력 방법 두 가지
		// (1)
		String[] dirs = file.list();
		for(int i = 0; i < dirs.length; i++) {
			System.out.println(dirs[i]);
		}
		// (2)
		System.out.println(Arrays.toString(dirs)); // import 필요
	}

}
```

<br>

### 파일 생성하기
```java
package com.bit.day21;

import java.io.File;
import java.io.IOException;

public class Ex03 {
// 파일 생성하기
	public static void main(String[] args) {
		String path = ".\\test02.txt";
		File file = new File(path);
		try {
			if(file.createNewFile()) {
				System.out.println("파일을 생성했습니다");
			} else {
				System.out.println("기존 파일이 존재합니다");
			} // 새로운 파일 만들기
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

}
```

<br>

### 파일 삭제하기

```java
package com.bit.day21;

import java.io.File;

public class Ex04 {
// 파일 삭제하기
	public static void main(String[] args) {
		String path = ".\\test02.txt";
		File file = new File(path);
		
		if(file.delete()) {
			System.out.println("파일을 삭제했습니다");
		} else {
			System.out.println("파일이 존재하지 않습니다");
		}
		

	}

}
```

<br>

### 파일 이름 수정하기

```java
package com.bit.day21;

import java.io.File;

public class Ex05 {
// 파일 이름 수정하기
	public static void main(String[] args) {
		String path = ".\\test02.txt";
		File file = new File(path);
		
		String rename = ".\\test03.txt";
		File file2 = new File(rename);
		
		file.renameTo(file2);
	}

}
```

<br>

### 임시저장 기능

```java
package com.bit.day21;

import java.io.File;
import java.io.IOException;

public class Ex06 {
// 임시적인 저장 기능 (temp 폴더에 임시파일 생성)
	public static void main(String[] args) {
		String prefix = "AABBCCDDEEFFGG"; // 찾을 파일명
		String suffix = ".txt"; // 찾을 파일의 확장자
		try {
			File file = File.createTempFile(prefix, suffix);
			System.out.println(file.getParent());
		} catch (IOException e) {
			e.printStackTrace();
		} // C:\Users\Bitcamp\AppData\Local\Temp 경로에 생성(숨긴폴더)

	}

}
```

<br>

### 디렉토리 폴더 만들기
```java
package com.bit.day21;

import java.io.File;

public class Ex07 {

	public static void main(String[] args) {
		String path = "test\\ex";
		File file = new File(path);
//		file.mkdir(); // test라는 디렉토리(폴더) 만들기
//		boolean result = file.delete();
//		System.out.println(result);
		file.mkdirs(); // test아래 ex까지 만들기

	}

}
```
