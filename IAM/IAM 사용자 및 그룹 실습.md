# IAM 사용자 및 그룹 실습

IAM 은 글로벌 서비스인 것을 알자.

“사용자들" 아래로 가서 “사용자 추가"를 클릭

root 유저만 모든 허가를 가지고 있고 사용자들을 생성해줄 수 있다.

루트 계정은 정말 정말 필요할 때만 사용한다.

자격 증명 유형은 암호 유형의 자격 증명을 활성화한다.

사용자 그룹을 만들어서 지금 만드는 사용자를 그룹에 추가하거나 기존에 존재하는 그룹에 사용자를 추가할 수 있다.

태그는 사용자들에 대한 조종 권한을 돕는 정보이다.

특정 사용자들을 고려해서 추가하려는 정보이다. 즉, 이 사용자에 대한 메타 데이터를 입력해주는 것이라고 생각하자

얘는 개발자고, 엔지니어링 작업을 한다. 이런식으로 태그를 걸어주는 것이다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e15e3672-9518-4c80-b32f-42f71b63fb38/Untitled.png)

비밀번호가 자동 생성되는 경우라면 .csv 를 다운받아 놓는다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/642c79f3-e207-4ee6-a8b0-6459d9c0f812/Untitled.png)

Permissions 에서 정책명을 그룹에 붙여줄 수 있다. 해당 그룹에 속하는 모든 사용자들은 해당 정책에 의해 권한을 갖게 된다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5894de3d-2603-4812-b6fb-b8dba270b0fe/Untitled.png)

계정 별칭을 지어줄 수 있다. Account Alias 에서 create 를 통해 숫자 대신 계정 별칭을 지어주어서 쉽게 로그인할 수 있게 해준다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1f310a58-178f-41be-8f5b-62789080d84a/Untitled.png)

Copy This URL 을 클릭하면 AWS 로그인 페이지로 이동하고

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f17960b8-32c6-4070-a31f-67119506d2e4/Untitled.png)

위와 같이 IAM 에서 정의한 사용자로 로그인할 수 있는 로그인 창이 나온다.

AWS 로그인 할 때는 루트 로그인 과 IAM user 로그인 두 가지가 있고 지금 같은 경우는 IAM user 로그인이다.