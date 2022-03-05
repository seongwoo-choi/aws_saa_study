# ENI(탄력적 네트워크 인터페이스) - 실습.md

일단 EC2 인스턴스 두개를 만들어야 한다.

인스턴스 구성에 들어가서 인스턴스 개수를 2개로 잡는다.

![image](https://user-images.githubusercontent.com/67403886/156888757-589bd123-07c7-4213-afb1-231b1145b166.png)

보안 그룹은 다음과 같이 구성하고, 시작 버튼을 클릭해서 인스턴스를 생성한다.

![image](https://user-images.githubusercontent.com/67403886/156888813-4851b5a9-d3ff-4225-a004-f1c8f9eaa43b.png)

기존의 키 페어가 있으면 기존 키 페어를 사용하고 없으면 새로 생성한 후에 다운받아 파일을 보관한다.
 
![image](https://user-images.githubusercontent.com/67403886/156888843-0edce4de-d7f5-4cf3-b04d-ab8c2e8eae7e.png)

생성한 인스턴스를 클릭하고 네트워크 탭을 누른다. 스크롤을 내리면 네트워크 인터페이스 탭을 볼 수 있다.

방금 생성한 각각의 인스턴스는 하나의 네트워크 인터페이스를 갖게 된다.

인터페이스 아이디를 확인할 수 있고, 각각의 네트워크 인터페이스들은 public IPv4 와 private IPv4 private IPv4 DNS 를 갖는 것을 알 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156889033-46cd060c-8c67-4547-80d2-4e94f36ff299.png)

왼쪽 탭 란을 스크롤해서 네트워크 및 보안의 네트워크 인터페이스를 누르면 방금 생성한 인스턴스들에 대한 각각의 네트워크 인터페이스가 있다.

대시보드를 통해서 해당 네트워크 인터페이스가 어떤 인스턴스에서 사용중인지 상태는 어떤지 퍼블릭 IPv4 주소는 무엇인지 등등에 대한 정보를 얻을 수 있다.

여기서 새로운 네트워크 인터페이스를 생성할 수 있다.

네트워크 인터페이스 생성 버튼을 클릭해서 새로운 네트워크 인터페이스를 생성해보자.

![image](https://user-images.githubusercontent.com/67403886/156889146-b51c459b-9be2-4b39-8f65-51af6d9a34eb.png)

네트워크 인터페이스 이름은 DemoENI 로 설정했고 생성한 네트워크 인터페이스가 위치할 서브넷을 골라야 하는데 EC2 인스턴스가 위치한 AZ 을 골라야 한다. 왜냐하면 생성하려는 네트워크 인터페이스를 사용하기 위해서는 같은 EC2 와 같은 AZ 에 속해야 하기 때문이다.

생성한 EC2 인스턴스들은 모두 ap-northeast-2a 에 속해있다.

![image](https://user-images.githubusercontent.com/67403886/156889330-25720f86-89f8-42b7-822f-209e2ad0d528.png)

다음으로는 private IPv4 에 자동 할당 할 것인지 커스텀하게 사용할 것 인지 정할 수 있다.

여기서는 자동 할당을 받도록 했다.

![image](https://user-images.githubusercontent.com/67403886/156889399-3eb5add7-abe2-40e7-b690-92dbd15df30d.png)

ENI 에 보안 그룹을 세팅할 수 있다. 여기서는 launch-wizard 1 이라고 명명된 보안 그룹을 설정했고, 해당 보안 그룹은 위에서 EC2 인스턴스를 생성할 떄 사용한 보안 그룹과 똑같은 보안 그룹이다.

네트워크 인터페이스 생성 버튼을 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156889457-6e625ed3-c8f1-4c62-a65a-1ff074dbe83a.png)

DemoENI 라는 새로운 네트워크 인터페이스를 생성했고 기본 프라이빗 IPv4 주소를 만들었다. 

![image](https://user-images.githubusercontent.com/67403886/156889536-3a2ea97e-580c-47b5-bc3e-be6a98fd4424.png)

DemoENI 를 누르고 우측 상단의 작업 버튼을 누르고, 연결을 클릭하여 인스턴스에 네트워크 인터페이스를 추가할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156889610-5e7db0d9-2dd0-46d5-bf90-678120c7ea8e.png)

![image](https://user-images.githubusercontent.com/67403886/156889602-dc43d19c-5aa6-487e-baab-1a74c47539a0.png)

EC2 인스턴스로 돌아가서 네트워킹 탭으로 간 후 네트워크 인터페이슬 보면 생성한 DemoENI 가 추가된 것을 확인할 수 있다.

기본적으로 제공된 네트워크 인터페이스는 기본 구성으로 사용되는 네트워크 인터페이스이고, DemoENI 같은 경우에는 후에 추가된 네트워크 인터페이스이다. 이건 보조 프라이빗 IPv4 를 제공해준다.

![image](https://user-images.githubusercontent.com/67403886/156889657-15415228-d9c1-4888-aef7-74ce9e4c9288.png)

DemoENI 는 EC2 인스턴스에서 다른 EC2 인스턴스로 옮기거나 다시 가져올 수 있다.

이렇게 하는 이유는 ENI 를 이동하여 두 인스턴스 간에 매우 빠르고 쉬운 네트워크 장애 조치를 취할 수 있기 떄문이다. 

다시 네트워크 인터페이스로 돌아와서 DemoENI 를 분리시킨다. 아까 EC2 인스턴스에 연결했던 것처럼 작업 버튼을 클릭하면 나오는 작업 목록 중에서 분리를 클릭하면 해당 EC2 인스턴스에서 ENI 가 강제로 분리가 된다.

그리고 다른 EC2 인스턴스에 연결을 시킬 수 있다.

위와 같은 방식으로 인스턴스 간에 장애 조치를 수행할 수 있다.

DemoENI 를 제외한 나머지 두개의 네트워크 인터페이스는 EC2 인스턴스를 생성하면서 자동으로 생성된 네트워크 인터페이스이다. 그래서 EC2 인스턴스를 종료하면 네트워크 인터페이스도 같이 삭제되지만 DemoENI 는 삭제되지 않는다.

그래서 추가적으로 설정한 네트워크 인터페이스의 경우에는 인스턴스를 종료한다고해도 삭제되지 않으므로 수동으로 삭제해줘야 한다!

ENI 는 사용하지 않더라도 요금이 발생하지는 않는다!
