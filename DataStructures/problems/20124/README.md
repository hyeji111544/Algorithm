##   <a href="https://www.acmicpc.net/problem/20124">📖 백준 20124 (모르고리즘 회장님 추천 받습니다 ) 📖</a>



### 접근법

```
대회를 치른 사람 중에서 점수가 가장 높은 사람을 차기 회장으로 지목한다.
만약 가장 높은 사람이 2명 이상 있는 경우, 이름이 사전 순으로 가장 앞선 사람이 된다. 
```
key 와 value 로 `이름`, `점수` 를 저장한다.<br>
 <br>
이때 이름을 사전 순으로 출력해야 하기 때문에 `EntrySet()`을 사용하여 `Map` 을 `List` 로 변환시켜준다. <br>
(Java 에서 `Collections.sort()`를 사용하여 정렬을 하려면 일반적으로 List 형태로 정렬할 데이터를 가지고 있어야 하기 때문) <br>

`Collections.sort()` 는`List`혹은 배열 등의 자료구조를 정렬할 때 사용하는데, 이 때 정렬 기준을 제공하기 위해 인터페이스를 구현한 객체를 인자로 전달할 수 있다.

코드의 `compare`메서드는 두 개의 객체를 비교하여 정렬하는 클래스.
[자세히](https://velog.io/@hyejihi/Map-%EA%B3%BCHashMap-EntrySet-%EB%A9%94%EC%86%8C%EB%93%9C)

이름을 사전순으로 정렬한 뒤 `String name` `int score`를 선언한 뒤 먼저 저장된 사람보다 점수가 높은 경우
score 와 name 을 저장시킨 뒤 저장된 name 을 출력한다.

### 정리
1. `Map` 은 정렬을 위한 `Comparator` 직접적으로 사용이 불가능 하다.
2. `EntrySet`을 `List` 로 변환한다. 
3. `Collections.sort()` 메서드의 `Comparator` 인터페이스를 구현하여 오름, 내림차순으로 정렬 할 수 있다.

### 풀이

```

public class Main_20124 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		sc.nextLine();
		
		HashMap<String, Integer> stfMap = new HashMap<>();
		
		for(int i=0; i<N; i++) {
			String stfs = sc.nextLine();
			String[] stf = stfs.split(" ");
			String name = stf[0];
			Integer record= Integer.parseInt(stf[1]);
			
			stfMap.put(name, record);
		}
		
		List<Map.Entry<String, Integer>> entryList = new ArrayList<>(stfMap.entrySet());
		
		Collections.sort(entryList, new Comparator<Map.Entry<String, Integer>>() {

			@Override
			public int compare(Entry<String, Integer> o1, Entry<String, Integer> o2) {
				
				return o1.getKey().compareTo(o2.getKey());
			}
			
		});
		
		String nameKey = null;
		int score = 0;
		
		for(Map.Entry<String, Integer> entry : entryList) {
			
		
			if(score <entry.getValue()) {
				nameKey = entry.getKey();
				score = entry.getValue();		
			}
				
		}
		System.out.println(nameKey);
		
		sc.close();
	}
}

```
