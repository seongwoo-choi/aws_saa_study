# ElastiCache

- 엘라스티캐시는 Managed Redis, Memcached 이다.
- 인메모리 데이터 스토어로 지연 시간이 1ms 미만인 성능이 아주 좋은 저장소이다. 
- 작동 방식은 RDS 와 유사하며 EC2 인스턴스 유형을 프로비저닝해야 한다. 
- Multi AZ 와 읽기 전용 복제본을 지원한다. 읽기 전용 복제본은 클러스터링을 통해 제공되고 이를 샤딩이라고 부른다.
- IAM, 보안 그룹, KMS 를 사용하여 보안을 유지하고 데이터베이스 자체에 IAM 인증은 없지만 레디스에 요청하면 레디스 AUTH 를 사용은 할 수 있다.
- 백업, 스냅샷 지정 시간 복구, 유지 관리, 작업 처리, 예약이 가능하다.
- RDS 와 비슷하게 모니터링 작업은 CloudWatch 를 사용한다.
- 사용 사례는 주로 Key-Value 형태로 데이터를 저장할 필요가 있을 경우, 혹은 쓰기 작업보다 읽기 작업이 월등히 많은 경우 사용한다. 데이터베이스에서 쿼리한 결과값을 캐시에 저장할 수 있는데 이를 write mode pattern 이라고 부른다. 웹사이트의 세션 데이터를 저장해야 할 경우에도 사용한다. 거의 캐싱을 위해 사용한다고 봐도 상관 없다.

### ElatiCache for Solutions Architect

- Operations: RDS 와 동일하다.
- Security: IAM 인증을 사용하지 않는다는 점과 Redis AUTH 를 사용할 수 있다는 점을 빼면 RDS 와 동일하다.
- Reliability: Clustering, Multi AZ, 샤딩 등을 사용하여 신뢰성을 높인다.
- Performance: 지연 시간이 1ms 미만이며, 인메모리이고 읽기 전용 복제본으로 샤딩이 가능해서 캐시용으로 많이 사용한다.
- Cost: RDS 와 동일하다.