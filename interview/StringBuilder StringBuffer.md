StringBuilder 와 StringBuffer의 차이는 무엇일까요?

StringBuilder의 사용법
```java
StringBuilder sb = new StringBuilder();
sb.append("ABC");
sb.append("DEF");
System.out.println(sb.toString());
```

- StringBuilder에는 append()로 문자열을 더하고 toString()으로 부른다.

- StringBuilder는 동기화를 지원하지 않는 반면, StringBuffer는 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작할 수 있습니다.
- 그 이유는 StringBuffer는 메서드에서 synchronized 키워드를 사용하기 때문입니다.
- java에서 synchronized 키워드는 여러개의 스레드가 한 개의 자원에 접근할려고 할 때, 현재 데이터를 사용하고 있는 스레드를 제외하고 나머지 스레드들이 데이터에 접근할 수 없도록 막는 역할을 수행합니다.
- StringBuilder는 동기화를 지원하지 않는 반면, 속도면에선 StringBuffer 보다 성능이 좋습니다.
- 그렇기 때문에 우리는 단일 스레드 환경 과 문자열의 추가, 수정, 삭제 등이 빈번히 발생하는 경우 StringBuilder를 사용하는 것이 성능면에서 유리할 것입니다.
- StringBuffer는 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작할 수 있습니다.
- 그렇기 때문에 우리는 멀티 스레드 환경 과 문자열의 추가, 수정, 삭제 등이 빈번히 발생하는 경우 StringBuffer를 사용하는 것이 성능면에서 유리할 것입니다.
- 응답시간
 
 StringBuffer > StringBuilder
 
 - 메모리

StringBuffer == StringBuilder
