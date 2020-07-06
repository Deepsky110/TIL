# Data modeling

### 1. 데이터 모델링

- 데이터 모델링은 현실세계를 데이터베이스로 표현하기 위해서 추상화한다.
- 고객과의 의사소통을 통해 고객의 업무 프로세스를 이해해야 한다.
- 고객의 업무프로세스를 데이터 모델링 표기법을 사용해서 모델링 한다.
- 복잡하지 않도록 해서 고객이 쉽게 이해할 수 있어야 한다.
- 고객의 업무 프로세스를 추상화하고, 소프트웨어가 분석, 설계 하면서 점점 더 상세해진다.
- 고객의 비즈니스 프로세스를 이해하고 비즈니스 프로세스의 규칙을 정의한다.
- 정의된 비즈니스 규칙을 데이터 모델로 표현한다.

[2. 데이터 모델링의 특징](https://www.notion.so/1835f3b398374340a7213cc0400a1280)

### 3. 데이터 모델링 단계

- 데이터 모델링은 개념적 모델링, 논리적 모델링, 물리적 모델링 단계로 이루어진다.

(1) 개념적 모델링(Conceptual Data Modeling)

- 기업의 비즈니스 프로세스를 분석하고 기업 전체에 대해서 데이터 모델리응 룻행한다.
- 잡하게 표현하지 않고 중요한 부분을 위주로 모델링 하는 단계이다.
- 업무관점에서 모델링하며 기술적 용어 사용은 지양한다.
- 엔티티(Entitiy)와 속성(Attribute)을 도출하고

    개념적 ERD(Entity Relationship Diagram)를 작성한다.

(2) 논리적 모델링(Logical Data Modeling)

- 개념적 모델링을 논리적 모델링으로 변환하는 작업이다.
- 식별자를 도출하고 필요한 모든 릴레이션을 정의한다.
- 정규화를 수행해서 데이터 모델의 독립성을 확보한다.

(3) 물리적 모델링(Physical Modeling)

- 데이터베이스를 실제 구축한다. 즉, 테이블, 인덱스, 함수 등을 생성한다.
- 성능, 보안, 가용성을 고려해서 구축한다.

[데이터 모델링 단계](https://www.notion.so/a55208e3639840ddb0f3adf95171dc26)

[데이터 모델링 관점](https://www.notion.so/e874ca54c61f4fc890f4bbcd3c68291a)


## 데이터 모델링을 위한 ERD(Entity Relation ship Diagram)

- 1976년 피터첸(Peter Chen)이 Entity Relationship Model 표기법을 만들었으며 데이터 모델링의 사실상 표준으로 사용되고 있다.
- 엔티티(Entity)와 엔티티 간의 관계를 정의하는 모델링 방법

(1) ERD 작성절차

① 엔티티를 도출하고 그린다

- 업무에서 관리해야 하는 집합을 도출한다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2427b42b-4596-4ddb-8462-fdafc47deee1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2427b42b-4596-4ddb-8462-fdafc47deee1/Untitled.png)

② 엔티티를 배치한다

- 엔티티를 도출하면 엔티티를 배치한다.
- 엔티티 배치는 중요한 엔티티를 왼쪽 상단에 배치

③ 엔티티 간의 관계를 설정한다

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/268f594c-44d2-460b-bc01-d01fdbe961dc/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/268f594c-44d2-460b-bc01-d01fdbe961dc/Untitled.png)

④ 관계명을 서술한다

- 엔티티 간에 어떤 행위나 존재가 있는지 표현한다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3beb3dad-69fb-4337-af5c-4a3d95cf7c5d/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3beb3dad-69fb-4337-af5c-4a3d95cf7c5d/Untitled.png)

⑤ 관계 참여도를 표현한다

- 관계 참여도는 한 개의 엔티티와 다른 엔티티 간의 참여하는 관계 수를 의미
- e.g. '고객이 여러 개의 계좌를 개설할 수 있다.'

⑥ 관계의 필수 여부를 표현한다

- 필수는 반드시 존재해야 한다
- e.g. '모든 고객은 반드시 하나의 계좌는 개설해야 한다.'

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/20281bde-bfbd-4eea-a652-94025949ab86/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/20281bde-bfbd-4eea-a652-94025949ab86/Untitled.png)

