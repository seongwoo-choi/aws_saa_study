# EC2 Hibernate 모드 실습

일단 인스턴스를 하나 생성해야 한다.

인스턴스 생성을 먼저 해보도록 하자.

이미지는 Amazon Linux 2 를 선택하고 t2.micro 유형을 사용한다.

인스턴스 구성에 들어가서 하단에 존재하는 종료 방식 부분을 살펴봐야 한다. 여기서 Hibernate 설정을 걸 수 있다.

종료 방식은 중지로 설정하고, 최대 절전 중지 동작(Hibernate) 를 활성화 한다.

경고문이 나오는데 Hibernate 를 사용하기 위해서 해당 인스턴스 유형의 RAM 크기만큼 루트 불륨에 공간이 할당되고, 루트 불륨이 RAM 의 크기보다 크거나 같은지 확인해야 한다.

t2.micro 의 RAM 크기는 1Gib 인 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156993489-8312f967-bd1f-4c68-8583-ac9171d342aa.png)

![image](https://user-images.githubusercontent.com/67403886/156993520-68781f1a-e701-48f5-ab1f-29a217f6d09c.png)

다음: 스토리지 추가 버튼을 클릭한다.

최대 절전 모드를 사용하려면 루트 볼륨을 암호화하라는 경고문이 나온다.

일단 EBS 볼륨의 크기가 8Gib 로 t2.micro 의 RAM 크기보다 크기 때문에 용량 문제는 패스, 암호화를 해야 하는데 드롭다운을 누르면 기본값으로 세팅된 aws/ebs 를 클릭하여 암호화를 사용한다.

![image](https://user-images.githubusercontent.com/67403886/156993804-f435a894-309a-48d8-854e-ae69706eaee2.png)
![image](https://user-images.githubusercontent.com/67403886/156994001-9016e53c-3aee-4d0f-b81d-2c554f1d5dec.png)

보안 그룹에선 기존에 만들어놓은 launch-wizard-1 보안 그룹을 사용한다. 

만약 없다면 새로 하나 만들자. 만드는 방법은 크게 어렵지 않으니 검색하며 진행할 수 있다.

![image](https://user-images.githubusercontent.com/67403886/156994193-a943f322-6a75-4f64-8ac3-1938c133a228.png)

검토 및 시작을 클릭하여 인스턴스를 생성한다.

생성된 인스턴스를 최대 절전 모드로 전환하고 싶으면 우측 상단에 있는 인스턴스 상태를 클릭하고 인스턴스 최대 절전 모드를 클릭하면 된다.

![image](https://user-images.githubusercontent.com/67403886/156994604-d2c41ee2-c6b1-41f6-a58b-48841c47a3f0.png)

그리고 다시 재실행할 경우 부팅하는데 걸리는 속도가 엄청나게 빨라진 것을 확인할 수 있다.
