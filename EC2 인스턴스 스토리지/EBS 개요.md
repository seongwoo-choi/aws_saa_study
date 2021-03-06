# EBS 개요

EC2 인스턴스의 다른 저장 옵션에 대해 알아본다.

EBS 볼륨은 Elastic Block Store 의 약자로 인스턴스에 연결된 네트워크 드라이브이다.

EBS 볼륨을 사용하면 인스턴스가 종료된 이후에도 데이터를 유지할 수 있다.

즉, 이전에 사용했던 EBS 볼륨을 EC2 인스턴스에 마운트하는 것이 목적이라고 할 수 있다.

EBS 볼륨들은 CCP 레벨에서 한번에 하나만 설치될 수 있다. 

EBS 볼륨을 생성할 때 특정 가용 영역에 묶여서 생성된다. (Ex) ap-northeast-2

정리하자면 EBS 볼륨은 네트워크 USB 라고 생각하면 된다. 일반적인 USB 는 물리적으로 존재하여 여러 장치들에 끼워 사용할 수 있지만

EBS 볼륨은 네트워크를 통해 연결하는 드라이브이고 물리적인 드라이브는 아니다! 또한 AWS 에서는 매월 SSD 나 마그네틱 유형의 무료 스토리지를 제공해준다.(최대 30GB)

인스턴스와 EBS 볼륨은 네트워크를 통해 통신하기 때문에 인스턴스에서 드라이브로 이동하는데 약간의 지연이 있을 수 밖에 없다.

아까도 말했다싶이 EBS 볼륨은 네트워크 드라이브여서..

물리적인 저장 장치가 아니라서 인스턴스에서 EBS 볼륨은 매우 쉽게 탈부착이 가능하고 빠르게 장애 조치를 취할 수 있다.

하지만, 사용중인 EBS 볼륨의 가용 영역이 ap-northeast-1 이라면 이외의 다른 가용 영역으로 EBS 볼륨을 옮길수가 없다.

그러나 스냅샷을 찍는다면 볼륨을 다른 가용 영역으로 옮길 수 있게 된다.

EBS 볼륨을 사용하기 전에 몇 기가 정도를 사용할 것인지 어느 정도 속도의 IOPS 가 필요한지 등에 대해서 계획하고 사용해야 한다.

해당하는 성능 만큼의 요금이 청구 되기 떄문에 매우 신중하게 선택해야 한다. 물론, 나중에 더 나은 성능이나 더 큰 용량을 원할 경우에는 EBS 볼륨을 업그레이드 할 수 있다.

예를 들어서 us-east-1a 에 EC2 인스턴스 하나를 생성하고 여기에 EBS 볼륨을 장착했다. 또 다른 EC2 인스턴스를 생성하고 여기에도 EBS 볼륨을 붙여주고 싶은데 Ceritfied Cloud Practitioner level 에서는 EBS 볼륨이 동시에 두개의 인스턴스에 연결될 수가 없다.

그래서, 또 다른 EBS 볼륨을 만들어서 연결해줘야 한다.

하나의 인스턴스에 두개의 EBS 볼륨을 설정할 수도 있다.

![image](https://user-images.githubusercontent.com/67403886/157062365-045d80f6-c8bf-4e41-a586-34f62dec0580.png)

다른 가용 영역에서 EBS 볼륨을 갖고 싶다면 해당하는 가용 영역으로 이동하여 EBS 볼륨을 생성해야 한다. 여기서는 EC2 인스턴스와 EBS 볼륨을 같이 생성하여 연결해줬다. 

EBS 볼륨을 생성하고 EC2 인스턴스에 연결할 필요는 없다. EBS 볼륨들은 필요에 EC2 인스턴스에 연결할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/157062788-78e9dd6b-9de0-409f-a931-f84c6ce55618.png)

마지막으로 EC2 인스턴스를 통해 EBS 볼륨을 생성할 때, Delete on Termination attribute 라는 옵션이 있다.

이 방법은 EC2 인스턴스가 종료될 때 루트 EBS 볼륨이 삭제되는 옵션이다.

이 옵션은 기본값은 아니며, 인스턴스가 종료돼도 루트 EBS 볼륨이 보존되게 할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/157063192-da6617fd-9408-49df-adce-451544d92b3a.png)
