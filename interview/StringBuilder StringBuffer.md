StringBuilder 와 StringBuffer의 차이는 무엇일까요?
StringBuilder
```java
StringBuilder sb = new StringBuilder();
sb.append("ABC");
sb.append("DEF");
System.out.println(sb.toString());
```
StringBuilder에는 append()로 문자열을 더하고 toString()으로 부른다.
