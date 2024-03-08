Virtual Thread의 기본 개념 이해하기
=

https://d2.naver.com/helloworld/1203723

> 자바 개발자는 아니라 크게 와닿지는 않지만, 문제를 푸는 재미있는 접근인 것 같다.

Heap에 존재하는 많은 ULT 중 하나가 JVM의 스케줄링에 따라 KLT에 매핑되어 실행하는 형태가 기존의 Java 스레드 모델이다.

> 1개의 요청을 1개의 스레드가 처리하므로 동시요청이 많을 때 서버에 부담, 기존 JDK의 스레드는 운영 체제(OS) 스레드의 Wrapper이기 때문에, 사용 가능한 스레드의 수가 하드웨어 수준보다 훨씬 적게 제한, 제한적인 스레드의 수, I/O시에 블로킹이 일어나는 단점 존재

Virtual Thread
-

Virtual Thread는 기존의 KLT(kernel-level thread)와 ULT(user-level thread)를 1:1 매핑하여 사용하는 JVM의 스레드 모델을 개선한, 여러 개의 가상 스레드를 하나의 네이티브 스레드에 할당하여 사용하는 모델

기존의 Java 스레드를 알아보았으니 이제 JDK 21에 새로 도입된 Virtual Thread를 알아보자.

Virtual Thread는 기존 KLT(1) : ULT(1)의 구조가 아닌 KLT(1) : ULT(1) : Virtual Thread(N)의 구조로 사용된다. KLT와 Virtual Thread 사이의 ULT는 플랫폼 스레드라고 한다.

Heap에 수많은 Virtual Thread를 할당해놓고, 플랫폼 스레드에 대상 Virtual Thread를 마운트/언마운트하여 컨텍스트 스위칭을 수행한다. 따라서 컨텍스트 스위칭 비용이 작아질 수 밖에 없다.

기존의 방식은 CPU intensive 환경이 아닌, 네트워크 I/O가 다수 발생하는 웹서버 환경에서는 하나의 호출에 하나의 스레드를 점유하는 기존 Spring MVC/Tomcat 모델은 큰 부담으로 작용했다.

Virtual Thread의 등장은 non-blocking single thread 모델을 사용하지 않아도 된다고 말하고 있다. 실제로 CPU intensive 환경이 아니라면 non-blocking single thread 모델만큼이나 효율을 잘 내고 있다.

> 기존의 하드웨어를 최적으로 사용하지 못하는 이유는 1대 1 대응으로 인한 OS 스레드 사용의 비효율. 따라서 해결 방안은 자바 런타임에서 OS 스레드와 일대일 대응되지 않는 더 효율적인 스레드를 구현해 사용하는 것. 따라서 운영 체제가 많은 가상 주소 공간을 제한된 양의 물리적 RAM에 매핑하여 메모리가 넉넉한 것처럼 보이게 하는 것처럼, 자바 런타임은 많은 수의 가상 스레드를 적은 수의 OS 스레드에 매핑하여 스레드가 넉넉한 것처럼 보이게 하는 것.