# 05 Tree

## 트리 (Tree)
- 비선형 자료구조이며, 계층적 자료구조이다.

### 트리의 특징
- 노드(Node)와 간선(Edge, Branch)로 구성되어 있다.
- 최상위 노드를 루트 노드(Root Node)라 부른다.
- 노드와 노드는 간선으로 연결되어 있다.
- 노드 간에 부모, 형제, 자식의 관계를 가지기 때문에 계층 즉, 레벨이 존재한다.
- 이진트리 : 데이터를 검색하거나 자료를 정렬하는 알고리즘에서 사용된다.

### 이진 트리의 성질
- n개의 노드를 가진 이진트리는 n-1개의 간선을 가진다.
- 부모와 자식 사이에는 하나의 간선만이 존재한다.
- 높이가 h인 이진트리의 경우, 최소 h개의 노드를 가지고 2^h-1개의 노드를 가진다.
- n개의 노드를 가지는 이진트리의 높이는 최대 n이거나 최소 log(n+1)이다.

### 구현
```java
class Tree {
    int count;

    public Tree() {
        count = 0;
    }

    // 노드 클래스
    public class Node {
		Object data;
		Node left;
		Node right;
	
		// 생성 시 매개변수를 받아 초기화하는 방법으로만 선언 가능
		public Node(Object data) {
			this.data = data;
			left = null;
			right = null;
		}

		public void addLeft(Node node) {
			left = node;
			count++;
		}

		public void addRight(Node node) {
			right = node;
			count++;
		}

		public void deleteLeft() {
			left = null;
			count--;
		}

		public void deleteRight() {
			right = null;
			count--;
		}
	}
	
    // 노드 추가
	public Node addNode(Object data) {
		Node n = new Node(data);
		return n;
	}
	
    // 전위
	public void preOrder(Node node) {
		if(node == null) {
			return;
		}
		
		System.out.print(node.data + " ");
		preOrder(node.left);
		preOrder(node.right);
	}

    // 중위
	public void inOrder(Node node) {
		if(node == null) {
			return;
		}
		
		inOrder(node.left);
		System.out.print(node.data + " ");
		inOrder(node.right);
	}

    // 후위
	public void postOrder(Node node) {
		if(node == null) {
			return;
		}
		
		postOrder(node.left);
		postOrder(node.right);
		System.out.print(node.data + " ");
	}
}
```
