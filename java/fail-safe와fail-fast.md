# 자바 Iterator 에서 fail-fast 와 fail-safe 란?

## fail-safe
"fail-safe" 란 엔지니어링 분야에서 손상이 없거나 최소한의 방식으로 실패하는 것을 의미한다.
자바에는 fail-safe iterator 와 같은 것은 없다. iterator 가 실패하면 손상이 발생할 것으로 예상할 수 있다.
자바에서 fail-safe 는 실제로 "weakly consistent(약한 일관성)" iterator를 의미한다.
```
대부분의 동시 Collection 구현 (대부분의 대기열 포함)도 반복기 및 분할기가 빠른 실패 순회보다는 약한 일관성을 제공한다는 점에서 일반적인 java.util 규칙과 다릅니다. - javadoc
```
일반적으로 약한 일관성은 컬렉션이 반복과 동시에 수정되는 경우 반복이 보는것에 대한 보장이 약하다는 것을 의미한다.


## fail-fast
시스템 설계에서 "fail-fast"은 너무 많은 손상이 발생하기 전에 장애 상태가(가능한 경우) 감지 되도록 장애상태를 적극적으로 확인 함을 의미한다.
자바에서 fail-fast 의 사례로 iterator의 생성 이후에 list의 변형이 일어날때 ConcurrentModificationException이 발생하는것을 의미한다.

"fail-fast" 및 "weakly consistency(약한 일관성 또는 fail-safe)"란 반복시 예기치 않게 실패하는 대안에 대한 의미론적인 개념이다.
