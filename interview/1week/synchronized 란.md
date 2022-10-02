`synchronized 란 `
lock을 사용해 동기화시키는 method

`동기화(Synchronizaion)`
동기화는 특정 객체를 동시에 접근하여 변경하기를 막는 기법입니다.

`synchronized method`

- 인스턴스 단위로 lock이 걸린다.
- 메서드가 시작될 때부터 종료될 때까지 동기화가 발생한다.
- 동일 인스턴스내에서 synchronized키워드가 적용된 곳에서는 lock을 공유한다. 

```java
  A a = new A();
  Thread thread1 = new Thread( () -> {
    a.run(name:"thread1");
  });
  Thread thread2 = new Thread( () -> {
    a.run(name:"thread2");
  });
  thread1.start();
  thread2.start();
```
```java
  public synchronized void run(String name){
    System.out.println(name + " lock");
    try{
      Thread.sleep(millis:1000);
    } catch (InterruptedException e) {
      e.printStackTrace();
    }
    System.out.println(name + " unlock");
  }
```
```java
thread1 lock
thread1 unlock
thread2 lock
thread2 unlock
```

`synchronized block`

- 인스턴스 단위로 lock이 걸린다.
- block내부에서 동기화가 발생한다.
- lock 객체를 지정하여 특정 대상에만 lock을 걸 수 있다.
- lock을 객체로 설정하면 해당 인스턴스만 lock이 걸리고 .class형식으로 설정하면 클래스 단위로 lock을 건다.


```java
  A a1 = new A();
  A a2 = new A();
  Thread thread1 = new Thread( () -> {
    a.run(name:"thread1");
  });
  Thread thread2 = new Thread( () -> {
    a.run(name:"thread2");
  });
  thread1.start();
  thread2.start();
```
```java
  public synchronized void run(String name){
    System.out.println(name + " lock");
    try{
      Thread.sleep(millis:1000);
    } catch (InterruptedException e) {
      e.printStackTrace();
    }
    System.out.println(name + " unlock");
  }
```
```java
thread1 lock
thread2 lock
thread1 unlock
thread2 unlock
```

`static synchronized method`

- 클래스 단위로 lock이 걸린다.
- 메서드가 시작될 때부터 종료될 때까지 동기화가 발생한다.
- static synchronized와 synchronized가 혼용되어있을 때 각자의 lock으로 관리된다.

```java
  A a1 = new A();
  A a2 = new A();
  Thread thread1 = new Thread( () -> {
    a.run(name:"thread1");
  });
  Thread thread2 = new Thread( () -> {
    a.run(name:"thread2");
  });
  thread1.start();
  thread2.start();
```
```java
  public static synchronized void run(String name){
    System.out.println(name + " lock");
    try{
      Thread.sleep(millis:1000);
    } catch (InterruptedException e) {
      e.printStackTrace();
    }
    System.out.println(name + " unlock");
  }
```
```java
thread1 lock
thread1 unlock
thread2 lock
thread2 unlock
```

`static synchronized block`

- 클래스 단위로 lock이 걸린다.
- block내부에서 동기화가 발생한다.
- lock객체를 지정하여 특정 대상에만 lock을 걸 수 있다.
- lock을 객체로 설정하면 해당 인스턴스만 lock이 걸리고 .class형식으로 설정하면 클래스 단위로 lock을 건다.

```java
  A a1 = new A();
  A a2 = new A();
  Thread thread1 = new Thread( () -> {
    a.run(name:"thread1");
  });
  Thread thread2 = new Thread( () -> {
    a.run(name:"thread2");
  });
  thread1.start();
  thread2.start();
```
```java
  public static void run(String name){
    synchronized (A.class){
     System.out.println(name + " lock");
     try{
       Thread.sleep(millis:1000);
     } catch (InterruptedException e) {
       e.printStackTrace();
     }
     System.out.println(name + " unlock");
   }
  }
```
```java
thread1 lock
thread1 unlock
thread2 lock
thread2 unlock
```

`synchronized는 thread별 동기화 순서를 보장안한다`
