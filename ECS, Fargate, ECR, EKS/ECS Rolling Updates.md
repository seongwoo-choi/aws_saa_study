# ECS Rolling Updates

- ECS 서비스를 버전 1에서 버전 2로 업데이트 할 때 한 번에 몇개의 태스크가 실행되고, 누가 먼저 실행되는지 제어할 수 있다. 
- ECS 업데이트를 보면 Minimum healthy percent 와 Maximum percent 를 설정한다. 디폴트 값으로 100, 200을 갖는다.
- Minimum healthy percent 는 ECS 서비스에 실행 중인 태스크가 10개가 있고 이 태스크의 갯수는 실제 실행 가능한 용량이다. Minimum healthy percent 가 50으로 설정될 경우 50% 만큼만 태스크를 ECS 서비스에 띄우겠다는 뜻이다.
- Maximum percent 는 버전 1에서 버전 2로 업데이트 할 때 얼마 만큼 태스크를 생성할지 나타낸다.
- 예를 들어, Min 이 50% 이고 Max 가 100% 이다. 4개의 태스크가 실행된다. 최소가 50% 로 잡혔기 때문에 오래된 태스크 2개가 종료된다. 최대는 100% 로 설정됐기 때문에 다시 2개가 생성된다. 최소가 50% 이기 때문에 또 다시 오래된 태스크 2개가 종료되고, 다시 2개가 생성된다.
- 위처럼 무한히 순환하여 태스크가 생성되는데 이를 롤링 업데이트라고 부른다. 태스크가 종료되고 다시 실행되는 이유는 최소가 50% 최대가 100% 이기 때문이다.