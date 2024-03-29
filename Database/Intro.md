# 데이터베이스 개요

## table of contents
1. [데이터베이스의 역사](#데이터베이스의-역사)
1. [데이터베이스의 등장](#데이터베이스의-등장)
1. [데이터베이스의 특징](#데이터베이스의-특징)


## 데이터베이스의 역사
컴퓨터 발전사의 역사는 데이터 처리의 발전사와 맥을 함께 하였다. 1세대 컴퓨터 시스템들은 소프트웨어나 저장장치 등의 개발이 부족한 까닭에 주로 기술 분야의 계산, 자료 분류 등에 사용되었다. 운영체제가 도입되고 FORTRAN 같은 프로그래밍 언어를 사용하는 2세대 컴퓨터 시스템이 등장하면서 자료를 분석하고 처리하는 일에 컴퓨터 시스템이 본격적으로 사용되기 시작하였다.

### 파일 시스템의 등장과 문제점
2세대 컴퓨터 시스템이 등장하면서 도입된 파일(File) 개념은 자료를 저장하는 기본적인 방법으로 사용되었으며 오늘날까지 이용되고 있다. 이러한 파일에 기초하여 자료나 정보를 처리하는 시스템을 파일 시스템이라고 부르는데, 파일 시스템에서는 개별 응용 프로그램이 직접 파일에 접근하여 기록, 갱신, 삭제를 할 수 있으며, 파일에 있는 데이터의 올바른 관리 여부는 전적으로 응용 프로그램에 달린다.

파일에 기초한 정보 시스템에서 데이터의 급속한 증가는 하드웨어나 소프트웨어의 성능 향상에도 불구하고, 다음과 같은 문제들이 드러난다.

- 데이터 종속성: 데이터를 사용하는 프로그램의 구조가 데이터 구조의 영향을 받는다는 것을 의미
- 데이터 무결성: 저장된 데이터 내용이 본래 의도했던 데이터의 형식, 범위를 준수해야 한다는 성질
- 데이터 중복성: 같은 내용의 데이터가 여러 곳에 중복하여 저장되는 것을 의미
- 데이터 불일치: 중복 저장된 데이터들이 서로 일치하지 않는 것을 의미
- 데이터 표준화의 어려움: 표준화된 규칙이 있더라도 응용 프로그래머가 이를 지키지 않을 수 있는 여지
- 데이터 보안성의 결여: 파일은 응용 프로그램이 없더라도 쉽게 그 내용을 열어볼 수 있고, 공유를 위한 접근이 쉬우므로 보안을 유지하기 어려움

## 데이터베이스의 등장
파일 시스템의 단점을 극복하고, 다수의 사용자들이 정보를 공유하기 위해 데이터베이스가 등장했다. 데이터베이스는 **파일 형태로 흩어져 있는 데이터, 정보들을 하나로 모아 관리**하고, **응용 프로그램들이 운영체제를 통해 시스템 자원을 이용하는 것처럼 모아놓은 데이터들을 관리하고 사용자와 데이터 사이에 인터페이스 역할**을 하는 S/W이다. 

모아놓은 데이터의 집합을 데이터베이스, 데이터를 관리하는 S/W를 DBMS라고 한다. 

## 데이터베이스의 특징
데이터베이스 시스템은 파일 시스템에 비해 다음과 같은 특징을 갖는다.
- 데이터 독립성
- 데이터 무결성
- 데이터 중복성 및 불일치 최소화
- 데이터 표준화와 용이성
- 높은 데이터 보안성
- 데이터 공유의 용이성
