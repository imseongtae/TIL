# AWS



## Table of Contents

1. [Regions](#Regions)
1. [Availability Zone](#Availability-Zone)
1. [VPC](#VPC)
1. [Subnet](#Subnet)
1. [EC2](#EC2)
1. [Elastic Load Balancing](#Elastic-Load-Balancing)
1. [S3](#S3)
1. [CloudFront](#CloudFront)
1. [IAM](#IAM)
1. [API Gateway](#API-Gateway)
1. [참고문헌](#참고문헌)

---



## Regions

리전은 AWS에서 운영되는 서버의 물리적 위치를 의미한다. 여러 개의 리전을 두는 이유는 네트워크 속도 때문인데, 전 세계의 주요 지역에 리전을 위치시키고, 가까운 리전으로 접속해서 빠른 속도를 낼 수 있다. 



## Availability Zone

`Availability Zone`은 리전내에 있는 IDC(데이터 센터)를 의미한다. 각 가용 영역은 하나 이상의 데이터 센터로 구성되지만, 하나의 데이터 센터가 2개의 가용 영역에 포함될 수는 없다.

각 가용 영역은 독립된 장애 영역으로 설계되었으므로 가용 영역은 일반적인 대도시 리전 내에서 물리적으로 격리되어 있으며, 별도의 무정전 전원 공급 장치와 현장 백업 발전 시설 외에도 독립적인 유틸리티의 서로 다른 그리드를 통해 전력을 공급받음으로써 단일 장애 지점이 더욱 줄어들게 된다.

## VPC

`Amazon Virtual Cloud`는 논리적으로 격리된 **가상 네트워크**를 생성할 수 있는 웹 서비스이다. IP주소의 범위 선택, 퍼블릭 서브넷, 프라이빗 서브넷 등을 생성할 수 있다. 라우팅 테이블 및 네트워크 게이트웨이 구성 등 가상 네트워킹 환경을 구성할 수 있다. VPC에서 IPv4와 IPv6 모두 사용이 가능하다. 이를 통해 안전하게 **AWS내에 구성된 서버 간의 안전하고 쉬운 액세스**가 가능하다. 



## Subnet

서브넷은 **VPC의 IP 주소 범위**이다. 지정된 서브넷으로 AWS 리소스를 시작할 수 있으며, 인터넷에 연결되어야 하는 리소스에는 **퍼블릭 서브넷**을 사용하고, 인터넷에 연결되지 않는 리소스에는 **프라이빗 서브넷**을 사용한다.

예를 들어 Network Address Translation(NAT)를 사용하여 인터넷에서 주소로 직접 액세스하지 못하게 할 인스턴스에 대해서는 프라이빗 서브넷을 사용한다. 프라이빗 서브넷에 있는 인스턴스는 퍼블릭 서브넷의 NAT 게이트웨이를 통해 트래픽을 라우팅하여 프라이빗 IP 주소를 노출하지 않고 인터넷에 액세스할 수 있다.

**[⬆ back to top](#table-of-contents)**



## EC2

Amazon Elastic Compute Cloud(Amazon EC2)는 가상 서버를 필요한 만큼 비용을 지불하고 임대해서 사용하는 서비스이다. 애플리케이션의 부하나 규모에 따라 유동적으로 서버의 대수를 조절하면서 사용할 수 있다. 

## Elastic Load Balancing

`Elastic Load Balancing(ELB)`는 들어오는 애플리케이션 트래픽을 Amazon EC2 인스턴스, 컨테이너, IP 주소와 같은 여러 대상에 자동으로 분산시킨다. ELB는 단일 AZ(Availability Zone) 또는 여러 AZ에서 다양한 애플리케이션 부하를 처리하므로 내결함성과 가용성을 향상한다.





## S3

Simple Storage Service는 인터넷용 스토리지 서비스이다.

## CloudFront

전세계의 사용자에게 빠른 전송 속도로 동영상, 데이터, 애플리케이션 및 API를 전송하는 **고속 콘텐츠 네트워크(CDN)** 서비스이다. `CloudFront`를 통해 전송 속도의 향상과 비용절감 효과를 누릴 수 있다. `CloudFront`를 사용하면 사용자는 자신의 위치와 가까운 서비스 서버가  캐싱되어 있는 에지 로케이션으로 연결되어 콘텐츠를 이용하게 된다.

## IAM 

사용자와 그룹을 생성하고 AWS 서비스와 리소스에 대한 액세스를 허용 거부할 수 있다. 이를 통해 접근 권한 때문에 발생하는 사고를 미연에 방지할 수 있다. 

## API Gateway

`REST API` 및 `Websock API`를 생성, 게시, 유지 관리 모니터링, 보안 등을 할 수 있는 AWS 서비스 이다. `API Gateway`는 단순히 관문의 역할만 하는 것이 아니라 트래픽 관리 및 모니터링 API 버전 관리  등 **API 호출에 관련된 모든 작업**을 처리한다. 









**[⬆ back to top](#table-of-contents)**







## 참고문헌

- [[초보자를 위한 AWS 웹구축] 0. 웹서버 아키텍처 소개]([https://tech.cloud.nongshim.co.kr/2018/10/11/%EC%B4%88%EB%B3%B4%EC%9E%90%EB%A5%BC-%EC%9C%84%ED%95%9C-aws-%EC%9B%B9%EA%B5%AC%EC%B6%95-%EC%9B%B9%EC%84%9C%EB%B2%84-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EC%86%8C%EA%B0%9C/](https://tech.cloud.nongshim.co.kr/2018/10/11/초보자를-위한-aws-웹구축-웹서버-아키텍처-소개/))



**[⬆ back to top](#table-of-contents)**