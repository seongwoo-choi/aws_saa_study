# EC2 배치 그룹 실습

EC2 서비스로 이동, 왼쪽 하단에서 배치 그룹을 찾아서 클릭하고, 배치 그룹 생성버튼을 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156882581-b995ce3e-9dca-4231-ae9e-34c1cd9140b4.png)

이름은 my-high-performance-application 으로, 배치 전략은 클러스터로 선택하여 그룹을 생성 한다.

클러스터는 하나의 AZ 에 EC2 인스턴스를 배치하는 방식으로 같은 배치 그룹내의 EC2 인스턴스들의 속도는 무척이나 빠르다. 단점으로는 AZ 장애가 발생하면 모든 EC2 에 장애가 발생한다.

![image](https://user-images.githubusercontent.com/67403886/156882648-30ab2f8e-5db8-4be2-954d-3202f47dc5b8.png)

두 번째 배치 그룹을 만든다. 이름은 my-critical-application 로 만들고, 분산 전략을 사용한다.

분산은 클러스터 방식과 정반대이다. 분산에서는 치명적인 장애를 통한 위험을 최소화하는 것이 목적이다.

내가 사용할 수 있는 가용 영역에 각각의 하드웨어와 EC2 인스턴스들이 배치된다. 이렇게 함으로써 하나의 랙(가용 영역)에서 장애가 발생해도 그 영향을 최소화 할 수 있게 했다.

![image](https://user-images.githubusercontent.com/67403886/156883033-c8f3e20c-cceb-4a8a-aa28-35c3cc492cc1.png)

세 번째 배치 그룹을 만든다. 이름은 my-distributed-application 로 만들고, 파티션 전략을 사용한다.

이 배치 그룹에서 몇개의 파티션을 만들지 선택하면 된다. 최대 7개의 파티션을 만들 수 있다. 7개를 선택해서 그룹을 생성한다.

![image](https://user-images.githubusercontent.com/67403886/156883235-f7dc5ccc-874b-43f8-bb5e-700b9f2b8ebb.png)

이 배치 그룹에 인스턴스를 어떻게 설정할 수 있을까..?

일단 EC2 인스턴스를 생성해야 한다. 이전과 동일하게 Amazon Linux 2 AMI 를 선택하고, t2.micro 를 선택한다.

인스턴스 세부 정보 구성을 클릭한다.

![image](https://user-images.githubusercontent.com/67403886/156883377-4128517c-23a2-4c06-8046-fb47983f2aa1.png)

배치 그룹에 인스턴스 추가를 클릭한다.

여기서 새로운 배치그룹을 생성하여 배치 그룹에 인스턴스를 추가거나, 기존에 만들어놓은 배치 그룹에 인스턴스를 추가할 수 있다.

배치 그룹에 인스턴스를 추가하는 것은 이게 끝이다!

![image](https://user-images.githubusercontent.com/67403886/156883557-dc8a9749-a01e-4bb9-bcf5-84cb490019a8.png)

배치 그룹을 사용하지 않는다면 요금이 나가기 때문에 꼭 삭제해주자.
