# EC2 인스턴스 연결

SSH 를 사용해서 EC2 인스턴스에 연결을 해봤다.
SSH 말고도 EC2 Instance Connect 라는 방법으로 EC2 인스턴스에 연결할 수 있다.
우측 상단에 연결이라고 되어있는 부분이 보일텐데 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156374498-85393425-f9a1-40b5-b5f0-413243b9f32a.png)

EC2 인스턴스 연결, Session Manager, SSH 클라이언트, EC2 직렬 콘솔 4가지 옵션을 확인할 수 있다.

여기서는 EC2 인스턴스 연결 옵션을 이용할 것이다.

사용자 이름은 자신이 원하는 이름으로 지정해서 사용하면 된다.

EC2 인스턴스 연결 옵션은 Amazon X2 나 Ubuntu 에서 사용할 수 있다.
AWS 의 모든 AMIs 타입에서 작동하는 것이 아니다.
연결 버튼을 누르면 자동적으로 EC2 인스턴스에 연결이 된다.

![image](https://user-images.githubusercontent.com/67403886/156374570-63748e68-e23c-4856-b78f-73c7a8bf6e1b.png)

현재 이 방식은 SSH 키를 사용하지 않았지만 EC2 인스턴스에 자동으로 연결된 것을 확인할 수 있다.
이 방식은 EC2 인스턴스에 임시 SSH 키를 업로드하는 방식이다. 그래서 보안 그룹에서 인바운드 룰 탭에 있는 SSH 룰을 제거하면 SSH 임시키를 발급받지 못하기 때문에 접속을 할 수 없게 된다.
이 방식은 사용자가 직접적으로 SSH 키를 사용하지 않는 것일 뿐이지 사실은 임시 SSH 키를 발급받아서 EC2 인스턴스에 접근하는 것이다.

![image](https://user-images.githubusercontent.com/67403886/156375441-a68a7dfb-4e1c-4f37-be99-4c554fe0b5c7.png)








