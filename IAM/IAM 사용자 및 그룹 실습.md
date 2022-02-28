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

![image](https://user-images.githubusercontent.com/67403886/155990595-5c17425e-713b-4dfc-9b85-d3d50cb8c30d.png)

비밀번호가 자동 생성되는 경우라면 .csv 를 다운받아 놓는다.

![image](https://user-images.githubusercontent.com/67403886/155990619-3c374381-acba-4413-a66e-5a64b0c155fd.png)

Permissions 에서 정책명을 그룹에 붙여줄 수 있다. 해당 그룹에 속하는 모든 사용자들은 해당 정책에 의해 권한을 갖게 된다.

![image](https://user-images.githubusercontent.com/67403886/155990665-3307d2b6-5590-48ea-bb16-1a06bc3755dd.png)

계정 별칭을 지어줄 수 있다. Account Alias 에서 create 를 통해 숫자 대신 계정 별칭을 지어주어서 쉽게 로그인할 수 있게 해준다.

![image](https://user-images.githubusercontent.com/67403886/155990694-6e141452-a653-46dd-bccd-360164432066.png)

Copy This URL 을 클릭하면 AWS 로그인 페이지로 이동하고

![image](https://user-images.githubusercontent.com/67403886/155990719-ededaefc-3a57-43f4-ae46-159bf5b5c961.png)

위와 같이 IAM 에서 정의한 사용자로 로그인할 수 있는 로그인 창이 나온다.

AWS 로그인 할 때는 루트 로그인 과 IAM user 로그인 두 가지가 있고 지금 같은 경우는 IAM user 로그인이다.
