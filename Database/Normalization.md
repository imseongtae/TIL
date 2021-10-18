# 정규화

## table of contents
1. [정규화 개념](#정규화-개념)
1. [정규화의 등장 배경](#정규화의-등장-배경)
1. [제 1정규화](#제-1정규화)
1. [제 2정규화](#제-2정규화)
1. [제 3정규화](#제-3정규화)
1. [Reference](#reference)

---


## 정규화 개념
관계형 데이터베이스 모델의 기본 정신은 동일한 정보는 한 곳에서만 관리하는 것이다. 동일한 정보가 여러 곳에 중복해 존재하면 중복된 정보들 사이의 불일치가 발생하게 된다. 이러한 측면에서 **정규화(normalization)는 ERD내에서 중복을 찾아 제거해 나가는 과정을 말한다.** 

### 정규화에 대한 다른 설명

```bash
관계형 데이터베이스에서 중복을 최소화하기 위해 데이터를 구조화하는 작업입니다. 
좀 더 구체적으로는 불만족스러운 나쁜 릴레이션의 애트리뷰트들을 나누어서 더 작은 '좋은' 릴레이션으로 분해하는 작업을 말합니다. 
정규화 과정을 거치게 되면 정규형을 만족하게 됩니다. 정규형이란 특정 조건을 만족하는 릴레이션의 스키마의 형태를 말하며
제 1 정규형, 제 2 정규형, 제 3 정규형 등이 존재합니다.
# by 한재엽님
```



## 정규화의 등장 배경

오늘날 정보시스템을 구축하거나 웹사이트를 개발할 때 데이터베이스를 떼어놓고 생각하기 어렵다. 데이터베이스 기반으로 시스템을 개발하기 위해 데이터베이스 설계가 필요하다. 데이터베이스 설계를 위해선 컴퓨터로 관리해야 할 정보를 구분하고, 관리되어야 하는 정보를 명확하게 규정해야 하는데, 현실 세계를 소프트웨어적으로 더 잘 반영한 개념적 모델을 만들기 위해 정규화가 등장한다.

### 정규화가 필요한 예
예를 들면, 하나의 릴레이션에 여러 엔티티의 애트리뷰트들을 혼합하면 정보가 중복 저장되고, 저장 공간을 낭비하게 된다. 그리고 중복된 정보로 인해 **갱신 이상**이 발생하게 된다. 동일한 정보를 한 릴레이션에는 변경하고, 나머지 릴레이션에는 변경하지 않은 경우 어느 것이 정확한지 알 수 없게 된다. 이러한 문제를 해결하기 위해 정규화 과정을 거친다. 

#### 갱신 이상의 종류
- 삽입 이상: 새 데이터를 삽입하기 위해 불필요한 데이터까지 함께 삽입해야 해야 하는 문제
- 삭제 이상: 튜플을 삭제하면 꼭 필요한 데이터까지 함께 삭제되는 데이터 손실의 문제
- 수정(갱신) 이상: (중복된 속성을 가진 튜플 중)일부의 튜플만 갱신되어 데이터가 불일치하게 되는 모순의 문제

### 정규화는 꼭 해야만 할까?
모델링에 익숙해진다면 정규화 과정을 거치지 않는다. 왜냐하면 몇 가지 원칙만 잘 지킨다면 정규화를 할 필요가 없도록 ERD를 작성할 수 있기 때문이다. 이론적으로 정규화는 5차 정규화까지 있지만 3차 정규화까지만 알아도 큰 문제가 없다.
3차 정규화 이상이 필요한 사례는 모델링 과정에서 접하기 어렵다. 
3차 정규화까지의 기법을 숙지하고, 이를 모델링에 능숙하게 활용할 수 있다면 정규화할 필요가 없는 ERD를 작성할 수 있다.

---


## 정규화를 이해하기 배경지식
데이터베이스 설계는 정보시스템을 구축하기 위한 절차 가운데 설계 부분에 해당한다. 그리고 데이터베이스 설계 부분에는 정규화와 관계가 깊은 데이터 모델링이 있다.

![Information system design process](https://user-images.githubusercontent.com/60806840/137804109-792c126b-6f9a-4a22-a181-10f70ebd3ad4.png)

### 데이터베이스 설계
데이터베이스 설계란 데이터베이스 안에 **어떤 테이블들이 있어야 하고, 각 테이블들은 어떤 컬럼이 있어야 하며, 기본기와 외래키는 어떤 것인지 정하고**, 응용프로그램에서 필요로하는 뷰와 인덱스를 생성하는 일련의 과정을 말한다. 
데이터베이스 설계는 단순히 단순히 데이터베이스 안에 테이블을 생성하는 과정뿐만 아니라 현실세계에 대한 분석, **논리적 설계(데이터 모델링)**, 물리적 설계, 데이터베이스 구축에 이르는 전과정을 포함한다.

### 데이터 모델링:논리적 데이터베이스 설계
현실세계를 관찰하여 컴퓨터로 관리해야 할 정보, 혹은 데이터를 찾는 것이 데이터 모델링이다. 데이터 모델링의 산출물인 ERD는 현실세계를 '데이터의 관점'에서 관찰하여 어떤 정보들이 관리되어야 하는지 표현한 결과이다. 

**즉 데이터 모델링이란 현실세계를 관찰, 분석하여 ERD로 불리는 개념적 모델을 만드는 과정**

![Database design](https://user-images.githubusercontent.com/60806840/137804151-8c3a3f79-a631-440e-b19a-96dd4241011f.png)

### ERD
데이터 모델링에서는 ERD라는 수단을 통해 모델링을 하고, 모델링의 결과를 표현한다.  
'Entity-Relationship Diagram'라는 용어에서도 알 수 있듯이 데이터 모델링에서 핵심은 엔티티를 도출하는 일이다. 

### 엔티티
엔티티란 업무의 관심 대상이 되는 정보를 갖고 있거나, 그에 대한 정보를 관리할 필요가 있는 유형, 무형의 사물(개체)을 의미한다. 엔티티의 예로 학생, 개설과목, 수강신청서 등을 들 수 있다.

### 함수적 종속성(FD: Functional Dependency)
함수적 종속성은 **좋은 릴레이션 설계의 정형적 기준**으로 사용되며, 데이터 애트리뷰트의 의미와 애트리뷰트간의 상호 관계로부터 유도되는 제약조건의 일종이다. FD와 키는 릴레이션의 정규형을 정의하기 위해 사용된다. 

> X → Y

X와 Y를 임의의 애트리뷰트 집합이라고 할 때, X의 값이 Y의 값을 유일하게 결정한다면 'X는 Y를 함수적으로 결정한다'고 한다

- X는 결정자, Y는 종속자라고 표현
- X는 Y를 함수적으로 결정
- Y는 X에 함수적으로 종속


---


## 제 1정규화
제 1정규화(1NF: First Normal Form)는 속성에 중복된 값이 저장되는 경우나 엔티티에 반복 속성이 존재하는 경우 이를 제거해 나가는 과정이다. 다시 말하면 엔티티(개체)에서 하나의 속성이 복수의 값을 갖도록 설계되었을 때, 하나의 속성이 단일 값(atomic value)을 갖도록 하는 것이다.

### 제 1정규화 예시
사원의 취미를 관리하는 엔티티를 예시로 들면, 한 명의 사원은 여러 개의 취미를 가질 수 있다. 

| 사원번호(PK) | 취미             |
| ------------ | ---------------- |
| 1001         | 등산<br />낚시   |
| 1002         | 테니스<br />등산 |
| 1003         | 볼링             |

위의 예시에서 취미 속성에 복수 개의 값들이 저장된 것을 확인할 수 있는데, 복수의 값이 한 속성에 저장되면 각각의 값들을 구분하기 어려우므로 정규화가 필요하다. 

| 사원번호(PK) | 취미1  | 취미2 | 취미3 |
| ------------ | ------ | ----- | ----- |
| 1001         | 등산   | 낚시  |       |
| 1002         | 테니스 | 등산  |       |
| 1003         | 볼링   |       |       |

위의 예시 또한 데이터가 저장되지 않은 빈 곳이 발생할 수 있고, 취미가 세 가지 이상인 사람이 나타나면 속성을 더 늘려야 하는 문제가 발생한다. 

아래처럼 수정하는 과정을 제 1정규화라고 한다.


| 사원번호(PK) | 취미(PK) |
| ------------ | -------- |
| 1001         | 등산     |
| 1001         | 낚시     |
| 1002         | 테니스   |
| 1002         | 등산     |
| 1003         | 볼링     |

---


## 제 2정규화
제 2정규화(2NF: Second Normal Form)는 주식별자가 아닌 속성 중에서 주식별자 전체가 아닌 일부 속성에 종속된 속성을 찾아 제거하는 과정이다. 여기서 제거란 다른 엔티티를 만들어 속성을 옮기는 것을 말한다.

다시 말하면, **제 2정규화는 주식별자가 아닌 속성들 중 주식별자의 '일부' 속성에 중복된 속성들을 제거하는 과정**이다.

### 제 2정규화에 대한 다른 설명

```bash
어떤 릴레이션 R이 제1정규화에 속하고
기본키에 속하지 않는 모든 속성이 키본키에 완전 함수적 종속이면 충족하는 정규화
# 정규화Normalization-개념과-기본-과정 by IT 정보기술 따라잡기!

모든 비주요 애트리뷰트들이 주요 애트리뷰트에 대해서 완전 함수적 종속이면 제 2정규형을 만족한다고 볼 수 있습니다. 완전 함수적 종속이란 X -> Y 라고 가정했을 때, X 의 어떠한 애트리뷰트라도 제거하면 더 이상 함수적 종속성이 성립하지 않는 경우를 말합니다.
# Database : 데이터베이스 참조 by splin
```

### 제 2정규화 예시

#### 제 2정규화 적용 전
![Before 2NF](https://user-images.githubusercontent.com/60806840/137789504-acc609a4-b636-4353-9ccc-9f2a27a091b5.png)

#### 제 2정규화 적용 후
![After 2NF](https://user-images.githubusercontent.com/60806840/137789522-d1484f4f-3a27-40c0-aed4-f49e2846ced9.png)

---


## 제 3정규화
제 3정규화(3NF: Third Normal Form)는 주식별자가 아닌 속성들 사이에 종속관계가 있을 때 이를 제거하는 과정이다.

```bash
어떤 릴레이션 R이 제 2정규화에 있으며 기본키에 속하지 않는 모든 속성이
기본키에 이행적 함수 종속이 아닌 상태의 관계를 말한다
# 정규화Normalization-개념과-기본-과정 by IT 정보기술 따라잡기!

어떠한 비주요 애트리뷰트도 기본키에 대해서 이행적으로 종속되지 않으면 제 3 정규형을 만족한다고 볼 수 있습니다.
이행 함수적 종속이란 X - >Y, Y -> Z의 경우에 의해서 추론될 수 있는 X -> Z의 종속관계를 말합니다. 
즉, 비주요 애트리뷰트가 비주요 애트리뷰트에 의해 종속되는 경우가 없는 릴레이션 형태를 말합니다.
# Database : 데이터베이스 참조 by splin
```

### 제 3정규화 예시

![IMG_5048 1](https://user-images.githubusercontent.com/60806840/137326523-bf293f9f-712d-4582-8314-c2e709309e02.png)

---


## Reference
- [Database : 데이터베이스](https://dev-splin.github.io/cs(computer%20science)/database/Database-Database(Total)/)
- 데이터베이스 설계 및 구축(오세종 저)
- [데이터베이스 정규화 - 이상현상 & 함수적 종속성](https://yaboong.github.io/database/2018/03/09/database-anomaly-and-functional-dependency/)
- [관계 데이터베이스의 함수적 종속성과 정규화](http://cs.kangwon.ac.kr/~ysmoon/courses/2009_2/db/11.pdf)
- [정규화(Normalization) 개념과 정규화 과정(1NF, 2NF, 3NF, BCNF)](https://minimax95.tistory.com/entry/%EC%A0%95%EA%B7%9C%ED%99%94Normalization-%EA%B0%9C%EB%85%90%EA%B3%BC-%EA%B8%B0%EB%B3%B8-%EA%B3%BC%EC%A0%95)