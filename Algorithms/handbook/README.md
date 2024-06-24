# 자료구조 내용 정리

## 자료구조란?
 - 데이터를 효율적으로 저장하고 관리하는 방법이나 형식을 말한다.

<details>

<summary>1. 리스트(List) </summary>

### 리스트의 특징

- 순서가 있고 중복을 허용한다.
- 인덱스로 관리하기 때문에 인덱스로 접근 가능하다.
- 크기가 가변하다.

### List 인터페이스 메서드
| 메서드 | 사용 |
|--------|----------|
|add(int index, Object element) | 주어진 인덱스에 객체를 추가한다. |
|addAll(int index, Collection c)| 주어진 인덱스에 컬렉션을 추가한다. `boolean` 타입을 리턴 |
|set(int index, Object element)|주어진 인덱스에 객체를 저장. `Object` 타입을 리턴|
|indexOf(Object o) / lastIndex(Object o)| 순방향 / 역방향으로 탐색하여 주어진 객체의 위치를 반환한다.  `int` 타입 리턴 |
|listIterator() / listIterator(int index)| List의 객체를 탐색할 수 있는 `ListIterator` 반환 / 주어진 index부터 탐색할 수 있는 `ListIterator` 타입 리턴 |
|subList(int fromIndex, int toIndex)|fromIndex부터 toIndex까지의 객체를 반환한다. List 타입을 리턴한다.|
|remove(int index)|주어진 인덱스에 저장된 객체를 삭제 후, 삭제된 객체를 반환 `Object` 타입 리턴|
|remove (Object o) | 주어진 객체를 삭제한다. `boolean` 타입을 리턴 |
|sort(Comparator c)|주어진 비교자(comparator)로 List를 정렬한다.|


### ArrayList
`ArrayList`는 배열 기반의 리스트로, 인덱스로 접근할 때 빠르지만 중간에 요소를 추가하거나 삭제할 때는 느릴 수 있습니다.

#### ArrayList 특징
- 동적 배열로 크기가 자동으로 조정된다.
- 인덱스를 통해 빠르게 접근할 수 있다.
- 요소 추가 및 삭제가 느릴 수 있다.
  
### 예시
```java
   import java.util.ArrayList;
   import java.util.List;
   
   public class Main {
		public static void main(String args){
			List<String> list = new ArrayList<>();
			
			list.add("a")
			list.add("b")
			list.add("c")

			for(String aToc : list){
				System.out.print(aToc)  // 출력 abc
			}
	
			List<String> list = Arrays.asList(new String[]{"a","b","c"});
			
			for(String aToc : list){
				System.out.println(aToc) // 출력 abc
			}
		}
	}
```

### LinkedList
`LinkedList` 는 노드 기반의 리스트로, 요소를 추가하거나 삭제할 때 빠르지만 인덱스로 접근할 때는 느릴 수 있다.

### 특징
- 이중 연결 리스트로 구현된다.
- 요소 추가 및 삭제가 빠르다.
- 인덱스를 통해 접근할 때 느릴 수 있다.

```java
import java.util.LinkedList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> linkedList = new LinkedList<>();
        
        linkedList.add("x");
        linkedList.add("y");
        linkedList.add("z");
        
        for (String element : linkedList) {
            System.out.print(element);  // 출력 xyz
        }

        linkedList.add(1, "w");
        System.out.println(linkedList);  // 출력 [x, w, y, z]

        linkedList.remove("y");
        System.out.println(linkedList);  // 출력 [x, w, z]
    }
}

```

</details>


<details>

<summary>2. 맵(Map) </summary>

## 2. 맵(Map)

- (key-value)방식으로 key-value를 하나의 쌍으로 저장하는 방식 사용
- key는 value를 찾기위해 사용, 이것이 맵의 가장 큰 특징으로 Key의 중복을 허용X, Value 중복O

### Map 인터페이스 메서드

