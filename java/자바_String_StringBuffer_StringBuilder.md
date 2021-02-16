# String, StrignBuffer, StringBuilder

# String 클래스
## String 클래스는 char 배열에 기능을 추가한 것이다.
C언어에서는 문자열을 char배열로 다루지만, 객체지향언어인 자바에서는 char배열과 그에 관련된 기능들을 함께 묶어서
클래스에 정의한다. 객체지향개념이 나오기 이전의 언어들은 데이터와 기능을 따로 다루었지만, 객체지향언어에서는 데이터와
기능을 따로 다루었지만, 객체지향언어에서는 데이터와 그에 관련된 기능을 하나의 클래스에 묶어서 다룰 수 있게
한다. 즉, 서로 관련된 것들끼리 데이터와 기능을 구분하지 않고 함께 묶는 것이다.  
  여기서 말하는 기능은 함수를 의미하며, 메서드는 객체지향 언어에서 함수 대신 사용하는 용어일 뿐 함수와 같은 뜻이다.  
 char배열과 String 클래스의 한 가지 중요한 차이가 있는데, String객체(문자열)는 읽을수만 있을 뿐 내용을 변경할 수 없다.  
```java
String str = "Java";
str = str + "8";            // "Java8"이라는 새로운 문자열이 str에 저장된다.
System.out.println(str);    // "Java8"
``` 
위의 문장에서 문자열 str의 내용이 변경되는 것 같지만, 문자열은 변경할 수 없으므로 새로운 내용의 문자열이 생성된다.  
***[참고] 변경 가능한 문자열을 다루려면, StringBuffer클래스를 사용하면 된다.***

## String클래스의 주요 메서드
|메서드|설명|
|------|----|
| char charAt(index) | 문자열에서 해당 위치(index)에 있는 문자를 반환한다. |
| int compareTo(String str) | str과 사전순서로 비교한다, 같으면 0, 사전순 이전이면 1, 이후면 -1을 반환 |
| String concat(String str) | 입력받은 str은 문자열 뒤에 덧붙인다 |
| boolean contains(CharSequence s) | 지졍된 문자열이 포함되어있는지 검사 |
| boolean startWith(String s) | 지정된 문자열로 시작하는지 검사 |
| boolean endWith(String s) | 지정된 문자열로 끝나는지 검사 |
| boolean equals(String str) | 문자열의 내용이 같은지 확인한다. 같으면 결과는 true, 다르면 false가 된다. |
| boolean equalsIgnoreCase(String str) | 대소문자 구분없이 비교 |
| int indexOf(int ch) | 주어진 문자가 문자열에 존재하는지 확인하여 인덱스를 반환, 못찾으면 -1 반환 |
| int indexOf(int ch, int pos) | 주어진 문자가 문자열에 존재하는지 입력받은 pos 위치부터 확인하여 인덱스를 반환, 못찾으면 -1 반환 |
| int indexOf(String s) | 주어진 문자열이 확인하여 인덱스를 반환, 못찾으면 -1 반환 |
| int lastIndexOf(int ch) | 지정된 문자 또는 문자코드를 문자열의 오른쪽 끝에서부터 찾아서 위치를 반환, 못찾으면 -1 반환 |
| int lastIndexOf(String s) | 지정된 문자열을 문자열의 오른쪽 끝에서부터 찾아서 위치를 반환, 못찾으면 -1 반환 |
| String intern() | 문자열을 상수풀에 등록한다. 이미 상수풀에 같은 내용의 문자열이 있을 경우 그 문자열의 주소값을 반환한다 |
| char[] toCharArray() | 문자열을 문자배열(char[])로 변환해서 반환한다. |
| int length() | 문자열의 길이를 반환한다 |
| String replace(char old, char new) | 문자열 중의 문자를 새로운 문자로 바꾼 문자열을 반환한다 |
| String replace(CharSequence old, CharSequence new) | 문자열 중의 문자를 새로운 문자로 바꾼 문자열을 반환한다 |
| String replaceAll(String regex, String replacement) | 문자열중에서 지정된 문자열과 일치하는 것을 새로운 문자열로 모두 변경 |
| String replaceFirst(String regex, String replacement) | 문자열중에서 지정된 문자열과 일치하는 것 중 첫번째 것만 새로운 문자열로 모두 변경 |
| String[] split(String regex) | 문자열을 지정된 분리자로 나누어 문자열 배열에 담아 반환 |
| String[] split(String regex, int limit) | 문자열을 지정된 분리자로 나누어 문자열 배열에 담아 반환. 단, 문자열 전체를 지정된 수로 자른다 | 
| String substring(int begin) | 문자열에서 begin 부터 끝에 있는 문자열을 반환한다. |
| String substring(int from, int to) | 문자열에서 해당 범위(from~to)에 있는 문자열을 반환한다. (to는 범위에 포함되지 않음) |
| String toLowerCase() | String 인스턴스에 저장되어 있는 모든 문자열을 소문자로 변환하여 반환 |
| String toUpperCase() | String 인스턴스에 저장되어 있는 모든 문자열을 대문자로 변환하여 반환 |
| String toString() | String인스턴스에 저장되어 있는 문자열을 반환 |
| String trim() | 문자열의 왼쪽 끝과 오른쪽 끝에 있는 공백을 없앤 결과를 반환 (중간 공백은 제거되지 않음) |
| static String valueOf(boolean b) | 지정된 값을 문자열로 반환하여 반환, 참조변수일 경우 toString()을 호출한 결과를 반환 |
| static String valueOf(char c) | |
| static String valueOf(int i) | |
| static String valueOf(long l) | |
| static String valueOf(float f) | |
| static String valueOf(double d) | |
| static String valueOf(Object o) | |

