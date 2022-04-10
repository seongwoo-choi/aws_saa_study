# S3 Analytics

- Standard 클래스에서 Standard-IA 로 언제 객체를 보낼지 결정하기 위해 S3 애널리틱스를 설정할 수 있다.
- 즉, 며칠 후에 객체를 보내는 것이 좋은지 계산하는 것이다.
- OneZone-IA 나 Glacier 에는 설정할 수 없다. 오직 Standard 로 부터 Standard-IA 로 보낼 때만 사용 가능하다.
- 이 보고서를 활성화하면 매일 정보들이 업데이트된다.
- 처음 활성화할 때는 첫 시작까지 24~48 시간이 소요된다. 
- 수명 주기 규칙을 구축하거나 개선하기 위한 첫 단계는 Standard 에서 Standard-IA 로 객체를 언제 이동시키는 것이 좋은지 알아내는 것이고 이를 위해서는 S3 Analytics 를 활성화시켜야 한다.