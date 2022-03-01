# EC2 인스턴스 생성

리눅스 OS 를 사용하는 EC2 인스턴스를 생성할 것이다.

EC2 인스턴스 구성을 위한 접근 방식을 알아야 한다.

EC2 user data 스크립트를 사용하여 웹 서버를 구성할 것이다.

![image](https://user-images.githubusercontent.com/67403886/156162078-d42b3703-5feb-4afe-9bb6-2bff17784b5e.png)


ec2 를 검색해서 ec2 서비스에 들어간다.

현재 사는 지역에서 가까운 region 으로 설정한 후에 인스턴스를 클릭하고 인스턴스 시작 버튼을 누른다.

![image](https://user-images.githubusercontent.com/67403886/156162110-eb1fa57e-9bab-44f3-a061-efe34db193e8.png)


그러면 Amazon Maching Image 를 선택하는 화면이 나오는데 빠른 시작을 누르면 AWS 에서 제공해주는 AMI 들이 나온다.

![image](https://user-images.githubusercontent.com/67403886/156162138-243efe8e-45fc-46e5-96b2-49efe81e3e9b.png)


나의 AMI 처럼 나만의 AMI 를 만들 수 있다.

또, AMI 를 위한 AWS 마켓플레이스와 커뮤니티 AMI 가 존재한다. 여기서 다른 사용자들이 만들어놓은 AMI 를 사용할 수도 있다.

여기서는 빠른 시작에 있는 Amazon Linux 2 AMI 를 사용할 것이다. 이것은 프리 티어에 적합하다. 즉, 돈을 내지 않고 EC2 인스턴스를 만들 수 있다는 것이다.

다음으로는 인스턴스 유형을 선택하는 화면이 나오는데 정말 다양한 인스턴스 유형을 확인할 수 있다. 아래 사진 처럼 각각의 이름들로 그룹화 되어 있다.

![image](https://user-images.githubusercontent.com/67403886/156162166-31d93150-2b0a-4176-a483-49a94609e3f2.png)


프리 티어로 시작하기 때문에 t2 micro 를 선택한다. 

![image](https://user-images.githubusercontent.com/67403886/156162185-0972dacf-0a67-474b-a809-e52073667754.png)


다음으로는 인스턴스 세부 정보를 구성할 것이다.

한 개의 인스턴스를 사용할 것이고 기본 네트워크 세팅을 사용한다. 기본으로 설정된 것은 VPC 즉, virtual private cloud 로 실행한다.

IAM 역할은 아무것도 건들지 않는다. 나중에는 EC2 가 IAM 역할을 가지게 될 것이다.

![image](https://user-images.githubusercontent.com/67403886/156162217-315a4658-4521-4aab-92c1-0ad5a2e4d9a4.png)


스크롤을 마지막까지 내리게 되면 EC2 사용자 데이터를 확인할 수 있다. 

이 EC2 사용자 데이터는 맨 처음 부팅에만 실행되는 스크립트이다. 즉 맨 처음 환경 구성을 위한 설정들을 세팅하기 위해 사용한다고 보면 된다.

```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>hello world $(hostname -)</h1>" > /var/www/html/index.html
```

리눅스에서 사용하는 yum 패키지 매니저를 업데이트 하고 httpd 라이브러리를 다운받은 후에 httpd 를 실행하게 한다. 그 후 내 리눅스 환경의 hostname 에 대한 정보를 /var/www/html 디렉토리에 index.html 로 저장한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2866fc9b-0b32-4866-9319-f9a40991ee88/Untitled.png)

다음 스토리지 추가를 누른다.

여기에는 EC2 인스턴스에서 사용할 수 있는 데이터 디스크의 양이 표시된다. 모든 값들을 기본으로 놔둔다. 종료 시 삭제(Delete on Termination)라는 부분이 체크된 것을 확인할 수 있다. 이 말은 우리가 인스턴스를 종료할 때 저장장치도 사라진다는 뜻이다.

![image](https://user-images.githubusercontent.com/67403886/156162250-89b1ce91-b5dd-4527-bd45-42c64d7a0992.png)


다음을 클릭하여 태그를 설정하는 페이지로 넘어간다. 해당 인스턴스에 대한 정보를 표시해주면 된다.

여기서는 아무런 태그를 붙이지 않고 넘어갔다.

![image](https://user-images.githubusercontent.com/67403886/156162280-d9eb6bf9-3a15-4093-9345-96efd569113a.png)


다음 버튼을 클릭해서 보안 그룹 구성을 할 수 있다. 

기존에 사용하던 보안 그룹을 사용할 수도 있지만 여기서는 새로운 보안 그룹을 생성할 것이다.

규칙 추가 버튼을 클릭해서 HTTP 에 대한 규칙을 추가한다. 포트를 80번을 사용하는데 이 규칙은 어디서나 똑같이 적용된다. 하나이 규약이라고 생각하면 된다.

HTTP 를 통해 EC2 인스턴스의 웹사이트에 접근할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156162301-5dc4d7ce-5cb5-4403-b1cd-438627008ac7.png)



검토 및 시작을 클릭한다.

그러면 인스턴스 보안 그룹에 대한 경고가 나오는데 현재 인스턴스의 보안 그룹이 전세계에 오픈되어 있기 때문에 나온다. 의도한 것이기 때문에 무시한다. 

검토 및 시작 페이지에서는 우리가 EC2 인스턴스 설정을 한 것을 재확인할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156162371-d5bd6ab9-f175-4d71-871b-beef34f7fb6e.png)


시작하기 버튼을 클릭한다. 그러면 키 페어를 선택 또는 생성하라고 나오는데 키 페어는 ssh 방식으로 인스턴스에 접근하기 위해 필요하다. 

![image](https://user-images.githubusercontent.com/67403886/156162393-d11d22e8-f7e1-4ada-946d-2ee45d53622c.png)


현재는 기존 키 페어가 존재하지 않기 때문에 새 키 페어 생성하기를 클릭해 키 페어를 새로 생성한다. 

중요한 점은 키 페어 유형을 RSA 로 선택해야 한다는 것! 

EC2 Tutorial 이라고 이름을 지정해줬다. 이름을 지정했으면 키 페어 다운로드를 클릭해서 .csv 파일을 다운 받는다. 이 파일은 잃어버리면 안되니 잘 보관하자.

![image](https://user-images.githubusercontent.com/67403886/156162468-ce827f2d-46fd-45dd-8df1-54ef6c092098.png)


이제 인스턴스 시작 버튼이 활성화됐을 것이고 버튼을 클릭한다. 

인스턴스가 활성화되면 링크가 나오는데 클릭해서 접근을 하거나 EC2 대시보드에서 접근을 할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156162500-63e0c89c-fdd4-4702-a97a-de9b9369529d.png)


10 초에서 20 초 정도 기다리면 인스턴스가 실행 상태로 변한다. 

이런 방식으로 100개의 인스턴스를 실행할 수도 있다. 필요할 때 마다 유연하게 컴퓨터 성능을 올릴 수도 있다.

여기서는 태그를 붙이지 않아 인스턴스 이름이 명명되지 않았는데 원하는 이름을 인스턴스에 붙여준다.

여기서는 첫 인스턴스라고 이름을 붙여줬다.

인스턴스를 누르고 스크롤을 내리면 해당하는 인스턴스에 대한 정보를 확인할 수 있다. 다만 키 페어는 다시 다운받을 수 없다.

![image](https://user-images.githubusercontent.com/67403886/156162535-2bedb9a1-d5f3-47b9-a3e8-8292a99137c3.png)


public IPv4 address 를 확인할 수 있고, private IPv4 address 도 확인할 수 있다.

만약 인스턴스가 public IPv4 address 를 갖지 않았다면 해당 옵션을 비활성화 했기 때문이라고 유추할 수 있다. 

 public IPv4 address 란에 있는 개방 주소법을 클릭하면 인스턴스에 접근할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156162552-253149ed-c915-4727-8569-20a15bbba0a5.png)


public IPv4 address 로 접근해도 작동하지는 않는다. 왜냐하면 HTTPS 에 대한 설정을 하지 않았기 떄문에 작동하지 않는다.

![image](https://user-images.githubusercontent.com/67403886/156162582-d9dd346a-7753-41a0-bf2a-130f68f4f885.png)


만약에 인스턴스에 접근을 해보고 싶으면 public IPv4 address 를 복사해서 붙여 넣으면 http 로 작동을 하기 때문에 우리가 EC2 user data 에서 세팅한 index.html 이 나타나는 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156162600-6e59f605-e01b-4930-b93b-6b8c9ba318a1.png)


현재 접근한 ip 는 public ip 가 아닌 private ip 로 접근한 것이다. 그래서 private IPv4 address 의 주소를 복사해서 붙여넣으면 화면에 나오는 결과값이 똑같은 것을 알 수 있다.

왜냐하면 EC2 user data 스크립트를 통해 만들었기 때문에 의도적으로 private ip 로 응답하게 했다.

이제 인스턴스를 종료해야 하는데, 매우 간단하다. 인스턴스를 선택하고 인스턴스 상태를 중지로 변경한다.

![image](https://user-images.githubusercontent.com/67403886/156162621-95d25f4c-cde9-44df-a70d-b8162e5b4f1f.png)


클라우드에서 인스턴스를 작동시키거나 중지시키거나 삭제할 수 있다. 인스턴스를 사용하지 않을 때마다 멈추는 것이 좋다.

인스턴스를 종료하기 전에 데이터를 백업하는 것이 매우 일반적이다!

만약 인스턴스를 중지했다가 다시 실행하면 public IPv4 address 가 변경되기 때문에 새로운 공공 ip 주소로 접근해야 한다.

인스턴스가 작동되는 동안은 돈을 지불해야 하지만 중지시키면 돈을 낼 필요가 없다.
