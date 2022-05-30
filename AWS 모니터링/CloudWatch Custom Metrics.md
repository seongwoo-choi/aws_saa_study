# CloudWatch Custom Metrics

- CloudWatch 에서 직접 metrics 를 정의해서 커스텀하게 지표를 가져올 수 있다.
- 메모리 사용량, 디스크 공간, 애플리케이션에 로그인한 사용자 수 등을 CloudWatch 의 metrics 로 사용하고 싶다면 put-metric-data 라는 API 를 사용하여 metrics 배열에 추가할 수 있다.
- 기본은 1분마다 metrics 을 수집하는 것이지만 돈을 더 내서 1/5/10/30 초 마다 metrics 을 수집할 수 있다.
- 중요한 점은 과거나 미래의 metrics 를 수집할 수 있다는 점이다. 2주 전이나 2시간 후의 metrics 를 push 한다고 해도 CloudWatch 에서 오류가 발생하지 않는다. push 된 metrics 그대로를 받아들인다.