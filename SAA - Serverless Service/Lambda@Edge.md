# Lambda@Edge

- 엣지 로케이션 마다 글로벌 람다 함수를 실행하고 싶을 때 사용한다.
- Lambda@Edge 는 CloudFront CDN 을 통해서 특정 리전이 아닌 전 세계의 모든 리전에 람다 함수를 배치한다. -> 응답성이 뛰어난 애플리케이션을 구축하기 위해서이다.
- 서버리스 서비스이기 때문에 서버를 관리할 필요가 없으며 CDN 을 통해 전송되는 컨텐츠를 사용자가 지정할 수 있고 온디맨드 바탕이기 때문에 사용한만큼 돈을 지불한다.
- Lambda@Edge 를 사용하여 CloudFront 로 오는 request 와 response 를 변경한다.
- Lambda@Edge 에는 4가지 람다 함수가 있다.
  - viewer request: viewer request 의 경우 CloudFront 가 사용자로부터 request 를 수신하면 람다 함수를 통해 request 를 수정한다.
  - origin request: CloudFront 가 origin 으로 request 를 전달하기 이전 단계에서 람다 함수를 통해 request 를 수정한다.
  - origin response: CloudFront 가 origin 으로부터 response 를 수신할 때 이뤄지며 해당 단계에서 람다 함수를 통해 response 를 수정한다.
  - viewer response: CloudFront 가 response 를 viewer 로 전달하기 전에 람다 함수를 통해 response 를 수정한다. 그래서 origin 으로 request 를 보내지 않더라도 viewer 로 보내는 response 를 만들어 보낼 수 있다.

### Lambda@Edge: Global application

S3 에 정적 웹사이트가 호스팅 되고 웹사이트에 사용자가 방문하면 클라이언트 측의 자바스크립트를 통해 CloudFront 로 API 요청을 보내고 CloudFront 는 전 세계의 엣지 로케이션에서 실행되는 Lambda@Edge 함수를 실행한다.

람다 함수는 다이나모 DB 의 데이터를 쿼리할 수 있게 된다.

### Lambda@Edge 사용 예시

Lambda@Edge 는 웹사이트 보안 및 동적 웹 애플리케이션에서 검색 엔진 최적화, 오리진과 데이터 센터 사이에서 인텔리한 경로 찾기, 실시간 이미지 변환, 오리진 도달 전에 사용자 인증 및 권한 부여, 사용자 우선순위 지정, 사용자 추적 및 분석 등을 위해 사용된다.

Lambda@Edge 는 람다 함수와 CloudFront 를 통합해서 viewer, origin 의 req, res 를 수정하는 경우 사용한다.