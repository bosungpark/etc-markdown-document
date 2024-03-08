CloudFront Behavior
=

https://youtu.be/Z3lxE9rUsZo?si=F-8UrsRJAEiG5R2Q

캐시 동작
-

- 클라우드 프론트의 요청이 어떻게 처리되는지 정의하는 다양한 설정의 모음
- 경로 패턴 단위로 Behavior 구성
- 경로 패턴 목록 중 처음으로 매칭된 패턴의 동작을 적용
- 신규 생성시 *로 고정

Viewer 설정
-

- 클라우드 프론트에 접근하는 프로토콜 (HTTP, HTTPS, 복합, HTTPS 리다이렉션 등)
- HTTP 메서드
- 뷰어 접근 제한 (Presigned URL, Presigned Cookie)

Poclicy 설정
-

1. Cache Poclicy
- 어떤 키로 컨텐츠를 캐시하는지
- 얼마나 오래 캐시하는지 
- 컨텐츠 압축 저장 설정

2. Origin Request Poclicy
- 오리진에 컨텐츠를 전달할 때 어떤 내용을 전달할지 (HTTP Header, querystring...)
- 캐시 키로 사용할지 안할지

3. Response Header Poclicy
- 응답과정에서 HTTP Header를 더할지 뺄지



