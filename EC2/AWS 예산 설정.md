# AWS 요금 설정

AWS 에서 돈을 최소한으로 사용하거나 아예 안쓰도록 해야한다.

돈을 지불하게 하는 것들이 존재하는지 확인하는 방법이 있다.

하지만 갖은 노력을 해도 결제 예산을 설정하는 것이 좋다. 왜냐하면 일정 지출 이상을 하게 될 때가 있기 때문이다.

우상단에 내 계정을 클릭하여 결제  대시보드를 클릭하여 연다.

<img width="705" alt="image" src="https://user-images.githubusercontent.com/67403886/156128735-cc73e9c2-df08-4aaf-bf47-453c35d459fd.png">


IAM 사용자로는 결제 대시보드에 접근할 수 없다.

만약 접근하고 싶다면 루트 계정으로 로그인해야 한다. 계정을 클릭한 후에 계정을 클릭한다. 아래로 쭉 내리다보면 IAM 사용자 및 역할 접근이라는 설정을 찾을 수 있다.

<img width="599" alt="image" src="https://user-images.githubusercontent.com/67403886/156128774-2522ca9b-5b98-4c64-9e86-4a50b457e2ba.png">


편집 버튼을 클릭하고 IAM 접근을 활성화 시키면 IAM 사용자가 결제 대시보드에 접근할 수 있게 된다.

<img width="673" alt="image" src="https://user-images.githubusercontent.com/67403886/156128805-704cdb6f-8c17-491c-9c9a-279d4b280260.png">


결제 대시보드에서 청구서를 클릭하면 월별 요금표를 확인할 수 있다. 2월달에 0.11 달러를 지불했다.

<img width="713" alt="image" src="https://user-images.githubusercontent.com/67403886/156128846-4afd21ff-6f77-461e-af75-321f50bcc57f.png">


계정에 대한 요금이 발생하기 시작할 때 어떤 서비스에 어떤 요금이 발생했는지, 어느 지역에서 어떻게 발생했는지 파악하는 방법을 이해할 수 있어야 한다.

사진에 나온 것처럼 RDS 서비스, Aisa Pacific (Seoul) 지역에서 요금이 발생했고, 왜 이런 가격이 책정됐는지에 대한 분석도 제공해준다. 그래서 보다시피 Amazon Relational Database Service Backup Storage 작업으로 인해 요금이 발생한 것을 확인할 수 있다.

그래서 이러한 정보는 AWS 계정에 일부 요금이 부과되는 이유를 이해하고 요금을 발생시키는 리소스를 끄거나 삭제하는데 필요한 정보를 제공한다.
