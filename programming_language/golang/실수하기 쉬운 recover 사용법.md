실수하기 쉬운 recover 사용법
=

https://go.dev/ref/spec#Handling_panics

<img width="1192" alt="스크린샷 2024-11-15 오후 11 54 53" src="https://github.com/user-attachments/assets/77f4f00f-e5ae-4ed0-9437-43747f693215">

**요약**
1. recover는 패닉이 일어난 지점을 기준으로 n+1 되는 지점에 위치해야 한다.
2. 예를 들어 고루틴인 G함수와 defer 함수를 선언하고, G함수 안에서 패닉이 발생한다면 recover 로직은 defer 함수안에 바로 위치 해야한다.
3. 만약, recover을 커스텀하게 사용하고 싶다던가 하는 이유로, customRecover라는 유틸성 함수를 만들고 defer안에서 customRecover를 호출한다면 패닉은 복구되지 못할 것이다.