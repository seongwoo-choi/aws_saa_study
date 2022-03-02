# 리눅스 또는 맥에서 SSH 실행하는 방법

SSH 는 AWS 를 다룰 때 가장 중요한 기능 중 하나이다. 
터미널이나 CLI 를 사용하여 원격으로 서버를 조종할 수 있도록 허락하는 것이다.
EC2 인스턴스가 있고 아마존 리눅스 2도 있다.
EC2 인스턴스는 public ip 를 사용하고 있다. 
이 인스턴스에 접근을 하기 위해서는 인바운드 룰로 SSH 에 대한 설정을 해줘야 한다.
그리고나서 터미널을 사용하여 22번 포트를 통해 EC2 인스턴스에 접근할 것이다.
![image](https://user-images.githubusercontent.com/67403886/156366968-061757ad-eb22-40fa-b926-14c62f8620e8.png)

이런식으로 접근을 하게 되면 내 터미널이 EC2 인스턴스인 것처럼 되는 것이다.

일단 실행 중인 EC2 인스턴스를 클릭한다.
EC2 인스턴스는 public DNS 와 public ip 를 사용한다. 즉 EC2 에 접근하기 위해 public IPv4 주소를 복사한다. 이 IP 주소를 사용할 것이다.

또한 인바운드 룰에서 SSH 22 번 포트로 모든 IP 주소에서 접근할 수 있게 열어놓은 상태라서 바로 EC2 에 접근을 할 수 있다.

MAC 이나 Linux 에서 터미널을 연다.

그리고 ssh ec2-user@public IPv4  를 누르고 엔터를 친다.
ec2-user 는 아마존 리눅스의 사용자를 뜻한다.

![image](https://user-images.githubusercontent.com/67403886/156372089-c973432a-3dce-4654-8f54-c0cbde431529.png)

위와 같이 yes 를 누르라고 나오는데 yes 를 쳐서 다음으로 넘어간다.
그러면 permission denied. 즉, 허가가 거부되었다고 나온다.
당연히 접속이 허가되지 않는다! SSH 는 보안쉘이다! IP 주소를 안다고 해서 아무나 접속을 할 수 없는 것이다.

![image](https://user-images.githubusercontent.com/67403886/156372177-e6106232-d8bd-4460-89cb-1d2351c2d467.png)

이전에 다운로드 받아놓은 키 파일이 있을 것이다. 이 키를 사용해서 EC2 인스턴스에 접속할 것이다.
해당 키 파일이 있는 폴더로 이동한다. 

![image](https://user-images.githubusercontent.com/67403886/156372748-dd965f06-37f9-4c25-8713-b92cbcddc907.png)

그리고나서는 다시 ssh 를 이용해서 EC2 인스턴스에 접근을 한다.
ssh -i EC2Tutorial.pem ec2-user@3.35.235.113

![image](https://user-images.githubusercontent.com/67403886/156372949-4cd756b0-7925-4c06-babf-605b7376dcee.png)

그러면 경고: 보호되지 않은 private 한 키 파일입니다 라는 경고문이 나온다.
일반적으로 나오는 시험문제로 해당 파일에 대한 권한이 0644 로 너무 개방적이다라고 나온다
여기서 말하는 private key 는 다른 사람에 의해 접근될 수 있는 가능성이 있는 키다.
그래서 좋지 않은 권한 부여 방식이라고 경고문이 말해준다.

그래서 키를 갖고 있음에도 SSH 를 통해 EC2 인스턴스에 접근을 할 수 없는 것이다.

![image](https://user-images.githubusercontent.com/67403886/156373179-e1f35a3d-eb0a-421c-a4d9-dc7440311faf.png)

이러한 문제를 해결해주기 위해 파일의 소유권자에게만 파일 권한을 주어야 한다. 
chmod 0400 EC2Tutorial.pem
chmod 로 파일에 대한 권한을 소유권을 가진 사람만 read 할 수 있게 변경했다.
그러면 SSH 로 가상 머신에 접근을 할 수 있게 됐다.

![image](https://user-images.githubusercontent.com/67403886/156373669-6cb6527b-4f78-4f6c-bbae-43773dc56d67.png)

![image](https://user-images.githubusercontent.com/67403886/156373822-943b4b4f-05bf-4a71-b78e-aa6e5b572680.png)

가상 머신에서 나가고 싶을 때는 컨트롤 D 를 누르거나 logout 명령어를 작성하여 나올 수 있다.
