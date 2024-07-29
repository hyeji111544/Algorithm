##   <a href="https://www.acmicpc.net/problem/2164">📖 백준 2164 (카드 2) 📖</a>

![image](https://github.com/user-attachments/assets/0be3628f-8732-4fbd-9362-e1db069a8ac9)

### 접근법

```
1. 제일 위에 있는 카드를 버린다.
2. 다음 카드는 제일 아래의 카드 밑으로 옮긴다.  
```
`queue` 에 처음 입력받은 숫자 만큼 큐에 입력한다.

`while` 문에서 배열이 비었는지 확인하고 k 에 배열의 첫 숫자를 저장한다.
그 다음 배열이 비어있는지 확인하고 비어있지 않으면 그 다음 배열의 수를 `queue` 에 새로 넣는다.

마지막에 저장된 k 를 출력시키면 된다.

### 풀이

```
public class Main_2164  {
	public static void main(String[] args) throws IOException{
		 BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	    
	     int n = Integer.parseInt(br.readLine());
	     
	     Queue<Integer> queue = new LinkedList<>();
	     
	     for(int i = 1 ; i<=n ; i++) {
	    	 queue.offer(i);
	     }
	     
	     int k = 0;
	     
	     while (!queue.isEmpty()) {
			k = queue.poll();
			if(!queue.isEmpty()) {
				queue.offer(queue.poll());
			}
		}
	     System.out.println(k);
    }
}
```
