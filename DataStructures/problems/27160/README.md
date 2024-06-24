##   <a href="https://www.acmicpc.net/problem/27160">📖 백준 27160 (할리갈리) 📖</a>



### 접근법

```
할리갈리는 4종류의 과일이 최대 5개 까지 그려져 있다.
펼쳐진 카드 중 한 종류 이상의 과일이 정확히 5개가 있는 경우 종을 눌러야 하며
5개일때 YES, 아닐때 NO 를 출력한다. 
```
과일 이름과 갯수를 저장해야 하기 때문에 `Map`을 사용했다.<br>
String 타입의 key 와 Integer 타입의 value 로 저장한다.<br>
 <br>
이때 같은 key 인 경우 과일 갯수가 더해져야 하기 때문에 `getOrDefault()` 를 사용했다. <br>
(Map 에서 key 값으로 value 값을 취득하는 경우 `get()` 을 사용하는데 이때, 찾는 key 가 없거나 null 이면 null 을 리턴한다.) <br>
**getOrDefault** 는 null 대신 기본 값을 반환한다. <br>
`getOrDefault(Object key, V defaultValue)` 인 경우 찾는 key 의 값을 반환하거나, 아닐 때 `defaultValue` 를 리턴하도록 정해주는것. <br>
 <br>
`fruitCount.put(fruit, fruitCount.getOrDefault(fruit, 0)+count)` 풀이의 이 코드를 통해 카드의 과일 갯수를 더하여 문제를 해결했다.
 

### 풀이

```
public class Main_27160 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		//sc.nextLine();
		
		Map<String, Integer> fruitCount  = new HashMap<>();
	        
		for(int i=0; i<N; i++) {
			String cards= sc.nextLine();
			String[] card = cards.split(" ");
			String fruit = card[0];
			int count = Integer.parseInt(card[1]);
			
			fruitCount.put(fruit, fruitCount.getOrDefault(fruit, 0)+count);
			
		}
		
		boolean strawberry = fruitCount.getOrDefault("STRAWBERRY", 0) == 5;
		boolean banana = fruitCount.getOrDefault("BANANA", 0) == 5;
		boolean lime = fruitCount.getOrDefault("LIME", 0) == 5;
		boolean plum = fruitCount.getOrDefault("PLUM", 0) == 5;
		
		if(strawberry || banana || lime || plum) {
			System.out.println("YES");
		}else {
			System.out.println("NO");
		}
		
		
		sc.close();
	}
}
```
