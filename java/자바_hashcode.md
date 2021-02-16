# Java - System.identityHashCode()와 hashCode()의 차이점

백기선님 더자바-개발인터뷰 강의 수강중 미션으로 String, StringBuffer, StringBuilder에 대해 정리하는 미션을 받게 되었습니다.
String의 이런저런 메소드들을 사용하다 String의 hashCode() 메소드는 String 인스턴스의 인스턴스 필드의 문자열 배열에 따라 같은 값을
반환할 수 있도록 오버라이드 되어 있다는 것을 확인하였고, 그럼 ***String 인스턴스는 다른 참조변수들처럼 hashCode를 출력할 수 없는걸까?*** 란
의문이 들었습니다. 결론 부터 말씀드리면 *System 패키지의 static 메소드 중 identityHashCode 를 이용하면 알수있다!* 입니다.
본 포스팅에서는 저와 같은 궁금증을 가지셨던 분들에게 도움이 되었으면 좋겠습니다.
  
---

자바에서 hashCode()는 최상위 Object의 메소드입니다. 편의상 객체의 주소값을 반환한다고 알려져있습니다(정확하게는 다름)
JavaDoc에서는 아래와 같이 설명하고 있습니다.
```text
객체의 hash code 값을 반환하여 java.util.HashMap와 같은
hash tables 형태의 자료구조를 사용할 수 있게 한다.
자바에서 같은 객체의 hashCode() 반환값은 반드시 같은 int 값을 반환하여 일관성을 유지해야 한다.
두 객체의 hashCode() 가 같다면 두 객체는 같다고 말한다. 반대로 두 객체의 hashCode()가 다르면 두 객체는 다르다고 말하지만
특수한 목적을 위해 프로그래머의 의도로 equals 메소드를 재정의하여 두 객체가 같다고 할 수 있다.
```
설명에서 언급된 HashMap에서는 값을 저장하는 put() 메소드의 실행 시, 키의 hashCode()를 이용해서 값이 저장 될 버킷을 결정합니다. 값을 검색하기 위해 hashCode()를 사용하여 동일한 방식으로 버킷을 계산하고, 해당 버킷에서 찾은 객체를 equals() 메서드를 사용하여 검색합니다. 이처럼 자바에서 hashTable 형태의 자료구조는 hashCode() 를 사용하여 키를 만들기 때문에 **키의 불변성**을 지켜야 자료구조의 일관성을 유지할 수 있습니다.

*참고:hash table의 자료구조에 대해 더 궁금하신 분들을 위해*
- [HashTable 이란?](https://en.wikipedia.org/wiki/Hash_table)
- [HashMap Search really O1?](https://stackoverflow.com/questions/1055243/is-a-java-hashmap-search-really-o1)
- [Java HashMap](https://www.baeldung.com/java-hashmap)

자바에서는 HashTable 자료구조의 키로 String을 사용할 수 있고, 이 때문에 String 클래스에는 hashCode()를 오버라이드 하여 리터럴이 같으면 같은 값을 반환할 수 있도록 하였습니다. 실제 사용할 가능성은 적지만 리터럴이 같다면 new 를 이용해 새로운 인스턴스를 생성하여 메모리상 주소값이 다른 경우에도 hashCode()의 반환값은 일치하게 되어있습니다. 이럴때 실제 객체의 hash code 값을 확인하기 위한 메소드가 System.identityHashCode() 입니다.
아래의 예제 코드를 보시는 쪽이 이해하시는데 더 도움이 될거라 생각합니다.
```java
String a = new String("java");
String b = new String("java");
String c = new String("java");

assertThat(a.equals(b)).isTrue();
assertThat(b.equals(c)).isTrue();
assertThat(c.equals(a)).isTrue();

assertThat(a == b).isFalse();
assertThat(b == c).isFalse();
assertThat(c == a).isFalse();

assertThat(a.hashCode() == b.hashCode()).isTrue();
assertThat(b.hashCode() == c.hashCode()).isTrue();
assertThat(c.hashCode() == a.hashCode()).isTrue();

assertThat(System.identityHashCode(c) == System.identityHashCode(a)).isFalse();
assertThat(System.identityHashCode(a) == System.identityHashCode(b)).isFalse();
assertThat(System.identityHashCode(b) == System.identityHashCode(c)).isFalse();
```
String 클래스에서 hashCode 메소드는 오버라이드 되어 있기 때문에
String 인스턴스가 다르더라도 같은 문자열을 갖고있다면 같은 값을 반환합니다.
그러나 System.identityHashCode()를 이용하면 실제 객체의 hashCode를 반환하여 비교연산자 == 를 통한 레퍼런스 비교 결과 같은 결과를 나타나게 합니다.

---

Object 클래스의 hashCode() 메소드와 System.identityHashCode()의 차이점을 알아보았습니다.
제 생각에 실무에서 System.identityHashCode()를 사용할 일이 거의 없을것 같습니다. 생성하는 객체의 hashCode()를 목적에 따라 적절하게 오버라이드 하고 개발자의 의도하에 관리하여야 한다고 생각합니다. 필요에 따라서는 hashCode()를 사용하는 equals() 메소드 또한 적절한 변형이 추가되야 할 것입니다. 자바 개발자라면 필독서인 Effective Java 3판의 item11. Always override hashCode when you override equals 의 맥락과 궤를 같이 한다고 생각합니다.
오랜만에 이펙티브 자바에서 학습했던 내용과 연계하여 생각해 볼 수 있는 좋은 시간이었습니다.

참고
- [Java API Documentation](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/lang/System.html#identityHashCode(java.lang.Object))