`System.out.println` 메소드는 현업에서 절대 쓰지 말라고하는 메소드인데요. 그 이유가 무엇일까요?
`System.out.println()` 의 구현
```java
public void println(){
  newLine();
}
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
