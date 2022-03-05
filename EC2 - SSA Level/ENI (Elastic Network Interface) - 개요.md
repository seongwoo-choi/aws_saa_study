# ENI (Elastic Network Interface) - 개요

ENI 는 VPC 의 논리적 구성 요소이며 가상 네트워크 카드이다.

EC2 인스턴스 외부에서 사용되며 EC2 인스턴스에 네트워크 접근 권한을 부여해준다.

AZ 에 한 개의 EC2 인스턴스가 있고 이 인스턴스에는 eht0 이라는 기본 ENI 가 설정된다. 

eth0 이외에도 예비 ENI 를 가질 수 있다. 여기선 eth1 을 예비 ENI 로 갖는다. ENI 는 private IPv4 한 개당 탄력적 IPv4 를 갖거나, 한 개 이상의 public IPv4 를 갖게 된다. 

ENI 를 독립적으로 생성하여 EC2 인스턴스에 연결하거나 장애 조치를 위해 EC2 인스턴스에서 이동할 수 있다.

또한 ENI 는 AZ 에 묶여서 사용된다. 이말인즉슨, ENI 를 특정 AZ 에서 생성할 수 있고, 어떤 AZ 에서만 사용될 수 있도록 묶을 수 있다는 뜻이다.

ENI 에는 다음과 같은 속성이 포함될 수 있다.
- VPC의 IPv4 주소 범위 중 기본 프라이빗 IPv4 주소
- VPC의 IPv4 주소 범위 중 하나 이상의 보조 프라이빗 IPv4 주소
- 프라이빗 IPv4 주소당 한 개의 탄력적 IP 주소(IPv4)
- 한 개의 퍼블릭 IPv4 주소
- 한 개 이상의 IPv6 주소
- 하나 이상의 보안 그룹
- MAC 주소
- 원본/대상 확인 플래그

![image](https://user-images.githubusercontent.com/67403886/156888286-36386dba-7960-4c11-80cf-1859ad51b0f6.png)

또한 아래 사진처럼 어떤 EC2 인스턴스에서 사용되는 ENI 를 다른 EC2 인스턴스에서 사용하게 이동할 수 있다. 

해당 EC2 의 private ip 를 통해 접근할 수 있을 경우, ENI 를 private ip 를 통해 이동시킬 수 있고 장애 조치를 취할 때 매우 유용하게 사용할 수 있다. 

![image](https://user-images.githubusercontent.com/67403886/156888537-32c9af9f-275b-4b5e-8eb0-af6ffeebbba0.png)
