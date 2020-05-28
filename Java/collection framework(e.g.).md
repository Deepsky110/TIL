# Collection Framework - ArrayList, list

```java
package com.bit.day17;

// 도서 대여 프로그램
// 도서정보:
//		1. id
//		2. 제목
//		3. 저자
//		4. 대여가격
//		5. 현재상태(대여중 or 대여가능) >> 비교해서 없으면 대여 불가능
// 프로그램 기능
//		1. 대여
//		2. 반납
//		3. 각종 정보 출력
//			1. 대여중인 책 출력
//			2. 대여 가능한 책 출력
//			3. 전체 책 목록 출력
//		4. 생성자를 통해서 기본적으로 몇권의 책을 대여 가능 목록에 넣는다.

public class BookVO {

	private int id;
	private String title;
	private String author;
	private int price;

	public int getId() {
		return id;
	}

	public void setId(int id) {
		this.id = id;
	}

	public String getTitle() {
		return title;
	}

	public void setTitle(String title) {
		this.title = title;
	}

	public String getAuthor() {
		return author;
	}

	public void setAuthor(String author) {
		this.author = author;
	}

	public int getPrice() {
		return price;
	}

	public void setPrice(int price) {
		this.price = price;
	}

	@Override
	public String toString() {
		return "관리번호: " + id + ", 제목: " + title + ", 작가: " + author
				+ ", 가격: " + price + "]";
	}
	public boolean equals(Object o) { // 다형성 이용 - 어떤 클래스 객체라도 파라미터로 넣을 수 있다(뭐든지 받을 수 있다)
		if(o instanceof BookVO) { // 무엇이 bookVO의 객체인지 확인
			BookVO b = (BookVO)o;
			if(id == b.id) {
				return true;
			}
		}
		return false;
	}

}
```

```java
package com.bit.day17;

import java.util.ArrayList;
import java.util.List;

public class BookController {
	
	private List<BookVO> inventoryList; // 재고
	private List<BookVO> rentList; // 대여중
	public BookController(List<BookVO> inventoryList,  List<BookVO> rentList) {
		this.inventoryList = inventoryList; // 무슨 뜻이지
		this.rentList = rentList; 
	}
	
	// 리스트에서 해당하는 bookVO 객체와 같은 id를 가진 요소를 리턴하는 메서드
	public BookVO retrieveBookVO(List<BookVO> list, BookVO b) {
		int index = list.indexOf(b);
		return list.get(index);
	}

	// Viewer가 대여되는 책을 보내주면 객체를 inventoryList에서 rentList에 이동시키는 add 메서드
	public void rentBookVO(BookVO b) {
		rentList.add(retrieveBookVO(inventoryList, b));
		inventoryList.remove(b);
	}
	
	// Viewer가 반납하는 BookVO 객체를 rentList에서 inventoryList로 이동 시키는 메서드
	public void returnBookVO(BookVO b) {
		inventoryList.add(retrieveBookVO(rentList, b));
		rentList.remove(b);
	}
	
	// 해당 bookVO 객체가 대여 가능한지 검증(validate)하는 메서드 만들기
	public boolean validateRentBookVO(BookVO b) {
		return inventoryList.contains(b);
	}
	// 해당 bookVO 객체가 반납 가능한지 검증하는 메서드 만들기
	public boolean validateRetrunBookVO(BookVO b) {
		return rentList.contains(b);
	}
	
	// rentList와 inventoryList를 하나로 합쳐서 리턴하는 메서드
	public List<BookVO> selectAll() {
		List<BookVO> list = new ArrayList<BookVO>();
		list.addAll(inventoryList); // 해당 리스트의 모든 것을(All) 더해준다(add)
		list.addAll(rentList);
		return list;
	}
	
	public List<BookVO> selectInventory(){
		return inventoryList;
	}
	
	public List<BookVO> selectRent(){
		return rentList;
	}
	
	// private 정보를 바로 가져올 수 없어서 메서드를 통해 불러옴
	// 반납 가능한 책이 있는지 확인하는 메서드
	public boolean isRentEmpty() {
		return rentList.size() == 0;
	}
	
	// 대여 가능한 책이 있는지 확인하는 메서드
	public boolean isInventoryEmpty() {
		return inventoryList.size() == 0;
	}
}
```

```java
package com.bit.day17;

public class BookEx {

	public static void main(String[] args) {
		BookViewer viewer = new BookViewer();

	}

}
```

