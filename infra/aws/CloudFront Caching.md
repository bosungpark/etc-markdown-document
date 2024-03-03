CloudFront Caching
=

https://youtu.be/oa-6f8QyFyo?si=qQRI4KUIUUGRQl7D

2 티어로 캐싱이 구성
edge location -> regional edge cache -> origin의 순으로 구성

클라우드 프론트의 캐시 키(경로, 쿼리 스트링, 쿠키, 헤더 등)는 어떤 캐시의 내용을 보여줄지 결정하는 정보의 조합. 쓸데없는 키는 지양하고 필요한 부분을 잘 구성하는 것이 중요

헤더는 언어, 장치, 지역별 캐싱을 지원한다.

쿠키 기반으로도 같은 쿼리스트링과 주소를 가지는 경우에도 변별력있는 조회가 가능하다. 

캐시는 ttl 기간(기본 24시간) 이후 만료.
