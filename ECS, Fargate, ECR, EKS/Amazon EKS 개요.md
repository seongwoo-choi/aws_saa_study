# Amazon EKS 개요

- Amazon Elastic Kubernetes Service 로 아마존에서 관리형 쿠버네티스 클러스터를 실행하는 방법이다.
- 쿠버네티스는 컨테이너화 된 애플리케이션을 자동으로 배포, 스케일링 관리할 수 있다. ECS 의 대안으로 사용되며 컨테이너를 실행하려는 목적은 비슷하지만 API 는 아주 다르다.
- EC2 인스턴스 등 워크 노드를 배치할 때는 EC2 인스턴스를 사용하고, EKS 클러스터에 서버리스 컨테이너를 배치할 때는 Fargate 를 사용한다.
- 주로 온프레미스에서 쿠버네티스를 사용하거나, 다른 클라우드에서 쿠버네티스를 사용하거나, 쿠버네티스 API 를 사용하거나, AWS 의 쿠버네티스 클러스터를 관리하고자 할 때 Amazon EKS 를 사용한다.
- 쿠버네티스는 Azure, GCP 등 어떤 클라우드에서 사용 가능하다. 즉, 클라우드나 컨테이너 사이를 옮겨 다니려면 Amazon EKS 를 사용하는 게 훨씬 편리하다.