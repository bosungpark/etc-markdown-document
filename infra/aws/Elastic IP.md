Elastic IP
=

EC2에는 여러 ENI를 붙일 수 있다.
ENI는 하나의 퍼블릭 IPv4 주소를 가진다.
그런데 ENI의 퍼블릭 IP는 계속 변화하게 된다.
그러면 EC2를 정지했다가 재시작하면 기존의 IP주소를 사용할 수 없게 된다.

이 문제를 해결하기 위해 Elastic IP를 사용한다.
Elastic IP를 거쳐 ENI에 부여된 주소는 바뀌지 않는다.
