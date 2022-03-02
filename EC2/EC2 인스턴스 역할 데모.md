# EC2 인스턴스 역할 데모

EC2 인스턴스에 IAM 역할을 사용하는 법을 익혀보자.

SSH 를 사용하여 EC2 인스턴스에 접근하거나 EC2 인스턴스 연결을 사용해서 EC2 인스턴스에 접근할 수 있다.
둘 중 편한 방법을 사용하자.

EC2 인스턴스 연결 방법은 private IPv4 IP 주소를 사용하여 EC2 에 접근한다.

여기서는 EC2 인스턴스 연결 방법을 사용해서 EC2 에 접근했다.

해당 리눅스는 Amazon Linux AMI 이기 때문에 별다른 설치 없이 aws 명령어를 사용할 수 있다.

$ aws iam list-users 명령어를 입력하면 해당하는 자격 증명이 없다고 표시된다.

![image](https://user-images.githubusercontent.com/67403886/156377432-7cf2ec53-53c8-4f1e-b6a5-31326d257560.png)

AWS 구성을 이용해 자격증명을 구성할 수 있다.

$ aws configure 명령어를 입력하여 자격 증명을 구성하고 access key id, secret access key, region 등을 지정할 수 있다.

하지만!! 이 방식은 정말정말 안좋은 방식이다....
왜냐하면 aws configure 명령어를 사용해서 내 개인 정보들을(access key id, secret access key, region) 입력하면

내 계정에 들어오는 모든 사람들이 EC2 인스턴스 연결 방법을 통해 해당 EC2 인스턴스에 접근할 수 있게 되고 해당 EC2 인스턴스에서 자격 증명을 검색할 수 있기 떄문에 좋은 방법이 아니라는 것이다.

즉, 보안상 매우 취약하다!

### 대신 IAM 역할을 사용하는 것이다.

AWS Management Consol 에서 IAM 역할에 대한 것을 설정해 봤었다.

IAM 서비스로 이동하고 역할 탭을 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156378627-a1af50a8-dc98-4029-89b4-15ffa9aac2b8.png)

여기서 역할을 생성하고 생성한 IAM 역할을 EC2 인스턴스에 연결하여 자격 증명을 제공할 것이다.

간단하게 DemoRoleForEC2 라는 이름을 갖는 IAM 역할을 생성해보자.

역할 만들기를 클릭하고 엔티티 유형으로는 AWS 서비스를 사용 사례로는 EC2 를 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156379102-8e4367e6-f1ac-405a-9341-09baf7eef7bd.png)

권한 정책을 연결해야 하는데 검색 창에서 iamread 를 검색하고 IAMReadOnlyAccess 정책을 추가한다.

![image](https://user-images.githubusercontent.com/67403886/156379243-b894bf72-0525-418a-9298-bddf962673bf.png)

역할 이름을 DemoRoleForEC2 로 지정해주고 역할 생성을 해준다.

![image](https://user-images.githubusercontent.com/67403886/156379318-ce67e264-4f95-46aa-8ec3-03a350c65e23.png)

이제 이 IAM 역할을 EC2 인스턴스에 연결해줘야 한다.

IAM 역할을 연결해주고자 하는 EC2 인스턴스를 클릭하고 보안 탭을 누른다.

![image](https://user-images.githubusercontent.com/67403886/156379571-4e771128-56b0-422e-aafc-3f4333199bda.png)

보안 세부 정보를 보면 IAM 역할에는 아무것도 존재하지 않고 있다.

우측 상단에 작업 버튼을 클릭하고 보안 -> IAM 역할 수정을 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156379789-a7859a6a-3b4d-4ff9-affe-3f879f36f1ea.png)

방금 생성한 DemoRoleForEC2 를 클릭하고 저장을 누른다.

![image](https://user-images.githubusercontent.com/67403886/156379894-e2e28fb6-3b65-45f2-99cc-0c6db5b29de2.png)

그러면 EC2 인스턴스에 DemoRoleForEC2 IAM 역할이 연결된 것이다.

다시 리눅스 화면으로 넘어가서 aws iam list-users 명령어를 사용하면 IAM 서비스로부터 응답을 받을 수 있게 됐다.

![image](https://user-images.githubusercontent.com/67403886/156380179-36b520b3-6d1c-4763-800b-8d8800fa0d46.png)

aws configure 명령어를 사용하지 않고 IAM 역할을 연결했을 뿐이다.

만약에 해당 IAM 역할을 EC2 인스턴스에서 제거하면 접근권한이 사라져서 다시 자격 증명을 하라는 경고문이 나올 것이다.

IAM 역할을 통해서만 EC2 인스턴스에 AWS 자격증명을 제공하는 방법이다.

