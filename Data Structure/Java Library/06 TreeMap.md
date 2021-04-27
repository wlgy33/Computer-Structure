# 06 TreeMap

## TreeMap
TreeMap은 이진트리를 기반으로 한 Map 컬렉션이다. 객체를 저장하면 자동 **정렬**된다. 정렬 순서는 기본적으로 부모 key 값과 비교해 key 값이 낮은 것은 왼쪽 자식 노드, key 값이 높은 것은 오른쪽 자식 노드에 Map.Entry 객체를 저장한다. 데이터를 저장하는 즉시 정렬하기 때문에 추가/삭제에 시간이 걸린다. 정렬된 상태로 Map을 유지해야 하거나 정렬된 데이터를 조회해야 하는 범위 검색이 필요한 경우에 효율성이 좋다.

### TreeMap 사용법
Java Library에서 제공하는 TreeMap은 TreeSet이 그냥 값만 저장한다면 TreeMap은 Map 컬렉션이기 때문에 key와 value 형태의 **Map.Entry**를 저장한다. 기본적으로 메소드 사용법이 HashMap과 동일하다. 

### TreeMap 선언
```java
TreeMap<Integer, String> treeMap1 = new TreeMap<Integer, String>(); // int타입의 key와 String 타입의 value를 가진다.
TreeMap<Integer, String> treeMap2 = new TreeMap<>(); // 타입 파라미터의 생략이 가능하다
TreeMap<Integer, String> treeMap3 = new TreeMap<>(treeMap1); // 다른 TreeMap을 복사해서 선언할 수 있다
```
key로 저장할 객체타입과 value로 저장할 객체 타입을 타입 파라미터로 주고 기본 생성자를 호출한다. TreeMap 또한 선언 시 크기를 지정할 수 없다.

### 추가
```java
TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
treeMap.put(1, "사과");
treeMap.put(2, "복숭아");
treeMap.put(3, "수박");
```
TreeMap에 값을 추가하려면 put(key, value) 메소드를 사용한다. TreeMap의 타입 파라미터와 같은 타입의 key와 value 값을 넣어야 정상적으로 값이 input되며 만약 입력되는 key 값이 TreeMap 내부에 존재한다면 기존의 값은 새로 입력되는 값으로 대치된다.

### 삭제
```java
TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
treeMap.put(1, "사과");
treeMap.put(2, "복숭아");
treeMap.put(3, "수박");

treeMap.remove(1);
treeMap.clear();
```
TreeMap에 값을 삭제하려면 remove(key) 메소드를 사용한다. **오직 key 값으로만 TreeMap의 요소를 삭제할 수 있다.** 초기화하려면 clear() 메소드를 사용하면 된다.

### 크기 구하기
```java
TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
treeMap.put(1, "사과");
treeMap.put(2, "복숭아");
treeMap.put(3, "수박");

System.out.println(treeMap.size());
```
TreeMap의 크기는 size() 메소드를 사용해 알 수 있다.

### TreeMap의 값을 출력하는 다양한 메소드
```java
TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
treeMap.put(1, "사과");
treeMap.put(2, "복숭아");
treeMap.put(3, "수박");

System.out.println(treeMap); // 전체 출력 {1=사과, 2=복숭아, 3=수박}
System.out.println(treeMap.get(1)); // key값 1의 value얻기 : 사과
System.out.println(treeMap.firstEntry()); // 최소 Entry 출력 : 1=사과
System.out.println(treeMap.firstKey()); // 최소 Key 출력 : 1
System.out.println(treeMap.lastEntry()); // 최대 Entry 출력: 3=수박
System.out.println(treeMap.lastKey()); // 최대 Key 출력 : 3
```

### TreeMap 전체 출력
```java
TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
treeMap.put(1, "사과");
treeMap.put(2, "복숭아");
treeMap.put(3, "수박");

//entrySet() 활용
for (Entry<Integer, String> entry : treeMap.entrySet()) {
    System.out.println("[Key]:" + entry.getKey() + " [Value]:" + entry.getValue());
}
//[Key]:1 [Value]:사과
//[Key]:2 [Value]:복숭아
//[Key]:3 [Value]:수박

//KeySet() 활용
for(Integer i : treeMap.keySet()){ //저장된 key값 확인
    System.out.println("[Key]:" + i + " [Value]:" + treeMap.get(i));
}
//[Key]:1 [Value]:사과
//[Key]:2 [Value]:복숭아
//[Key]:3 [Value]:수박
```
TreeMap의 전체를 출력하려면 entrySet()이나 keySet() 메소드를 활용하여 Map의 객체를 반환받은 후 출력한다. **entrySet()은 key와 value 모두가 필요할 경우 사용**하며 **keySet()은 key 값만 필요할 경우 사용**한다.
key값만 받아서 get(key)를 활용하여 value도 출력할 수도 있다. 상대적으로 코드가 간단한 keySet을 사용하기도 하나 key값을 이용해서 value를 찾는 과정에서 시간이 많이 소모되므로 **많은 양의 데이터를 가져와야 한다면 entrySet()이 좋다**.

### Iterator 사용
```java
TreeMap<Integer, String> treeMap = new TreeMap<Integer, String>();
treeMap.put(1, "사과");
treeMap.put(2, "복숭아");
treeMap.put(3, "수박");

//entrySet().iterator()
Iterator<Entry<Integer, String>> entries = treeMap.entrySet().iterator();
while(entries.hasNext()){
    Map.Entry<Integer, String> entry = entries.next();
    System.out.println("[Key]:" + entry.getKey() + " [Value]:" +  entry.getValue());
}
//[Key]:1 [Value]:사과
//[Key]:2 [Value]:복숭아
//[Key]:3 [Value]:수박
		
//keySet().iterator()
Iterator<Integer> keys = treeMap.keySet().iterator();
while(keys.hasNext()){
    int key = keys.next();
    System.out.println("[Key]:" + key + " [Value]:" +  treeMap.get(key));
}
//[Key]:1 [Value]:사과
//[Key]:2 [Value]:복숭아
//[Key]:3 [Value]:수박
```
TreeMap도 객체 전체를 대상으로 한 번씩 반복해서 가져오는 반복자(Iterator)를 제공한다. Map 컬렉션이기 때문에 entrySet() 메소드나 keySet() 메소드를 활용해 iterator() 사용이 가능하다.
