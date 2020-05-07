# 1 식별자와 예약어

**식별자** : 자바에서 식별자는 클래스, 인터페이스, 변수, 메소드, 배열, 문자열을 구분할 수 있는 이름  

- 식별자의 사용 원칙
	- 자바에서 식별자는 문자로 시작한다. 숫자는 사용할 수 없다.
	- 예약어를 식별자로 사용할 수 없다.
	- 식별자는 길이에 제한을 두지 않는다. 단 space를 사용할 시 문장이 끝난 것으로 인식한다.
	- 같은 문자의 대소문자는 서로 다른 문자로 인식한다.
	- 암묵적으로 class 이름의 첫 글자는 대문자를 사용한다.
	- 메소드, 변수, 배열, 문자열 이름의 첫 글자는 소문자를 사용한다.  
<br>

- 예약어의 종류  

|분류|예약어|
|:---|:---|
|기본 데이터 타입|boolean, byte, char, short, int, long, float, double|
|접근 지정자|private, protected, public|
|클래스 관련|class, abstract, interface, extends, implements, enum|
|메소드 관련|void, return|
|제어문 관련|if, else, switch, case, default, for, do, while, break, continue|
|논리 리터널|true, false|
|예외 처리 관련|try, catch, finally, throw, throws|
|기타|transient, volatile, package, import, synchronized, native, final, static, strictfp, assert|  
<br>

# 2 변수의 의미

값이나 데이터 을 저장하기 위한 메모리공간  
하나의 변수는 하나의 자료형만 지정할 수 있고  
값을 저장 하고 조회 변경 등을 할 수 있다.  
