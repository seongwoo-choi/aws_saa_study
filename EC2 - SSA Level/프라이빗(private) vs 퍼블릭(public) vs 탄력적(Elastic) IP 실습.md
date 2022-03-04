# 프라이빗(private) vs 퍼블릭(public) vs 탄력적(Elastic) IP 실습

$ cd .pem 파일이 있는 디렉토리
$ ssh -i EC2Tutorial.pem ec2-user@public ip 주소

AWS management console 에서 EC2 인스턴스에 접근을 할 때는 private ip 주소를 사용해도 상관이 없었다. 왜냐하면 AWS EC2 서비스라는 건

결국 커다란 AWS 서비스 내부에서 작동되는 작업이기 때문이다. 즉, 같은 네트워크이기 때문에 private ip 를 사용해도 괜찮았던 것이다.

하지만 AWS 서비스에서 사용하고 있는 네트워크가 아닌 내 로컬에서 접근하려면 private ip 가 아닌 public ip 로 접근을 해야한다.

왜냐하면 AWS 서비스 내부에서 사용하는 네트워크와 내가 사용 중인 네트워크는 다른 네트워크니까 내 컴퓨터에서 접근을 하기 위해서는 public ip 주소로 접근을 해야 한다. 같은 네트워크를 사용하는 AWS 서비스에서는 private ip 주소를 사용해도 문제가 되지 않는다. 

그래서 ssh 로 EC2 에 접속할 때는 public ip 주소로 접속을 해야한다. 그리고 현재 EC2 인스턴스의 public ip 주소는 EC2 인스턴스가 중지됐다 시작되면 새로운 public ip 주소를 할당받는다. 

인스턴스가 중지됐다 다시 켜져도 public ip 주소가 변경되는 것을 막고 싶을 때는 Elastic ip 를 사용하면 된다. 

왼쪽 탭에서 탄력적 ip 탭을 클릭하고 탄력적 주소 할당을 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156720434-c59b2eff-87d8-4e57-81fd-6d102c5dec2a.png)

아마존의 IPv4 주소 풀에서 IPv4 주소를 할당 받아 Elastic ip 로 할당할 것이다.

할당을 클릭하면 내 계정에 탄력적 아이피를 할당받을 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156720685-ea8387d2-c194-4497-96f5-46b6f77d8210.png)

이렇게 할당 받은 IPv4 를 EC2 인스턴스에 설정할 수 있다. 그래서 고정된(static) public ip 를 가질 수 있다.

그리고 탄력적 아이피를 할당받고 실제 인스턴서에 설정하지 않으면 요금이 나간다. 아이피를 할당 받았으면 꼭 EC2 인스턴스에 설정해주자.

우상단에 작업 버튼을 클릭하고 탄력적 IP 주소 연결을 클릭하자

![image](https://user-images.githubusercontent.com/67403886/156720968-870b8249-0f8b-49f1-bb0f-c0295d3d9387.png)

해당 탄력적 IP 주소를 어떤 리소스에 사용할 것인지 만약 인스턴스라면 어떤 인스턴스에 설정할 것인지, 탄력적 IP 주소를 연결할 private ip 주소를 설정해주고 연결 버튼을 클릭하면 된다.

![image](https://user-images.githubusercontent.com/67403886/156721264-2b2c7be5-a62f-4c74-8d89-419bf53b31e8.png)

EC2 인스턴스로 돌아오면 public IPv4 주소가 탄력적 IP 주소로 변경된 것을 확인할 수 있고, 탄력적 IP 주소 란에도 탄력적 IP 주소가 설정된 것을 확인할 수 있다.

탄력적 IP 주소를 클릭하면 해당하는 탄력적 IP 주소의 상세 정보를 확인할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156721599-5c769d36-a12a-4cd8-b859-b312e558c96e.png)

이제 이 탄력적 IP 주소로 SSH 를 통해 원격 접속을 할 수 있다. EC2 인스턴스가 중지됐다가 재실행되도 IP 주소는 변동되지 않으므로 SSH 원격 접속을 할 때 마다 public ip 주소를 확인하지 않아도 된다.

만약 EC2 인스턴스가 종료 상태가 됐다면 탄력적 IP 주소를 릴리스(삭제)해야 한다.


