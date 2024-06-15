Advanced Golang: Limiting Goroutines
=

https://youtu.be/tSjnf6l8cq8?si=IzRaB2s4UnmrJ8Nm

goroutine을 이용할 때, oom kill을 방지하기 위한 방법
-

버퍼드 채널을 사용한다면, 버퍼가 찰 때 블락킹한 방식으로 동작하므로 앞단에 큐를 두는 것과 같은 효과를 매우 간단하게 얻을 수 있다.
