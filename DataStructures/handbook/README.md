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

### You can add a header

You can add text within a collapsed section. 

You can add an image or a code block, too.

```ruby
   puts "Hello World"
```

</details>

<details>

<summary>3. 스택(Stack) </summary>

### You can add a header

You can add text within a collapsed section. 

You can add an image or a code block, too.

```ruby
   puts "Hello World"
```

</details>

<details>

<summary>4. 큐(Queue) </summary>

### You can add a header

You can add text within a collapsed section. 

You can add an image or a code block, too.

```ruby
   puts "Hello World"
```

</details>
