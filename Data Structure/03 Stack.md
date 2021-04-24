# 03 Stack

## Stack
접시처럼 쌓아 올리듯 데이터를 쌓는 자료구조이다. 마지막에 들어간 것이 제일 먼저 나오는 **LIFO**(Last In First Out) 형태이다. 그래프의 **깊이 우선 탐색**(DFS)에서 사용되며 **재귀적 함수**를 호출할 때 사용한다.

## Stack 사용법
java.util.Stack에 포함되어 있기 때문에 **import**해야한다.

### Stack 선언
```java
import java.util.Stack; 
Stack<Integer> stack = new Stack<Integer>(); // int타입만 저장할 수 있다
Stack<String> stack = new Stack<String>(); // char타입만 저장할 수 있다
```

![Stack](https://user-images.githubusercontent.com/52726195/115961315-dc7bce00-a550-11eb-82f8-2947a35c0f6b.jpg)

### 추가
```java
Stack<Integer> stack = new Stack<Integer>();
stack.push(1);
stack.push(2);
stack.push(3);
```
Stack에 값을 추가할 때 push(value) 메소드를 사용한다. Stack에 값을 계속해서 추가해나간다면 아래 그림처럼 데이터가 쌓인다.

![Stack push](https://user-images.githubusercontent.com/52726195/115961333-eb628080-a550-11eb-9c53-875fba78d782.jpg)

### 삭제
```java
Stack<Integer> stack = new Stack<Integer>();
stack.push(1);
stack.push(2);
stack.push(3);
stack.pop();    // stack에 값 제거
stack.clear();  // stack의 전체 값 제거 (초기화)
```
Stack에서 값을 삭제할 때 pop() 메소드를 사용한다. pop을 하면 가장 위쪽에 있는 원소의 값이 아래 그림과 같이 제거된다. Stack의 값을 모두 제거하고싶다면 clear()라는 메서드를 사용한다.

![Stack pop](https://user-images.githubusercontent.com/52726195/115961338-f3babb80-a550-11eb-870e-7b5725363e05.jpg) 

### peek
```java
Stack<Integer> stack = new Stack<Integer>();
stack.push(1);
stack.push(2);
stack.push(3);
System.out.println(stack.peek());     // stack의 가장 상단의 값 출력
```
Stack의 최상단에 위치한 값을 반환할 때 peek() 메소드를 사용한다. 아래 그림과 같이 가장 마지막에 들어간 값이 반환된다.

### 크기 구하기
```java
Stack<Integer> stack = new Stack<Integer>();
stack.push(1);
stack.push(2);
System.out.println(stack.size());
```
Stack의 크기를 구하려면 size() 메소드를 사용한다. size() 메소드는 Stack의 크기를 반환한다.

### 비어 있는지 체크
```java
Stack<Integer> stack = new Stack<Integer>();
stack.push(1);
stack.push(2);
stack.empty();
```
Stack이 비어있는 지 확인한다. 비어 있다면 true를, 그렇지 않다면 false를 반환한다.

### contains
```java
Stack<Integer> stack = new Stack<Integer>();
stack.push(1);
stack.push(2);
stack.contains(1);
```
Stack에 해당 element가 있는지 확인한다. 있다면 true를, 그렇지 않다면 false를 반환한다.
