##   <a href="https://www.acmicpc.net/problem/7785">📖 백준 7785 (회사에 있는 사람) 📖</a>



### 접근법

```
출입카드 시스템 로그에는 어떤 사람이 회사에 들어왔는지, 나갔는지가 기록되어 있다.
현재 회사에 있는 사람의 이름을 사전 순의 역순으로 한 줄에 한명씩 출력한다.
```
key 와 value 로 `사람`, `회사에 있는 여부` 를 저장한다.<br>
 <br>
이때 이름을 사전 순의 역순으로 출력해야 하기 때문에 `EntrySet()`을 사용하여 `Map` 을 `List` 로 변환시켜준다. <br>
(Java 에서 `Collections.sort()`를 사용하여 정렬을 하려면 일반적으로 List 형태로 정렬할 데이터를 가지고 있어야 하기 때문) <br>

`Collections.sort()` 는`List`혹은 배열 등의 자료구조를 정렬할 때 사용하는데, 이 때 정렬 기준을 제공하기 위해 인터페이스를 구현한 객체를 인자로 전달할 수 있다.

코드의 `compare`메서드는 두 개의 객체를 비교하여 정렬하는 클래스.
[자세히](https://velog.io/@hyejihi/Map-%EA%B3%BCHashMap-EntrySet-%EB%A9%94%EC%86%8C%EB%93%9C)

### 정리
1. `Map` 은 정렬을 위한 `Comparator` 직접적으로 사용이 불가능 하다.
2. `EntrySet`을 `List` 로 변환한다. 
3. `Collections.sort()` 메서드의 `Comparator` 인터페이스를 구현하여 오름, 내림차순으로 정렬 할 수 있다.

### 풀이

```
public class Main_7785 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		sc.nextLine();
		
		Map<String, String> stfMap = new HashMap<>();
		
		for(int i=0; i<N; i++) {
			String stfs = sc.nextLine();
			String[] stf = stfs.split(" ");
			String name = stf[0];
			String record= stf[1];
			
			stfMap.put(name, record);
		}
		
		List<Map.Entry<String, String>> entryList = new ArrayList<>(stfMap.entrySet());
		
		Collections.sort(entryList, new Comparator<Map.Entry<String, String>>() {

			@Override
			public int compare(Entry<String, String> o1, Entry<String, String> o2) {
				
				return o2.getKey().compareTo(o1.getKey());
			}
			
		});
		
		for(Map.Entry<String, String> entry : entryList) {
			if(entry.getValue().equals("enter")) {
				System.out.println(entry.getKey());
			}
		}
			
		sc.close();
	}
}
```
