# 04 Queue

## 큐 (Queue)
- 선형 자료구조이며, 줄을 서서 기다리는 형태의 순서를 가지는 자료구조이다.

### 큐의 특징
- FIFO(First In First Out) 구조를 가진다.
- 큐의 한 쪽끝인 Front는 삭제연산만 수행한다.
- 큐의 한 쪽끝인 Rear는 삽입연산만 수행한다.
- 그래프의 넓이 우선 탐색(BFS)에서 사용된다.

### 구현
```java
class Queue {
    static final int MAX = 100;
    int front;
    int rear;
    int[] queue;

    public Queue() {
        front = 0
        rear = 0
        queue = new int[MAX];
    }

    // 맨 뒤에 새로운 값 삽입
    public enqueue(int value) {
        if (isFull()) System.out.println("Queue is Full");
        else queue[rear++] = value;
    }

    // 가장 앞에 있는 값 추출
    public dequeue() {
        if (isEmpty()) System.out.println("Queue is Empty");
        else return queue[front++];
    }

    // 가장 위에 있는 값 조회
    public peek() {
        if (isEmpty()) System.out.println("Queue is Empty");
        else return queue[front];
    }

    // 큐가 비어 있는지 확인
    public boolean isEmpty() {
        if (front == rear) return true;
        else return false;
    }

    // 큐가 가득 차 있는지 확인
    public boolean isFull() {
        if (rear == MAX-1) return true;
        else return false;
    }
}
```