| 메서드 | 사용 |
| --- | --- |
| put(Object a, Object b) | Key = a, Value = b로 저장 |
| get(Object o) | Key 값이 o인 Value를 반환한다. Object타입 리턴 |
| containsKey(Object o) | o라는 Key 값이 있는지 확인하여 값을 반환한다. boolean 타입 리턴 |
| remove(Object o) | Key값이 o인 객체를 삭제 후, 그 value값을 반환한다. Object 타입 리턴 |
| size() | Map의 갯수를 리턴한다. int 타입 리턴 |
| isEmpty() | 해당 맵이 비어있는지 확인 boolean 타입 리턴 |
| replace(Object k, Object v) | k라는 Key값에 해당하는 Value값을 v로 대체, 바뀌기 전 Value 값 리턴 |
| replace(Object key, Object oldValue, Object newValue) | key값에 대응하는 키의 값을 새로운 값으로 대체, boolean값 리턴으로 확인 |

### Map컬렉션 클래스에 속하는 클래스

### HashMap<K, V> 특징

- Map 컬렉션 중 가장 많이 사용
- Map의 가장 기본적인 형태
- 검색시 해시 알고리즘(hash algorithm)을 사용하여 검색속도가 매우 빠름

### treeMap<K, V> 특징

- key, value 값을 쌍으로하는 데이터를 이진 검색 트리(binary search tree) 형태로 저장
- 객체를 저장시 자동으로 오름차순으로 정렬 (문자일경우 유니코드로 정렬)
- 키 값이 낮은 것이 왼쪽 자식 노드에, 높은것은 오른쪽 자식 노드에 저장

### Map 예제
```java
public class Main {
    public static void main(String[] args) {
    
        // Map 생성 및 초기화
        Map<String, Integer> map = new HashMap<>();
        map.put("one", 1);
        map.put("two", 2);
        map.put("three", 3);

        // 첫 번째 replace 메서드 사용 예제
        Integer oldValue1 = map.replace("two", 22);
        System.out.println("Old value for key 'two': " + oldValue1); 
        /* 출력: Old value for key 'two': 2 */
        System.out.println("New value for key 'two': " + map.get("two"));
        /* 출력: New value for key 'two': 22 */

        // 키가 존재하지 않는 경우
        Integer oldValue2 = map.replace("four", 44);
        System.out.println("Old value for key 'four': " + oldValue2); 
        /* 출력: Old value for key 'four': null*/

        // 두 번째 replace 메서드 사용 예제
        boolean isReplaced1 = map.replace("three", 3, 33);
        System.out.println("Was the value for key 'three' replaced? " + isReplaced1);
        /* 출력: Was the value for key 'three' replaced? true */
        System.out.println("New value for key 'three': " + map.get("three"));
        /* 출력: New value for key 'three': 33 */

        // 값이 일치하지 않는 경우
        boolean isReplaced2 = map.replace("one", 10, 100);
        System.out.println("Was the value for key 'one' replaced? " + isReplaced2); 
        /* 출력: Was the value for key 'one' replaced? false */
        System.out.println("Value for key 'one': " + map.get("one")); 
        /* 출력: Value for key 'one': 1 */
    }
}
```

</details>


<details>

<summary>3. 집합(Set) </summary>

- Set은 리스트, 배열과 달리 순서를 저장하지 않고 값을 저장
- 리스트, 배열과 달리 중복된 값을 허용하지 않는다.
- FastLookup이 필요할때 주로 쓰인다(즉각적인 접근 시간을 제공)

### 장점

- 데이터의 고유성 보장(데이터 추가시 중복 항목은 제거, List를 Set으로 변환하고 다시 List로 변환하면 중복된 값을 제거하면서 요소의 순서 유지 가능)
- 수학적 집합연산 가능(합집합, 교집합)
- 효율적 데이터 테스트(존재여부 테스트에 매우 효율적)

### Set 인터페이스 메서드

