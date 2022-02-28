# IAM MFA 실습

루트 계정을 위해 MFA 를 세팅할 수 있다.

루트 계정은 모든 권한을 가지고 있기 때문에 조심히 관리해야 한다.

우상단에 존재하는 계정이름을 클릭하고 보안 자격 증명을 클릭한다.

여기서 MFA 를 활성화 한다.

![image](https://user-images.githubusercontent.com/67403886/155991784-62468685-7ed7-4ae5-a8d5-e3d107c37819.png)


세 가지 옵션이 있는데 버츄얼 MFA 디바이스, U2F 보안키, 다른 MFA 디바이스 하드웨어이다. 

핸드폰을 통해 MFA 토큰을 얻고자 하기 때문에 버츄얼 MFA 디바이스를 선택한다.

![image](https://user-images.githubusercontent.com/67403886/155991801-883035fb-58b0-4540-8ed2-53bfbe5e75fc.png)


다음으로 나오는 화면은 MFA 를 설정하는데 사용할 수 있는 호환가능한 앱의 목록이다.

![image](https://user-images.githubusercontent.com/67403886/155991833-080b7407-247b-49b8-bd37-31c9cfbb47a7.png)


안드로이드와 아이폰는 아래와 같은 버츄얼 MFA 어플리케이션을 사용할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/155991857-8770e417-61b7-4d00-b1cd-f582f89b33b4.png)


Authy 를 사용하면 여러 디바이스에서 MFA 토큰을 생성하여 로그인 할 수 있기 때문에 좋다. 물론 공짜 앱이다.

QR 코드 보기를 클릭하여 Authy 나 다른 MFA 애플리케이션에서 QR 코드를 스캔한다. 이 방식으로 계정을 디바이스에 추가하는 것이다.

계정을 추가한 이후에 MFA 토큰이 생성되는 데 총 6자리로 총 2번 입력해주면 등록이 된다.

![image](https://user-images.githubusercontent.com/67403886/155991889-4ab36cdd-ea13-4a82-a338-aed2e7c5573c.png)


![image](https://user-images.githubusercontent.com/67403886/155991908-16e9206b-9784-4a13-a1f0-99a78f600a06.png)


![image](https://user-images.githubusercontent.com/67403886/155991921-f063aec0-27e3-43cb-9f0b-d62b7748e4b5.png)


위와 같이 MFA 가 성공적으로 할당된 것을 확인할 수 있다.

이제 계정에 로그인할 때 MFA 토큰을 입력하라는 창이 나온다.
