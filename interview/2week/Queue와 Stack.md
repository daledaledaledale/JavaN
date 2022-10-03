`Queue`

- 줄을 지어 순서대로 처리되는 것이 큐라는 자료구조입니다.
- 큐는 데이터를 일시적으로 쌓아두기 위한 자료구조로 스택과는 다르게 FIFO(First In First Out)의 형태를 가집니다.
- FIFO 형태는 뜻 그대로 먼저 들어온 데이터가 가장 먼저 나가는 구조를 말합니다.
> Enqueue : 큐 맨 뒤에 데이터 추가
> Dequeue : 큐 맨 앞쪽의 데이터 삭제

Queue의 특징
1. 먼저 들어간 자료가 먼저 나오는 구조 FIFO(First In First Out) 구조
2. 큐는 한 쪽 끝은 프런트(front)로 정하여 삭제 연산만 수행함
3. 다른 한 쪽 끝은 리어(rear)로 정하여 삽입 연산만 수행함
4. 그래프의 넓이 우선 탐색(BFS)에서 사용
5. 컴퓨터 버퍼에서 주로 사용, 마구 입력이 되었으나 처리를 하지 못할 때, 버퍼(큐)를 만들어 대기 시킴

`Queue 선언`

```java
import java.util.LinkedList;
import java.util.Queue;
Queue<Integer> queue = new LinkedList<>();
Queue<String> queue = new LinkedList<>();
```

- 자바에서 큐는 LinkedList를 활용하여 생성해야 합니다. 
- 그렇기에 Queue와 LinkedList가 다 import되어 있어야 사용이 가능합니다. 
- Queue<Element> queue = new LinkedList<>()와 같이 선언해주면 됩니다.

`Queue 값 추가`

```java
Queue<Integer> stack = new LinkedList<>();
queue.add(1);
queue.add(2);
queue.offer(3);
```

- 자바에서 queue에 값을 추가하고 싶다면 add(value) 또는 offer(value)라는 메서드를 활용하면 됩니다. 
- add(value) 메소드의 경우 만약 삽입에 성공하면 true를 반환하고, 큐에 여유 공간이 없어 삽입에 실패하면 IllegalStateException을 발생시킵니다. 
- queue에 값을 계속해서 추가해나간다면 아래 그림과 같은 형태로 데이터가 쌓이게 됩니다.

`Queue 값 삭제`

```java
Queue<Integer> queue = new LinkedList<>();
queue.offer(1); // queue에 값 1 추가
queue.offer(2); // queue에 값 2 추가
queue.peek(); // queue의 첫번째 값 참조
queue.poll(); // queue에 첫번째 값을 반환하고 제거 비어있다면 null
queue.remove(); // queue에 첫번째 값 제거
queue.clear(); // queue 초기화
```

`Stack`

- 상자에 물건을 쌓아 올리듯이 데이터를 쌓는 자료 구조라고 할 수 있습니다.
- Stack의 가장 큰 특징은 나중에 들어간 것이 먼저 나오는 (Last In First Out)의 형태를 띈다는 것입니다.
- 이 방식을 가진 자료구조인 Stack을 활용하여 다양한 문제를 해결할 수 있습니다. 
- 자바에서 Stack은 java.util.Stack을 import하면 바로 사용할 수 있습니다.

`Stack의 특징`

1. 먼저 들어간 자료가 나중에 나옴 LIFO(Last In First Out) 구조
2. 시스템 해킹에서 버퍼오버플로우 취약점을 이용한 공격을 할 때 스택 메모리의 영역에서 함 
3. 인터럽트처리, 수식의 계산, 서브루틴의 복귀 번지 저장 등에 쓰임
4. 그래프의 깊이 우선 탐색(DFS)에서 사용
5. 재귀적(Recursion) 함수를 호출 할 때 사용

`Stack 선언`

```java
import java.util.Stack;
Stack<Integer> stack = new Stack<>();
Stack<String> stack = new Stack<>();
```

`Stack 값 추가,삭제`

```java
Stack<Integer> stack = new Stack<>();
stack.push(1);     // stack에 값 1 추가
stack.push(2);     // stack에 값 2 추가
stack.peek();     // stack의 가장 상단의 값 출력
stack.pop();       // stack에 값 제거
stack.clear();     // stack의 전체 값 제거 (초기화)
stack.size();      // stack의 크기 출력 : 2
stack.empty();     // stack이 비어있는제 check (비어있다면 true)
stack.contains(1)  // stack에 1이 있는지 check (있다면 true)
```
  

