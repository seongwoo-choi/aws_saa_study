# AWS CLI 실습

access key 를 생성하는 것은 아주 간단하다.

일단 루트 계정이라면 로그아웃을 하고 IAM 사용자로 로그인을 한다.

우상단 사용자 계정을 클릭하고 보안 자격 증명을 클릭한다.

그리고 Security credentials 을 클릭하여 access key 를 생성한다.

![image](https://user-images.githubusercontent.com/67403886/155995718-98757c36-75dd-40a3-a166-61b3b2c9fbba.png)


아래 사진과 같이 IAM 사용자에 접근할 수 있는 access key id 와 secret access key 가 생성된다. 한 번 생성된 secret access key 는 두 번 다시 변경하거나 볼 수 없으니 csv 파일을 다운로드 받거나 메모장에 작성해놓는다.

![image](https://user-images.githubusercontent.com/67403886/155995729-69dfe411-f9f9-4a78-9e74-38c22c65fe6f.png)


다음으로 할 일은 터미널을 열고 aws configure 명령어를 입력한다.

그러면 access key id 를 물어보는데 방금 생성한 access key id 를 입력하고 그 다음으로 secret access key 를 입력한다.

그러면 기본 지역 이름을 입력하라고 나오는데 내가 살고 있는 지역에서 가장 가까운 지역을 입력하면 된다. 한국 서울 리전을 입력해준다(**[ap-northeast-2](https://ap-northeast-2.console.aws.amazon.com/console/home?region=ap-northeast-2))**

그 다음으로는 기본 출력 포맷을 입력하라고 나오는데 그냥 엔터를 눌러준다. 

그러면 AWS CLI 구성환경이 끝난다.

![image](https://user-images.githubusercontent.com/67403886/155995749-97636edf-e74d-4227-b5bf-e15c0bbac52c.png)


aws iam list-users 명령어를 통해 내 계정에 있는 모든 사용자들의 목록이 나타나게 된다.

![image](https://user-images.githubusercontent.com/67403886/155995786-9e1960d1-219e-43a2-944a-dcc8d66ab0c3.png)

Management console 과 CLI 는 매우 비슷한 종류의 정보를 제공하는 것을 알 수 있다.

즉, Management console 을 사용하여 access key id 와 secret access key 를 만들고 CLI 에서 이를 사용하여 AWS 에 접근할 수 있다는 점이다.
