# 05 Tree

## Tree
Tree는 **노드(Node)**와 **간선(Edge)**를 이용하여 비선형구조를 가지는 자료구조이다. 단 하나의 **Root Node**를  가지며, Root Node는 0개 이상의 자식 노드를 가진다. 자식 노드들 또한 0개 이상의 자식 노드를 가지며 뻗어나간다. 부모 노드와 자식노드의 관계를 가지기 때문에 다른 자료구조와는 다른 **계층적 자료구조**이다. 또한, Tree에서 파생되는 여러 종류의 Tree들이 존재한다. 노드가 n개인 Tree는 항상 n-1개의 간선(edge)를 가진다. 흐름은 항상 **top-bottom**이나 **bottom-top**으로 이루어진다.

### Tree 용어
- **루트 노드(Root Node)** : 부모가 없는 노드, Tree는 하나의 루트 노드만을 가진다
- **단말 노드(Leaf Node)** : 자식이 없는 노드, 말단에 위치한다
- **내부 노드(Internal Node)** : 단말 노드가 아닌 노드
- **간선(Edge)** : 노드를 연결하는 선으로 **link** 또는 **branch**라고도 부른다
- **형제(Siblings)** : 같은 부모를 가지는 노드
- **노드의 크기(size)** : 자신을 포함한 모든 자식 노드의 개수
- **노드의 깊이(depth)** : 루트 노드에서 어떤 노드에 도달하기 위해 거쳐야 하는 간선의 수
- **노드의 레벨(level)** : Tree의 특정 깊이를 가지는 노드의 집합
- **노드의 차수(degree)** : 하위 트리 개수 / 간선의 수 = 각 노드가 지닌 가지의 수
- **트리의 높이(height)** : 루트 노드에서 가장 깊숙히 있는 노드의 깊이

**이진 탐색 트리(Binary Search Tree)** 구조로 이루어져 있다. 이진 탐색 트리는 추가와 삭제시간이 좀 걸리는 단점이 있지만 **정렬, 검색에 높은 성능**을 보인다. **부모노드보다 작은 값을 가지는 노드는 왼쪽으로, 큰 값을 가지는 노드는 오른쪽 자식 노드에 배치한다.**

### TreeSet 사용법
Java Library에서 제공하는 TreeSet은 객체를 중복해서 저장할 수 없고 저장 순서가 유지되지 않는다는 Set의 성질을 가지고 있다.

### TreeSet 선언
```java
TreeSet<Integer> set1 = new TreeSet<Integer>(); // int타입만 저장할 수 있다
TreeSet<Integer> set2 = new TreeSet<>(); // 타입 파라미터의 생략이 가능하다
TreeSet<Integer> set3 = new TreeSet<Integer>(set1); // 다른 Tree를 안에 넣어 선언할 수 있다
TreeSet<Integer> set4 = new TreeSet<Integer>(Arrays.asList(1,2,3)); // 초기값을 지정할 수 있다.
```
다른 자료구조의 선언과 마찬가지로 저장할 객체의 타입을 파라미터로 표기하고 기본 생성자를 호출하면 된다. 단, 선언 시 크기를 지정할 수 없다.

### 추가
```java
TreeSet<Integer> treeSet = new TreeSet<Integer>();
treeSet.add(4); 
treeSet.add(2);
treeSet.add(5);
treeSet.add(1);
treeSet.add(3);
```
TreeSet에 값을 추가할 때 add(value) 메소드를 사용한다. 입력되는 값이 TreeSet 내부에 존재하지 않는다면 그 값을 추가한 뒤 true를 반환하고 내부에 값이 존재한다면 false를 반환한다.

### 삭제
```java
TreeSet<Integer> treeSet = new TreeSet<Integer>();
treeSet.add(4); 
treeSet.add(2);
treeSet.add(5);
treeSet.add(1);
treeSet.add(3);

treeSet.remove(1);
treeSet.clear();
```
TreeSet에 값을 삭제할 때 remove(value) 메소드를 사용한다. 매개변수 value의 값이 존재한다면 그 값을 삭제한 뒤 true를 반환하고 없다면 false를 반환한다. 초기화하려면 clear() 메소드를 사용한다.

### 크기 구하기
```java
TreeSet<Integer> treeSet = new TreeSet<Integer>(Arrays.asList(1, 2, 3));
System.out.println(treeSet.size());
```
TreeSet의 크기는 size() 메소드를 사용해 알 수 있다.

### TreeSet의 값을 출력하는 다양한 메소드
```java
TreeSet<Integer> treeSet = new TreeSet<Integer>(Arrays.asList(5, 3, 1));
System.out.println(treeSet); // 전체 출력 [1, 3, 5]
System.out.println(treeSet.first()); // 최소값 출력
System.out.println(treeSet.last()); // 최대값 출력
System.out.println(treeSet.higher(3)); // 인자보다 큰 데이터 중 최소값 출력 없으면 null 반환
System.out.println(treeSet.lower(3)); // 인자보다 작은 데이터 중 최대값 출력 없으면 null 반환

// Iterator를 사용한 출력
Iterator iterator1 = treeSet.iterator();
while(iterator1.hasNext()) { // 값이 있다면 true 없으면 false
    System.out.println(iterator1.next());
}
```
TreeSet에는 객체 전체를 대상으로 한 번씩 반복해서 가져오는 반복자(Iterator)를 제공한다. iterator에서 하나의 객체를 가져올 때에는 next() 메서드를 사용한다. next() 메서드를 사용하기 전에 먼저 가져올 객체가 있는지 hasNext() 메서드를 활용하여 먼저 확인하는 것이 좋다. hasNext() 메서드는 가져올 객체가 있으면 true, 없으면 false를 반환한다.
