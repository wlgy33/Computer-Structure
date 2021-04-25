# 04 Queue

## Queue
영화관 매표소에 줄을 서서 기다리는 것처럼 순서대로 처리되는 자료구조이다. Queue는 데이터를 일시적으로 쌓아두기 위한 자료구조로 Stack과는 다르게 **FIFO**(First In First Out)의 형태를 가진다. Queue의 한 쪽 끝은 **front**로 정하여 **삭제** 연산만 수행한다. 다른 끝 쪽은 **rear**로 정해 **삽입** 연산만 수행한다. 그래프의 **넓이 우선 탐색**(BFS)에서 사용된다. **Buffer**에서 주로 사용되는데, 입력된 데이터가 많아 처리를 하지 못할 때, **Buffer**(Queue)를 만들어 대기시킨다.

## Queue 사용법
Java에서 Queue는 LinkedList를 사용해 생성해야 한다. 그렇기 때문에 Queue, LinkedList 둘 다 **import**해야한다.
```java
Queue<Element> queue = new LinkedList<Element>()
```

![Queue](https://user-images.githubusercontent.com/52726195/115990135-b0b62200-a5fc-11eb-8133-47a4c8da31ca.jpg)

### 추가
```java
Queue<Integer> queue = new LinkedList<Integer>(); 
queue.add(1);
queue.add(2);
queue.offer(3);
```
Queue에 값을 추가할 때 add(value) 또는 offer(value) 메소드를 사용한다. add(value) 메소드의 경우 삽입에 성공하면 true를 반환하고, Queue에 여유 공간이 없어 삽입에 실패하면 **IllegalStateException**을 발생시킨다.

![Queue Enqueue](https://user-images.githubusercontent.com/52726195/115990169-d3e0d180-a5fc-11eb-80e2-b946ce820bec.jpg)

### 삭제
```java
Queue<Integer> queue = new LinkedList<Integer>();
queue.offer(1);
queue.offer(1);
queue.offer(1);
queue.poll();    // queue의 첫 번째 값을 반환하고 제거, 비어있다면 null 반환
queue.remove();  // queue의 첫 번째 값 제거
queue.clear();   // queue의 전체 값 제거 (초기화)
```
Queue에 값을 삭제할 때 poll()이나 remove() 메소드를 사용한다. poll() 메소드는 첫 번째 값을 반환 후 제거하고, Queue가 비어있으면 null을 반환한다. remove() 메소드는 가장 앞에 있는 원소의 값이 제거된다. Queue를 초기화하려면 clear() 메소드를 사용하면 된다.

![Queue Dequeue](https://user-images.githubusercontent.com/52726195/115990190-e6f3a180-a5fc-11eb-815d-9511e64da6ce.jpg)

### peek
```java
Queue<Integer> queue = new LinkedList<>();
queue.offer(1);
queue.offer(2);
queue.offer(3);
System.out.println(queue.peek());   // queue의 첫번째 값 참조
```
Queue의 맨 앞에 위치한 값을 반환할 때 peek() 메소드를 사용한다.