```java
package com.bit.day17;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class BookViewer {
	private BookController bookController;
	private Scanner scanner;

	public BookViewer() {

		scanner = new Scanner(System.in);
		ArrayList<BookVO> inventory = new ArrayList<>();
		BookVO b = new BookVO();
		b.setId(1);
		b.setTitle("JAVA의 정석");
		b.setAuthor("남궁성");
		b.setPrice(30000);
		inventory.add(b);

		b = new BookVO(); // 생성자를 새로 만들어 하나하나의 값을 대입
		b.setId(2);
		b.setTitle("슬램덩크");
		b.setAuthor("일본인A");
		b.setPrice(10000);
		inventory.add(b);

		b = new BookVO();
		b.setId(3);
		b.setTitle("명탐정 코난");
		b.setAuthor("일본인B");
		b.setPrice(6000);
		inventory.add(b);

		b = new BookVO();
		b.setId(4);
		b.setTitle("귀멸의 칼날");
		b.setAuthor("일본인C");
		b.setPrice(7000);
		inventory.add(b);

		ArrayList<BookVO> rent = new ArrayList<>();
		bookController = new BookController(inventory, rent);
		showMenu();
	}

	private void showMenu() {
		while (true) {
			System.out.println("====================");
			System.out.println("ABC 도서대여점");
			System.out.println("====================");
			System.out.print("1.대여 2.반납 3.출력 4.종료 >> ");
			int choice = scanner.nextInt();
			scanner.nextLine();
			if(choice == 1) {
				// 대여하는 메서드 호출
				rentBook();
			}else if(choice == 2) {
				// 반납하는 메서드 호출
				returnBook();
			}else if(choice == 3) {
				// 출력하는 메서드 호출
				printList();
			}else if(choice == 4) {
				System.out.println("사용해주셔서 감사합니다.");
				break;
			}else{
				System.out.println("잘못 입력하셨습니다.");
			}
		}
	}
	
	private void printList() {
		// 출력시에는
		// 대여 가능, 반납 가능, 모든 목록 - 3가지 목록을 출력해야 한다.
		System.out.println("출력할 목록을 선태개주세요.");
		System.out.print("1.대여 가능 2.반납 가능 3.모든 도서 >> ");
		int choice = scanner.nextInt();
		List<BookVO> selectedList = null;
		if(choice == 1) {
			selectedList = bookController.selectInventory();
		} else if(choice == 2) {
			selectedList = bookController.selectRent();
		} else if(choice == 3) {
			selectedList = bookController.selectAll();
		} else {
			System.out.println("잘못 입력하셨습니다.");
		}
		if(selectedList != null) {
			System.out.println("==========================");
			for(BookVO b : selectedList) {
				System.out.println(b);
			}
			System.out.println("==========================");
		}
	}
	
	private void returnBook() {
		// 반납 가능한 목록이 있는지 체크한다.
		if(bookController.isRentEmpty()) {
			System.out.println("반납 가능한 도서가 없습니다.");
		} else {
			System.out.println("======반납 가능 목록======");
			for(BookVO b : bookController.selectRent()) {
				System.out.println(b);
			}
			System.out.println("==========================");
			System.out.print("반납할 책의 식별번호를 입력해주세요 >> ");
			int id = scanner.nextInt();
			BookVO b = new BookVO();
			b.setId(id);
			while(!bookController.validateRetrunBookVO(b)) {
				System.out.println("잘못 선택하셨습니다.");
				System.out.println("반납할 책의 식별번호를 입력해주세요 >> ");
				id = scanner.nextInt();
				b.setId(id);
			}
			bookController.returnBookVO(b);
		}
	}
	private void rentBook() {
		// 대여 가능한 리스트를 출력한다.
		if(bookController.isInventoryEmpty()) {
			System.out.println("대여 가능한 도서가 없습니다");
		} else {
			System.out.println("======대여 가능 목록======");
			for(BookVO b : bookController.selectInventory()) { // 향상된 for문
				System.out.println(b);
			}
			System.out.println("==========================");
			// 사용자로부터 대여하고자 하는 책의 id(관리번호)를 입력받는다.
			System.out.print("대여할 책의 식별번호를 입력해주세요 >> ");
			int id = scanner.nextInt();
			BookVO b = new BookVO();
			b.setId(id);
			while(!bookController.validateRentBookVO(b)) { // 결과가 false라면 (!)
				System.out.println("잘못 선택하셨습니다.");
				System.out.print("대여할 책의 식별번호를 입력해주세요 >> ");
				id = scanner.nextInt();
				b.setId(id);	
			}
			bookController.rentBookVO(b);
		}
	}
}
```
