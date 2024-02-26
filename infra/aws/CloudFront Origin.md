CloudFront Origin
-

https://youtu.be/Vq7DFKZIllI?si=WoaD6YfQZp7OYFyW

원본 
-
뷰어에게 보여줄 컨텐츠의 원본이 있는 거점 (S3 Origin, Custom Origin)


S3 Origin
-
반드시 버킷명 + s3 + region + amazonaws.com 의 형식의 도메인 형식을 가져야 한다.
s3에 별도의 접근제한이 가능
Post/Put 등으로 직접 s3 컨텐츠 업데이트 가능
S3 obj lambda 등의 기능 사용 가능

Custom Origin
-
S3 Origin을 제외한 모든 원본
여러 Origin을 그룹으로 묶어 시나리오에 대응 가능
IP주소는 사용 불가능

Origin Group
-
실패관리를 위해 primary, secondary의 그룹으로 묶어서 관리하는 기능
실패한 경우 자동으로 secondary에 요청

Origin Custom Header
-
CloudFront에서 Origin으로 요청시 추가적인 헤더를 설정 가능
