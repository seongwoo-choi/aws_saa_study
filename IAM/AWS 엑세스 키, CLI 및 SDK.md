# AWS 엑세스 키, CLI 및 SDK

지금까진 AWS 홈페이지에서 Management console 을 사용해 AWS 서비스를 사용하였다.

AWS 에 접근하여 서비스를 사용하는 방식은 총 세가지가 존재한다. 

첫번째는 Management console 로 계정과 비밀번호를 사용하여 로그인한 후 사용하는 방식이다.

두번째 방식은 CLI(Command Line Interface) 방식이다. 이건 우리가 컴퓨터를 셋업할 때 사용하는 방식으로 access key 에 의해 보호된다. access key 를 통해 터미널로 AWS 에 접근할 수 있도록해준다. 

마지막으로는 SDK 가 있다. AWS Software Development Kit 로, 여러가지 언어로 개발하고 있는 코드 안에서 AWS API 를 받아 사용하는 방식이다(프로그래밍 방식). 이 방식 또한 access key 에 의해 보호받는다.

access key 를 어떻게 생성할 수 있냐면 Management console 에서 생성할 수 있고, 이건 비밀번호와 똑같은 개념으로 아주 중요하게 다뤄야 한다.
