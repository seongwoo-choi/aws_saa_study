![image](https://user-images.githubusercontent.com/67403886/155990835-89161f0e-b1ea-4762-b540-4f20cd77fac1.png)

위와 같은 정책을 가지고 작동하는 그룹이 있다. 

Fred 사용자는 오직 사용자에게만 연결된 인라인 정책을 만들어 사용하고 있다.

사용자가 그룹에 속할 수도 속하지 않을 수도 있으므로 원하는 대로 사용자에 대한 인라인 정책을 가질 수 있다.

![image](https://user-images.githubusercontent.com/67403886/155990870-cec99790-6e36-4e9e-898c-549e4ffe6b9b.png)

위처럼 Charles 와 David 는 감사팀에서 정책을 계승한다.

Charles 는 개발자들의 정책과 감사팀의 정책을 갖게 된다.

David 는 감사팀의 정책과 Opretions 팀의 정책을 갖게 된다.

이게 높은 수준에서 어떻게 작동하는지 알아야 한다. 이건 AWS 에서 상당히 많이 볼 수 있는 구조이다.

![image](https://user-images.githubusercontent.com/67403886/155990900-893b440f-cfff-4f12-b553-31d59967a773.png)

IAM 정책 구조는 버전의 숫자로 구성되어 있고 보통 위의 사진과 같은 2012-10-17 이다. 정책 언어 버전이다.

 ID 는 정책을 식별하는 방법인데 선택사항이다.

Statement 는 하나 혹은 여러 개일 수 있고, Statement 에는 몇가지 매우 중요한 부분이 있다.

Sid 는 Statement id 이고 Statement 식별자이다. 이것도 선택사항이다. Sid 로 숫자 1을 갖고 있다.

Effect 를 통해 특정 API 에 접근하는 것을 허용하거나 부정할 수 있다. Principal은 이 정책이 적용될 계정 사용자 또는 역할로 구성된다. 이 예시처럼 AWS 루트 계정에 적용된다.

Action 은 Effect 의 허용 거부 여부에 따라 적용되는 API 호출 목록이다.

Resource 는 작업이 적용될 리소스 목록이다. 이 예시에서는 버킷이지만 여러가지가 있을 수 있다.

마지막으로 여기에는 표현되지 않았지만 이 문장을 언제 적용해야 하고 하지 말아야 하는지에 대한 조건이 있는데 선택사항이라 여기에 작성하지는 않았다.
