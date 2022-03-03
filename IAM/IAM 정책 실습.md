# IAM 정책 실습

![image](https://user-images.githubusercontent.com/67403886/155990994-1407fdf7-99ef-4031-b95f-a7e4ffa76d96.png)

현재 사용자는 권한이 없는 상태이다.

이때 권한을 주는 방법은 2가지가 존재하는데 첫 번째는 여러가지 권한을 갖는 그룹에 사용자를 추가해주는 것이고 

두 번째 방법은 이미 존재하거나 혹은 내가 이미 만들어놓은 정책을 사용자에게 곧바로 추가해주는 인라인 방식이다.

![image](https://user-images.githubusercontent.com/67403886/155991038-628d8cbc-ce12-454a-97ce-be8daa1b3ed4.png)

admin 그룹과 developers 그룹에 사용자를 추가해준다. 

현재 사용자는 admin 과 developers 그룹에 모두 속해있는 상태이다.

![image](https://user-images.githubusercontent.com/67403886/155991348-7d5193a4-3588-420d-a60a-84f38c5c9d6f.png)

해당 사용자는 admin 그룹의 정책과 developers 그룹의 정책을 모두 갖고 있는 것을 확인할 수 있다. 

![image](https://user-images.githubusercontent.com/67403886/155991404-7d2d61dd-ca50-40b5-af8d-103155583540.png)

위는 admin 정책으로, 모든 Action 을 모든 Resource 에 허가한다는 것을 알 수 있다.

![image](https://user-images.githubusercontent.com/67403886/155991447-8ac45554-8af7-4d68-84c2-c8168f92a87c.png)

IAM 정책은 우리가 JSON 으로 구성된 정책 문서를 볼 때 IAM 읽기 전용 접근권에 의해 허가된 모든 Action 을 볼 수 있다.

![image](https://user-images.githubusercontent.com/67403886/155991469-75bb9e46-68c0-4fc4-84d8-520a19094a9c.png)

모든 리소스들에 대해 실제로 허가된 Action 들은 위와 같다.

나만의 정책을 만들 수도 있는데 JSON 문서를 작성하는 방법이다. AWS 에는 Visual editor 라는 정책 생성기를 제공해주는데 IAM 서비스와 사용자들, Action, 특정 리소스를 지정하는 등 여러 편의성을 제공해준다.
