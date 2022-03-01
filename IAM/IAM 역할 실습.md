# IAM 역할 실습

IAM 에서 역할 에 들어가서 create role 을 누른다.

<img width="784" alt="image" src="https://user-images.githubusercontent.com/67403886/156121426-20c841ed-1aba-4cb6-89f2-ffe03ca054fe.png">


AWS 계정, 웹 자격 증명 등 여러가지 IAM role 을 생성할 수 있고 여기서는 AWS 서비스를 위한 IAM role 을 생성한다.

<img width="801" alt="image" src="https://user-images.githubusercontent.com/67403886/156121450-b11b7466-4cc1-47f3-9abb-0ffc3bc11963.png">


엄청나게 많은 양의 서비스들에 대한 IAM role 을 생성할 수 있다. 

하지만 일반적인 사용 용도는 EC2 인스턴스와 Lambda 서비스를 사용하기 위해서 만드는 경우이다.

여기서는 EC2 인스턴스에 대한 IAM role 을 만들것이기 때문에 EC2 를 클릭하고 다음을 누른다.

<img width="773" alt="image" src="https://user-images.githubusercontent.com/67403886/156121478-e80f63cf-c74d-408c-a978-1f6781d913e0.png">


그러면 EC2 인스턴스가 어떤 것을 할 수 있도록 설정해줄 수 있는 정책들이 나온다.

내 IAM role 에 대한 권한을 줄 수도 있고 여러가지 권한을 줄 수 있다. 선택하면 된다.

<img width="798" alt="image" src="https://user-images.githubusercontent.com/67403886/156121506-568d7641-854d-4cf4-aad2-cafa5a88c501.png">



역할 세부 정보에서는 생성하려는 역할에 대한 이름과 자세한 설명을 적는다.

<img width="796" alt="image" src="https://user-images.githubusercontent.com/67403886/156121537-b982c7b8-47b8-4388-9e7f-2a827483a3c6.png">


태그도 걸어줄 수 있다. 여기선 생략했다.

<img width="780" alt="image" src="https://user-images.githubusercontent.com/67403886/156121565-4c1e4aa1-0d1c-457c-983a-e9d18099ecdd.png">


이렇게 설정해주고 역할 생성을 클릭하면 EC2 인스턴스에 대한 IAM 역할이 생성된 것이다.
