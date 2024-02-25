https://codeconfessions.substack.com/p/cpython-dynamic-dispatch-internals

“a + b” 같은 동작을 하기위해 파이썬의 런타임에 벌어지는 일을 알아보자.
a와 b의 타입이 +의 행동을 결정한다.
모든 파이썬은 타입은 +를 구현하고 있다. 그리고 파이썬의 인터프리터는 적절한 구현체를 찾아 연산을 실행한다.
이 과정을 dynamic dispatch라고 부른다.

<img width="1254" alt="스크린샷 2023-12-12 오후 12 37 59" src="https://github.com/bosungpark/paper-markdown-document/assets/81157873/68be75c2-b85d-4d5f-93c1-9d3076df3a30">

위의 사진을 대략적으로 설명하면 다음과 같다.
파이썬은 스택기반의 vm에 컴파일된 바이트코드를 쌓는다.
cpython은 객체를 추상화하여, vm단에서는 구체적인 객체에 구현에 대해 알지 못한 채로 실행이 가능하다.

dynamic dispatch에 대해 알기 전에, PyTypeObject를 먼저 이해할 필요가 있다.
PyTypeObject는 cpython의 2차적으로 적용되는 객체이다.
런타임의 타입(PyTypeObject)에 관한 정보, 레퍼런스 카운트에 관한 정보를 포함하고 있다.
또 모든 타입은 PyTypeObject에 대한 정보를 담고 있다.
이는 모든 타입 객체는 PyTypeObject로 형변환이 가능하다는 의미이다.

[PyTypeObject]
<img width="744" alt="스크린샷 2023-12-12 오후 12 48 42" src="https://github.com/bosungpark/paper-markdown-document/assets/81157873/3f8e2aec-4070-4167-9f1b-b8359b69c2bd">

[type obj]
<img width="750" alt="스크린샷 2023-12-12 오후 12 49 30" src="https://github.com/bosungpark/paper-markdown-document/assets/81157873/65d55ff6-a5a5-496c-8a52-1e557955f392">

PyTypeObject 객체는 런타임 타입에 대한 디테일(타입의 이름,사이즈, 할당하고 할당을 해제할 때 사용할 함수 등등)을 가지고 있는 다소 크고 복잡한 객체이다.
PyTypeObject에 있는 함수의 포인터 테이블에 따라, 각 타입이 구현하고 있는 연산자 함수를 찾아 연산을 실행한다.

[요약]
1. 각각의 타입은 헤더에 형변홤 함수의 포인터를 저장한다.
2. vm은 추상화된 인터페이스에 따라 함수를 호출한다.
3. 추상화된 객체는 포인터 테이블을 사용해 연산을 한다.