## join(), StringJoiner 사용 예
Java8에 추가된 static String join(String join, String[] existing), java.util.StringJoiner
```java
# static String join(String join, String[] existing);
String animals = "dog,cat,bear";
String arr = animals.split(",");
String result = String.join("-", arr); 
# result = "dog-cat-bear"

# java.util.StringJoiner
StringJoiner sj = new StringJoiner("/", "[", "]");
for(String s: arr) {
    sj.add(s);
}
String reuslt2 = sj.toString();
# result2 = "[dog/cat/bear]"
```

## 유니코드와 보충문자
String 메서드 들중 매개변수 타입이 char인 것들이 있고, int인 것들도 있다. 확장된 유니코드를 다루기 위해서 int 매개변수를 사용
유니코드는 원래 2byte(16bit) 문자체계인데, 모자라게되어 20bit로 확장하게 되었다. 그래서 하나의 문자를 char 타입으로 다루지 못하고, 
int 타입으로 다룰 수밖에 없다. 확장에 의해 새로 추가된 문자들을 '보충 문자(supplementary characters)'라고 하는데, String 클래스의 메서드 중에서는
보충 문자를 지원하는 것이 있고 지원하지 않는 것도 있다. 보충문자를 지원하는 메소드는 매개변수 타입이 int 이다.
참고로 확장된 유니코드는 JDK1.5 부터 지원하였다.

## 문자 인코딩 변환
getByte(String charsetName) 을 사용하면 문자열의 문자 인코딩을 다른 인코딩으로 변경할 수 있다.
자바는 UTF-16을 사용하지만, 문자열 리터럴에 포함되는 문자들은 OS의 인코딩을 사용한다.
참고로 한글 윈도우즈는 CP949를 사용하고, 사용가능한 문자 인코딩 목록은 java.nio.charset.Charset.availableCharsets() 에서 확인할 수 있다.
```java
byte[] utf8_str = "가나다".getBytes("UTF-8");
String str = new String(utf8_str, "UTF-8");
```

# StringBuffer 클래스
String클래스는 인스턴스를 생성할 때 지정된 문자열을 변경할 수 없지만 StringBuffer클래스는 변경이 가능하다. 내부적으로 문자열 편집을 위한 버퍼를 가지고 있으며, StringBuffer인스턴스를 생성할 때 그 크기를 지정할 수 있다. 편집할 문자열의 길이를 고려하여 버퍼의 길이를 충분히 잡아주는게 성능상 좋다. 편집 중인 문자열이 버퍼의 길이를 넘어서게 되면 버퍼의 길이를 늘려주는 작업이 추가로 수행되어 작업의 효율을 떨어트리기 때문이다. StringBuffer클래스는 String클래스와 거의 비슷하다. 차이점은 append() 메서드를 통해 같은 참조의 내용을 변경할 수 있다는 점이다.
```java
StringBuffer sb1 = new StringBuffer("abc");
StringBuffer sb2 = new StringBuffer("abc");

assertThat(sb1 == sb2).isFalse();
assertThat(sb1.equals(sb2)).isFalse();
assertThat(sb1.toString().equals(sb2.toString())).isTrue();
```

