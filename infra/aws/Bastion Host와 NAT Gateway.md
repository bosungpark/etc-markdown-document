Bastion Host와 NAT Gateway
=

https://youtu.be/lqnncuQgz28?si=969RR63tPGgALOCl

프라이빗 서브넷은 외부의 노출을 거부하는 특성.
프라이빗 서브넷에 접근시 생기는 불편함을 해소하기 위한 요소로 Bastion Host와 NAT Gateway가 존재한다.

NAT Instance/Gateway
-
private instance가 외부의 인터넷과 통신하기 위한 통로이다.
프라이빗 서브넷과 같은 VPC에 있는 퍼블릭 서브넷에 외부와의 대리 통신을 부탁하는 것.

NAT Instance는 단일 인스턴스(EC2), NAT Gateway는 AWS에서 제공하는 서비스라는 차이가 있다.

Bastion Host
-
private instance에 접근하기 위한 인스턴스.
