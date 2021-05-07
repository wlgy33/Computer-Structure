# 03 Stack

## 스택 (Stack)
- 선형 자료구조이며, 접시를 쌓은듯한 순서를 가지는 자료구조이다.

### 스택의 특징
- 데이터에 제한적으로 접근이 가능하다.
- FILO(First In Last Out) 구조를 가진다.
- 단순한 구조 덕분에 데이터의 저장/읽기 속도가 빠르다.
- 데이터 최대 개수를 미리 설정해야 하며 저장 공간의 낭비가 발생할 수 있다.

### 구현
```java
class Stack {
    static final int MAX = 100;
    int size;
    int[] values;

    public Stack() {
        size = 0;
        values = new int[MAX];
    }

    // 가장 위에 값 삽입
	public void push(int data) {
		values[size++] = data;
	}

	// 가장 위에 있는 값 추출
	public int pop() {
		int rData = values[size];
		values[size--] = 0;

		return rData;
	}

	// 가장 위에 있는 값 조회
	public int peek() {
		if (size > 0) {
			return values[size - 1];
		} else {
			return -1;
		}
	}

	// 초기화 : 모든 값 삭제
	public void clear() {
		for (int i = 0; i < size; i++) {
			pop();
		}
		size = 0;
	}
}
```
