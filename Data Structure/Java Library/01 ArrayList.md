# 01 ArrayList

## ArrayList
**배열(Array)**는 크기가 고정되어 있지만 **ArrayList**는 **크기가 동적**인 배열이다. Java 라이브러리에서 제공하는 ArrayList 클래스로 구현된 Array는 데이터를 추가하는 데로 크기가 늘어난다. ArrayList의 검색 시간은 **O(1)**이다. 처음 설정한 ArrayList의 저장용량(Capacity)를 넘어서면 크기를 늘린다.

## ArrayList 사용법
java.util.ArrayList에 포함되어 있기 때문에 **import** 해야한다.

### ArrayList 선언
```java
ArrayList arrayList = new ArrayList(); // 타입 미설정 Object로 선언된다
ArrayList<Integer> intArray = new ArrayList<Integer>(); // int타입만 저장할 수 있다
ArrayList<Integer> capacity = new ArrayList<Integer>(10); // 크기가 10인 int타입 ArrayList
ArrayList<Double> doubleArray = new ArrayList<Double>(Arrays.asList(1.1, 2.2, 3.3)); // double타입의 ArrayList 생성과 동시에 값 지정
```
ArrayList 선언 시 ArrayList list = new ArrayList()로 선언 후 내부에 임의의 값을 넣고 사용할 수 있지만 값을 추출하기 위해 캐스팅(Casting) 연산이 필요하고 잘못된 타입으로 캐스팅할 시 에러가 발생할 여지가 있다. 따라서, 타입을 명시해주는 것이 권장된다. 타입으로 **제너릭(Generic)** 또한 가능하다.

### 추가
```java
// ArrayList 생성
ArrayList<Integer> numbers = new ArrayList<>();

// 추가
// ArrayList에 값 추가
numbers.add(10);
numbers.add(20);
numbers.add(30);
numbers.add(40);
```

```java
// 인덱스를 이용해 값 추가. 기존 위치에 있던 값들이 하나씩 밀려난다.
number.add(1, 50);
```

![추가](https://user-images.githubusercontent.com/52726195/115567389-2ddc5100-a2f6-11eb-87e0-55d54975a457.JPG)

### 삭제
index로 접근해 해당 값을 삭제한다
```java
numbers.remove(2);
```
![삭제](https://user-images.githubusercontent.com/52726195/115567448-3c2a6d00-a2f6-11eb-9838-29f36d29c76f.JPG)

### 값 가져오기
index로 접근해 해당 값을 가져온다
```java
numbers.get(2);
```
![가져오기](https://user-images.githubusercontent.com/52726195/115567492-48aec580-a2f6-11eb-98ca-5bbc57341a7a.JPG)
