# 02 LinkedList

## LinkedList
연결 리스트(LinkedList)는 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식의 자료구조이다. 데이터를 담고 있는 노드들이 연결되어 있고, 노드의 포인터가 이전 노드와 다음 노드와의 연결을 담당한다. 노드는 LinkedList에 객체를 추가/삭제하면 앞 뒤 링크만 변경되고 나머지 링크는 변경되지 않는다. 중간에 데이터를 추가/삭제하더라도 전체의 index가 한 칸씩 뒤로 밀리거나 당겨지는 일이 없기에 ArrayList에 비해 데이터의 추가/삭제가 용이하다. 단, index가 없기에 특정 요소에 접근하기 위해 **순차탐색**이 필요해 **탐색 속도가 떨어진다**는 단점이 있다. 따라서, **탐색 또는 정렬을 자주 하는 경우 배열을 사용하고 데이터의 추가/삭제가 많은 경우 연결 리스트를 사용하는 것이 좋다.**

![LinkedList 구조](https://user-images.githubusercontent.com/52726195/115723395-e66bc880-a3ba-11eb-89f4-e571128b57de.jpg)

ArrayList는 내부 배열에 객체를 저장해서 index로 관리하지만 LinkedList는 위와 같이 인접 참조를 링크해서 체인처럼 관리한다.

## LinkedList 사용법
java.util.LinkedList에 포함되어 있기 때문에 **import** 해야한다.

### LinkedList 선언
```java
LinkedList list = new LinkedList(); // 타입 미설정 Object로 선언된다
LinkedList<Integer> num = new LinkedList<Integer>(); // 타입설정 int타입만 저장할 수 있다
LinkedList<Integer> list2 = new LinkedList<Integer>(Arrays.asList(1,2)); // int타입의 LinkedList 생성과 동시에 값 지정
```
LinkedList는 ArrayList와 달리 초기의 크기를 미리 설정할 수 없다. LinkedList선언 시 LinkedList list = new LinkedList()로 선언하고 내부에 임의의 값을 넣어 사용할 수도 있지만 이렇게 사용할 경우 내부의 값을 사용할 때 캐스팅(Casting)을 해야 하고 잘못된 타입으로 캐스팅을 한 경우에는 에러가 발생할 여지가 있다. 따라서, 타입을 명시해주는 것이 권장된다. 타입으로 **제너릭(Generic)** 또한 가능하다.

### 추가
```java
LinkedList<Integer> list = new LinkedList<Integer>();
list.addFirst(1); // 가장 앞에 데이터 추가
list.addLast(2); // 가장 뒤에 데이터 추가
list.add(3); // 데이터 추가
list.add(1, 10); // index 1뒤에 데이터 10 추가
```
만약 클래스를 타입으로 한다면
```java
LinkedList<Student> list = new LinkedList<Student>();
Student student = new Student(name,age);
members.add(student);
members.add(new Member("홍길동",15));
```
LinkedList에 값을 추가할 때 add(index, value) 메소드를 사용한다. index를 생략하면 가장 마지막에 데이터가 추가된다. addFirst(value)함수를 사용하게 되면 가장 앞에 있는 Header의 값이 변경되고 addLast(value) 메소드를 사용하면 LinkedList 맨 뒤에 데이터가 추가된다.

![LinkedList 추가](https://user-images.githubusercontent.com/52726195/115724859-4747d080-a3bc-11eb-95f2-8ffceca94e65.jpg)

LinkedList의 값이 추가되는 방식은 위와 같다. 먼저 인자로 받은 값을 가지고 Node를 생성하여 생성한 노드는 이전 노드는 추가되는 노드를 가리키게 하고 추가되는 노드는 그다음 노드를 가리키도록 지정한다.

### 삭제
```java
LinkedList<Integer> list = new LinkedList<Integer>(Arrays.asList(1,2,3,4,5));
list.removeFirst(); // 가장 앞의 데이터 제거
list.removeLast(); // 가장 뒤의 데이터 제거
list.remove(); // 생략시 0번째 index제거
list.remove(1); // index 1 제거
list.clear(); // 모든 값 제거
```
removeFirst() 메소드를 사용하면 가장 첫 데이터가 removeLast()를 사용하면 가장 뒤에 있는 데이터가 삭제된다. remove(index, value)를 사용하여 특정 index의 값을 제거할 수 있다. 값을 전부 제거하려면 clear()메소드를 사용하면 된다.

![LinkedList 삭제](https://user-images.githubusercontent.com/52726195/115725133-8b3ad580-a3bc-11eb-8601-63d04318cc9a.jpg)

LinkedList의 값이 제거되는 방식은 위와 같다. 삭제 대상 노드의 이전의 노드가 삭제 대상 노드의 다음의 노드를 가리키게 하고 해당 노드는 삭제 된다.


