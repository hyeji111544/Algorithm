##   <a href="https://www.acmicpc.net/problem/25325">📖 백준 25325 (학생 인기도 측정) 📖</a>



### 접근법

```
인기도가 높은 학생부터 낮은 학생순으로 학생 이름과 해당 학생을 좋아하는 학생 수를 출력한다.
```
key 와 value 로 `학생`, `인기도 숫자` 를 저장한다.<br>
 <br>
이때 이름은 사전순, 인기도는 내림차순으로 정렬해야 하기 때문에 `EntrySet()`을 사용하여 `Map` 을 `List` 로 변환시켜준다. <br>
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
public class Main {
	public static void main(String[] args) {
			try {
			BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
			BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(System.out));
			int N = Integer.parseInt(reader.readLine());
			String[] names = reader.readLine().split(" ");
			
			HashMap<String, Integer> nameList = new HashMap<String, Integer>();
			
			 for (String name : names) {
	                nameList.put(name, 0);
	         }
			
			for(int k = 0; k<N ; k++) {
				String[] counts = reader.readLine().split(" ");
	
				for(String key : counts) {
					nameList.put(key, nameList.getOrDefault(key, 0)+1);
				}
			}
			
			 List<Entry<String, Integer>> list = new ArrayList<>(nameList.entrySet());
	            
	            Collections.sort(list, new Comparator<Entry<String, Integer>>() {
	                @Override
	                public int compare(Entry<String, Integer> o1, Entry<String, Integer> o2) { 
	                    if(o1.getValue().equals(o2.getValue())) {
	                    	return o1.getKey().compareTo(o2.getKey());
	                    }
	                    return o2.getValue().compareTo(o1.getValue());
	                }
	            });
			
	            for (Entry<String, Integer> entry : list) {
	            	writer.write(entry.getKey() + " " + entry.getValue() + "\n");
	            }
	            writer.flush();
		}catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```