| 메서드 | 사용 |
| --- | --- |
| boolean add(Object o) | 데이터 중복확인 후 요소 추가(중복되어 값이 안들어갔으면 false)후 bolean타입 리턴 |
| boolean remove(Object o) | 지정된 요소가 있는경우 Set에서 제거 후 true반환,  boolean타입 리턴 |
| boolean contains(Obnect o) | Set에 지정된 요소가 포함되어 있으면 true 반환, boolean 타입 |
| int size() | 집합의 요소 수 반환 int 타입 |
| Iterator<E> iterator() | Set의 요소 반복 반환, 특정 순서로 반환 되지 않음 |

```java
   public class Main {
    public static void main(String[] args) {
    
       // Set 생성 및 초기화
       Set<String> set = new HashSet();
        set.add("Apple");
        set.add("Banana");
        set.add("Orange");
        set.add("Apple"); // 중복된 요소 안들어감 return하면 flase
        
        // 해당 값 확인
        System.out.println("contains 'Banana': " + set.contains("Banana")); 
        /*출력: contains 'Banana' : true */
        
        // 해당 값 삭제
        set.remove("Ornage");
        
        // 크기(요소 수)출력
        System.out.println("number of elements: " + set.size()); 
        /*출력: number of elements: 2*/
        
        Iterator<String> iterator = set.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
         /*출력: 
         Apple
         Banana
         /
    }
}
```

### Set 컬렉션 클래스에 속하는 것
### HashSet 특징

- 가장 일반적으로 사용되는 Set 구현 형태
- 해시 테이블을 사용하여 요소의 빠른 접근, 삽입, 삭제를 제공
- 해싱을 사용하기 때문에 순서 유지X

### TreeSet 특징

- 정렬된 순서(오름차순)로 요소를 유지, 관리하는 Set 구현 형태
- 이진 검색 트리로 구현, null값을 허용하지 않는다.

### LinkedHashSet

- 해시 테이블 외에 이중으로 연결된 요소 목록을 관리하는 HashSet의 확장 형태
- null값을 허용 하지만 하나의 null 값만을 허용

</details>


<details>

<summary>4. 스택(Stack) </summary>

- 후입선출(LIFO) 구조로 먼저 들어온 데이터가 나중에 빠져나가는 구조
- 단방향 입출력구조로 데이터의 들어노는 방향과 나가는 방향이 같다
- 데이터를 하나씩만 넣고 뺄 수 있다.
- 깊이 우선 탐색(DFS)에 이용된다.

```java
   public class Main {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();

        // 스택에 요소 추가 (push)
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println("Stack after pushes: " + stack); 
        // 출력: Stack after pushes: [1, 2, 3]

        // 스택의 맨 위 요소 확인 (peek)
        int topElement = stack.peek();
        System.out.println("Top element: " + topElement);
        // 출력: Top element: 3

        // 스택에서 요소 제거 (pop)
        if(){
	        int removedElement = stack.pop();
	        System.out.println("Removed element: " + removedElement); 
	        // 출력: Removed element: 3
	        System.out.println("Stack after pop: " + stack); 
	        // 출력: Stack after pop: [1, 2]

        }
        
        
        // 스택이 비어 있는지 확인 (isEmpty)
        boolean isEmpty = stack.isEmpty();
        System.out.println("Is stack empty? " + isEmpty);
        // 출력: Is stack empty? false
    }
}

```

</details>

<details>

<summary>5. 큐(Queue) </summary>

- 선입선출(FIFO)의 성격을 지니는 자료구조(LinkedList도)
- 너비 우선탐색(BFS), 스레드풀(ExceutorService)에 사용

### Queue 인터페이스 메서드

| 메서드 | 사용 |
| --- | --- |
| boolean offer(E e) | 주어진 객체를 넣는다. bolean타입 리턴 |
| peek() | 큐의 객체 중 먼저 들어온 맨 앞 하나를 리턴 |
| poll() | 가장 먼저 들어온 맨 앞 객체 제거, 제거된 객체 턴 |
| int size() | 큐의 요소 수 반환 int 타입 |
| boolean isEmpty() | 큐의 요소가 비어있는지 확인 bolean타입 리턴 |


</details>
