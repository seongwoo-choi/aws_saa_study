# SQS - Message Visibility Timeout

Message Visibility Timeout 라는 중요한 개념을 알아야 한다.

consumer 가 메시지를 폴링하면 그 메세지는 다른 소비자들에게 보이지 않게 된다. 

기본 Message Visibility Timeout 시간은 30초로 설정되어 있고, consumer 가 메시지를 폴링하는 순간부터 다른 consumer 가 메시지를 요청하는 API 를 보내도 현재 폴링된 메시지가 반환되지 않는다. 언제까지? Message Visibility Timeout 인 30초가 지날 때 까지.

Message Visibility Timeout 이 초과되고 메시지가 처리되지 않아 대기열에서 삭제되지 않은 경우 메시지는 다시 대기열에서 폴링 요청이 올 때 까지 대기한다.

그리고 다른 consumer 가 메시지를 요청하면 해당 메시지가 폴링되게 된다.

즉, 어떤 consumer 가 메시지를 폴링하게 되는 그 순간 부터 Message Visibility Timeout 시간까지 다른 사용자들에게 해당 메시지가 보이지 않는다. 

Message Visibility Timeout 해당 시간 안에 메시지를 처리하지 않으면 메시지가 두 번 처리될 수도 있다는 사실을 알아야 한다. 두 명의 consumer 가 메시지를 수신하거나 동일한 consumer 가 두 번 수신할 수 있다는 뜻이다.

메시지를 Message Visibility Timeout 시간 안에 처리하지 못하고 시간이 좀 더 필요할 경우 ChangeMessageVisibility 라는 API 를 통해 SQS 에게 나 지금 메시지 처리 중이니까 대기열에 이 메시지 보이게 하면 안돼! 라고 말해준다.

Message Visibility Timeout 이 너무 길어도 안되고 너무 짧아도 안된다. 애플리케이션의 알맞는 적절한 시간을 갖춰야 한다.

만약 그럼에도 시간이 모자르다면 ChangeMessageVisibility API 를 호출하도록 프로그래밍을 해야 한다.