## 주요 메서드
|메서드|설명|
|------|----|
|StringBuffer()|16문자를 담을 수 있는 버퍼를 가진 StringBuffer인스턴스를 생성한다|
|StringBuffer(int length)|지정된 개수의 문자를 담을 수 있는 버퍼를 가진 StringBuffer인스턴스를 생성한다|
|StringBuffer(String str)|입력된 문자열을 값으로 갖는StringBuffer인스턴스를 생성한다|
|StringBuffer append(boolean b)| 매개변수로 입력된 값을 문자열로 변환하여 StringBuffer인스턴스가 저장하고 있는 문자열 뒤에 덧붙이고 자신을 반환한다 |
|StringBuffer append(char c)| |
|StringBuffer append(char[] str)| |
|StringBuffer append(double d)| |
|StringBuffer append(float f)| |
|StringBuffer append(int i)| |
|StringBuffer append(long l)| |
|StringBuffer append(Object obj)| |
|StringBuffer append(String str)| |
|int capacity()|StringBuffer인스턴스의 버퍼크기를 반환, length와 다름|
|int length()|StringBuffer인스턴스에 저장되어 있는 문자열의 길이를 반환|
|char charAt(int index)|해당 위치에 있는 문자를 반환|
|StringBuffer delete(int start, int end)|start<= 범위 < end 사이에 있는 문자를 제거한다|
|StringBuffer deleteCharAt(int index)|지정된 위치의 문자를 제거한다|
|StringBuffer insert(int pos, boolean b)|두 번째 매개변수로 받은 값을 문자열로 변환하여 지정된 위치에 추가한다|
|StringBuffer insert(int pos, char c)||
|StringBuffer insert(int pos, char[] str)||
|StringBuffer insert(int pos, double d)||
|StringBuffer insert(int pos, float f)||
|StringBuffer insert(int pos, int i)||
|StringBuffer insert(int pos, long l)||
|StringBuffer insert(int pos, Object obj)||
|StringBuffer insert(int pos, String str)||
|StringBuffer replace(int start, int end, String str)|start <= 범위 < end 범위의 문자들을 주어진 문자열로 바꾼다|
|StringBuffer reverse()|StringBuffer인스턴스에 저장되어 있는 문자열의 순서를 거꾸로 나열한다|
|void setCharAt(int index, char ch)|지정된 위치의 문자를 주어진 문자로 바꾼다|
|void setLength(int newLength)|지정된 길이로 문자열의 길이를 변경한다. 길이를 늘릴 경우 빈공간을 널문자 '\u0000'로 채운다|
|String toString()|StringBuffer인스턴스의 문자열을 String으로 반환한다|
|String substring(int start)|시작위치부터 문자열 끝까지 뽑아서 반환한다|
|String substring(int start, int end)|start <= 범위 < end 내의 지정된 문자열을 String으로 뽑아서 반환한다|

# StringBuilder 클래스
StringBuffer는 멀티쓰레드에 안전하도록 동기화 되어 있다. 그러나 동기화는 성능을 떨어트리기 때문에. 싱글스레드 환경에서 성능 최적화가 필요한 상황에서
굳이 StringBuffer를 사용해서 성능저하를 일으킬 필요가 없다. 이런 상황을 위해 탄생한 클래스가 바로 StringBuilder이다. StringBuilder는 StringBuffer에서 쓰레기 동기화 부분만 뺀 기능은 동일한 클래스이다. 하지만 StringBuffer도 충분히 성능이 좋기 때문에 성능향상이 반드시 필요한 경우를 제외하고는 StringBuilder로 굳이 바꿀 필요는 없다.

