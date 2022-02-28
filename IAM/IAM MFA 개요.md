사용자와 그룹들을 보호하는 방법 중에 하나이다.

Multi Factor Authentication, 즉 MFA 라고하는 방법이 있다.

AWS 에선 이 방법은 필수조항이고 사용하도록 강력하게 권고된다. 

root 계정을 보호하는 것 뿐만 아니라 모든 IAM 사용자들을 보호할 수 있는 아주 강력한 보호 방법이다.

MFA 는 계정 비밀번호와 내가 가지고 있는 장치(핸드폰, 태블릿 등)의 MFA 생성 토큰을 통해 계정을 보호하는 방식이다.

즉, 계정을 해킹당해도 내 핸드폰이 없으면 MFA 생성 토큰이 뭔지 알 수 없기 때문에 로그인을 할 수 가 없는 것이다.

MFA 를 사용하는 첫번째 방법은 Virtual MFA device 이다. Google Authenticator 를 사용하는 방식으로 하나의 핸드폰에서 작동하거나 다중 장치인 Authy 에서 사용한다. Authy 는 하나의 디바이스에서 MFA 토큰을 지원해준다. 

즉, Virtaul MFA device 에서 내가 원하는 만큼의 사용자와 계정을 가질 수 있다는 점이다. 

![image](https://user-images.githubusercontent.com/67403886/155991619-97f50dec-cbd1-4545-a169-a8e96b2b04be.png)


두번째 방법은 Universal 2nd Factor 혹은 U2F Security Key 이다. 이건 물리 장치로, 최성우에 의한 choikey 가 있다고 가정한다. 

choikey 는 AWS 의 서드 파티로 물리적 장치를 사용한다. 일반적인 usb 처럼 생겼다. 이 choikey 는 다양한 루트를 지원하고 IAM 사용자들은 단일 보안을 사용하기 때문에 사용자의 수만큼 많은 choikey 를 가진 필요가 없다.

![image](https://user-images.githubusercontent.com/67403886/155991637-b9875931-ebe2-45bf-a50b-beddb8720b3d.png)


세번째 방법은 Hardware Key Fob MFA device 를 갖는 것이다. 이것 또한 AWS 의 서드 파티로 물리적 장치를 사용한다. 

![image](https://user-images.githubusercontent.com/67403886/155991652-58c83ec2-9713-4301-97e9-54eb69f9229d.png)


마지막으로는 Hardware Key Fob MFA Device for AWS GovCloud(US) 로 이것 또한 AWS 의 서드 파티로 물리적 장치를 사용한다. 

![image](https://user-images.githubusercontent.com/67403886/155991676-ae75fc30-c5d0-465a-84f1-9da418f6db03.png)
