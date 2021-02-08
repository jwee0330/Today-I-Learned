### Java 컬렉션 프레임워크의 시간 복잡도
Java Collection API의 다양한 컬렉션 성능을 알아보자
Big-O 표기법을 사용하여 Java Collection API들의 시간복잡도를 표기

#### ArrayList
배열에 의해 구현됨
- add() - O(1)
- add(index, element) - O(n) 의 평균시간
- get() - O(1) 항상 일정
- remove() - O(n), 제거 할 수 있는 요소를 찾기위해 전체 배열을 반복해야 한다
- indexOf() - O(n), 선형 시간으로 실행된다. 내부 배열을 반복하고 각 요소를 하나씩 확인, 항상 O(n) 시간이 필요함
- contains() - O(n), 구현은 indexOf()를 기반으로 한다. 따라서 O(n) 시간에도 실행된다.

#### CopyOnWriteArrayList
이 List 인터페이스 구현은 멀티 스레드 응용 프로그램으로 작업 할 때 매우 유용하다. 스레드로부터 안전함.
- add() - O(n)
- get() - O(1)
- remove() - O(n)
- contains() - O(n)

#### LinkedList
LinkedList는 데이터 필드를 보유하는 노드와 다른 노드에 대한 참조로 구성된 선형 데이터 구조.
- add() - 모든 위치에서 O(1)
- get() - O(n)
- remove() - O(1)
- contains() - O(n)