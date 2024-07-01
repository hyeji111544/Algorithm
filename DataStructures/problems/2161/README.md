##   <a href="https://www.acmicpc.net/problem/2161">📖 백준 2161 (카드 1) 📖</a>



### 접근법

```
N 장의 카드가 있다. 1번 카드가 제일 위에 N 번 카드는 제일 아래이다.
제일 위의 카드를 버리고, 그 다음 제일 위에 있는 카드를 제일 아래로 옮긴다.
```
큐를 사용하여 풀이가 가능하다. <br>
제일 먼저 입력된 수 를 지우고, 그 다음 수를 지운 뒤 마지막 index 에 저장한다.<br>

입력된 N 개 만큼 for 문 안에서 `offer` 로 저장을 하여 1부터 시작되는 리스트를 만든다. <br>
그 후 `StringBuilder` 에 첫번째 값을 저장하고 새롭게 가장 앞쪽에 오게된 원소를 뒤로 보낸다. <br>

### 풀이

```
public class Main {
	public static void main(String[] args) {
		
		try {
			BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
			int N = Integer.parseInt(reader.readLine());
			
			Queue<Integer> queue = new LinkedList<>();
			
			// 입력받은 N 개 만큼의 카드를 queue 에 저장
			for(int m =1; m<=N ; m++) {
				queue.offer(m);
			}
			
			StringBuilder sb = new StringBuilder();
			
			while(!queue.isEmpty()) {
			
			    // 첫번째 데이터를 저장 이때 poll 은 값을 반환한 뒤 제거한다.
				sb.append(queue.poll()).append(" ");
				
				if(!queue.isEmpty()) {
				    // 새롭게 첫번째 오게된 값을 queue 리스트에 저장
					queue.offer(queue.poll());
				}
			}
			
			System.out.println(sb.toString().trim());
			
		}catch (Exception e) {
			// TODO: handle exception
		}
		
		
	}
}
```
