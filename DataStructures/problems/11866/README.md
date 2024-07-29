##   <a href="https://www.acmicpc.net/problem/11866">📖 백준 11866 (요세푸스 문제 0) 📖</a>

![image](https://github.com/user-attachments/assets/d4fc98bb-1372-49c4-8f8e-df479bf80fe9)

### 접근법

```
큐를 사용하여 1부터 N 까지 나열된 수에서 K 번째 수 마다 차례로 뽑아낸 수열을 출력하는 것.

k번째 수가 되기 직전까지 맨 앞의 원소를 k-1 번 꺼내고 (poll) 꺼내온 원소들을 맨 뒤로 넣는다.(offer)
그리고 k 번째로 뽑힌(poll)원소는 출력한다.
{1,2,3,4,5,6,7} -> {2,3,4,5,6,7,1}
{2,3,4,5,6,7,1} -> {3,4,5,6,7,1,2}
{3,4,5,6,7,1,2} -> 3 출력
```
이때 신경쓸 것은 출력 형태. <br>
StringBuilder 에 `<` 를 추가하고 `poll`과 `,` 을 추가한 뒤 <br>
마지막에 추가된 `,` 제거를 위해 delete 를 한다.

### 풀이

```java
public class Main_11866 {
    public static void main(String[] args)throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] input = br.readLine().split(" ");
        int n = Integer.parseInt(input[0]);
        int k = Integer.parseInt(input[1]);

        Queue<Integer> queue = new LinkedList<>();

        for(int m =1; m<=n ; m++) {
            queue.offer(m);
        }

        StringBuilder sb = new StringBuilder();
        sb.append("<");
        while(!queue.isEmpty()) {
            for (int i = 0; i < k - 1; i++) {
                queue.offer(queue.poll());
            }
            sb.append(queue.poll()).append(", ");

        }

        sb.delete(sb.length() - 2, sb.length());
        sb.append(">");

        bw.write(sb.toString());
        bw.flush();
        bw.close();
        br.close();

    }
}
```
