`System.out.println` 메소드는 현업에서 절대 쓰지 말라고하는 메소드인데요. 그 이유가 무엇일까요?
`System.out.println()` 의 구현
```java
public void println(){
  newLine();
}
```
`println()`은 `newLine()`을 호출한다. 
`newLine()`의 구현
```java
private void newLine(){
  try{
    synchronized (this) {
      ensureOpen();
      textOut.newLine();
    // ...
```
`synchronized` 키워드가 붙어있다. 이때 `newLine()` 메소드는 `임계영역(critical section)`이 된다. 
- 임계영역 : 멀티 스레드 프로그램에서 단 하나의 스레드만 실행할 수 있는 코드 영역
- 멀티 쓰레드 환경에서 A 쓰레드가 `newLine()` 메소드를 실행하면, 메소드는 잠기게 된다. 
- 다른 쓰레드는 A 쓰레드가 모두 사용하고 잠금을 풀어준 뒤에서야 `newLine()` 메소드를 실행할 수 있다. 오버헤드가 발생하게 되는 것 이다.
- 스프링을 실행하는 톰캣은 멀티 쓰레드로 동작한다. 요청이 오면 쓰레드 풀에서 쓰레드를 하나 가져와 요청을 처리한다. 
- 그런데, `System.out.println()` 을 여러 쓰레드가 사용하면 그만큼 위에서 이야기한 오버헤드가 발생하고 처리가 느려질 것 이다. 
- 따라서 실제 프로덕트의 코드에서는 `System.out.println()` 을 절대 사용해서는 안된다.
