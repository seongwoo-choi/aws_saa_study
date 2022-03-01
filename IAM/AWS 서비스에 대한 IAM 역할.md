## AWS 서비스에 대한 IAM 역할

몇몇 AWS 서비스들은 IAM 사용자들 처럼 몇가지 권한을 가지고 작업을 하게 된다.

이를 위해 IAM 역할을 생성할 것이다. 이 IAM 역할은 사용자와 같지만 실제 사람에 의해 사용되는 것이 아닌 AWS 서비스에서 사용되하도록 되어 있다.

EC2 인스턴스를 만든다고 할 때 EC2 인스턴스는 AWS 에서 몇가지 서비스를 사용하도록 되어 있고, 그렇게 해주기 위해서 EC2 인스턴스에 권한을 줘야 한다. 

<img width="753" alt="image" src="https://user-images.githubusercontent.com/67403886/156121307-3e7ca19a-23ab-4b94-b0c2-27b47177ed86.png">


즉, EC2 인스턴스에게 IAM role 을 만들어주고 EC2 인스턴스가 AWS 의 서비스에 접근하려고 하면 IAM 에 적힌 권한에 따라 접근하거나 접근하지 못하게 되는 것이다.

<img width="707" alt="image" src="https://user-images.githubusercontent.com/67403886/156121327-422a9455-4802-497b-b7c4-08fc1a34f210.png">