(2)  ERD 작성 시 고려사항

- 중요한 엔티티를 가급적 왼쪽 상단에 배치
- ERD는 이해가 쉬워야 하고 너무 복잡하지 않아야 한다.

## 데이터 모델링 고려사항

(1) 데이터 모델의 독립성

- 독립성이 확보된 모델은 고객의 업무 변화에 능동적으로 대응할 수 있다.
- 독립성을 확보하기 위해서는 중복된 데이터를 제거해야 한다.
- 데이터 중복을 제거하는 방법이 바로 정규화이다.

(2) 고객 요구사항의 표현

- 고객의 요구사항을 너무 복잡하지 않게 표현해야 한다.
- 데이터 모델링으로 고객과 데이터 모델러 간에 의사소통을 할 수 있어야 한다.
- 요구사항을 간결하고 명확하게 표현

(3) 데이터 품질 확보

- 데이터베이스 구축 시에 데이터 표준을 정의하고 표준 준수율을 관리해야 한다.
- 데이터 표준을 확보해야 데이터 품질을 향상시킬 수 있다.

# 3층 스키마(3-Level Schema)

## 1. 3층 스키마

- 사용자, 설계자, 개발자가 데이터베이스를 보는 관점에 따라 데이터베이스를 기술하고 이들 간의 관계를 정의한  ANSI  표준
- 데이터베이스의 독립성을 확보하기 위한 방법
- 데이터의 독립성을 확보하면 데이터 복잡도 증가, 데이터 중복 제거, 사용자 요구사항 변경에 따른 대응력 향상, 관리 및 유지보수 비용 절감 등의 장점을 갖는다.
- 3층 스키마의 독립성
    - 논리적 독립성 : 저장구조가 변경되어도 응용 프로그램 및 개념 스키마에 영향이 없다
    - 물리적 독립성 : 데이터베이스 논리적 구조가 변경되어도 응용 프로그램에 변화가 없다.

## 2. 3층 스키마 구조

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ea75c6ae-df1e-410f-a191-a78668b2e1a3/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ea75c6ae-df1e-410f-a191-a78668b2e1a3/Untitled.png)

- 3층 스키마의 구조
    - 외부 스키마(External Schema)
        - 사용자 관점, 업무상 관련 있는 데이터 접근
        - 관련 데이터베이스의 뷰(View)를 표시
        - **응용 프로그램이 접근하는 데이터베이스** 정의
    - 개념 스키마(Conceptual Schema)
        - 설계자 관점, 사용자 전체 집단의 데이터베이스 구조
        - 전체 데이터베이스 내의 규칙과 구조 표현
        - **통합 데이터베이스 구조**
    - 내부 스키마(Internal Schema)
        - 개발자 관점, 데이터베이스의 **물리적 저장구조**
        - 데이터 저장구조, 레코드 구조, 필드 정의, 인덱스 등을 의미

## 엔티티(Entitiy)

## 1. 엔티티(Entity)

- 엔티티는 업무에서 관리해야 하는 데이터 집합을 의미
- 저장되고 관리되어야 하는 데이터
- 개념, 사건, 장소 등의 명사
- 데이터 베이스 내부에서 변별 가능한 객체

## 2. 엔티티(Entity) 도출

- 엔티티는 고객의  비즈니스 프로세스에서 관리되어야 하는 정보를 추출해아 한다

## 3. 엔티티(Entity) 특징

1) 식별자

- 엔티티는 **유일한 식별자**가 있어야 한다
- e.g. 회원ID, 계좌번호

2) 인스턴스 집합

- **2개 이상의 인스턴스**가 있어야 한다

3) 속성

- **반드시 속성**을 가지고 있다
- e.g. 회원ID, 패스워드, 이름, 주소, 전화번호

4) 관계

- **다른 엔티티와 최소 한 개 이상 관계**가 있어야 한다
- e.g. 고객은 계좌를 개설한다

5) 업무

- **업무에서  관리되어야 하는 집합**이다
- e.g. 고객, 계좌
