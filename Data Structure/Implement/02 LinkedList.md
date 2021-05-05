# 02 LinkedList

## 연결 리스트 (LinkedList)
- 리스트는 선형 자료구조이며, 순서를 가진 데이터들의 모임이다.

### 연결 리스트의 특징
- 정해진 크기의 공간 없이, 필요할 때마다 데이터를 추가하고 삭제 가능한 자료구조이다.
- 배열과 달리 크기가 무한하다.
- 연결을 위한 메모리도 필요하기 때문에 효율이 낮은 단점이 있다.
- 접근 속도가 느리며, 중간 데이터 삭제시 앞 뒤 데이터의 연결을 재구성해야 하는 작업이 필요하다.

### LinkedList로 구현
```java
class LinkedList {
    // Node에 대한 정의
    private class Node {
        Node prev;  // 이전 노드의 정보
        int data;   // 현재 노드에 들어있는 값
        Node next;  // 다음 노드의 정보

        Node() { }

        Node(int data) {
            this.data = data;
        }
    }

    private Node head;  // 가장 앞 노드의 정보
    private Node tall;  // 가장 뒤 노드의 정보
    private Node cur;   // 현재 가리키고 있는 노드의 정보
    private int size;   // 현재 리스트의 크기

    // 본격적 노드 생성자
    public LinkedList() {
        head = new Node();
        tall = new Node();
        cur = new Node();

        size = 0;
    }

    // 삽입 연산
    public void add(int data) {
        // 처음 데이터 추가하는 경우
        if (size == 0) {
            Node newNode = new Node(data);

            head.next = newNode;
            newNode.prev = head;
            newNode.next = tail;
			tail.prev = newNode;

			size++;
		} else {
			Node newNode = new Node(data);

			cur = head.next;
			while (cur.next != tail) {
				cur = cur.next;
			}

			cur.next = newNode;
			newNode.prev = cur;

			newNode.next = tail;
			tail.prev = newNode;

			size++;
        }
    }

    public void add(int data, int index) {
        // 전체 크기보다 큰 곳에 데이터를 삽입하려는 경우
		if(index > size) {
			System.out.println("Please try again");
			return;
		}
		
		// 첫 데이터 추가인 경우와 아닌 경우 구분
		if (size == 0) {
			Node newNode = new Node(data);

			head.next = newNode;
			newNode.prev = head;

			newNode.next = tail;
			tail.prev = newNode;

			size++;
		} else {
			Node newNode = new Node(data);

			// 마지막 노드로 이동
			cur = head.next;
			for(int i = 0; i < index; i++) {
				cur = cur.next;
			}

			cur.next = newNode;
			newNode.prev = cur;

			newNode.next = tail;
			tail.prev = newNode;

			size++;
		}
    }

    public int remove(int index) {
		Node rNode;
		
		// 데이터 초과일 경우
		if(index > size) {
			System.out.println("Please try again");
			return -1;
		}
		
		// 인덱스 값 찾아가기
		cur = head.next;
		for(int i = 0; i < index; i++) {
			cur = cur.next;
		}
		rNode = cur;
		 
		// 이전 노드와 이후 노드 포인터 변경
		cur.prev.next = cur.next;
		cur.next.prev = cur.prev;
		size--;
		
		return rNode.data;
	}

	public int size() {
		return size;
	}

	public int indexOf(int data) {
		int count = 0;
		boolean bFind = false;
		
		cur = head.next;
		while(cur.next != tail) {
			if(cur.data == data) {
				bFind = true;
				break;
			}
			cur = cur.next;
			count++;
		}
		
		if(bFind) {
			return count;
		}else {
			return -1;
		}
	}
}
```
