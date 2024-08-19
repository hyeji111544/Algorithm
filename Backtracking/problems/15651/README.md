##   <a href="https://www.acmicpc.net/problem/15651">📖 백준 15651 (N과 M (3)) 📖</a>



### 문제

![img.png](img.png)


### 접근법
1. 자연수 N과 M 의 정의를 위해 split 으로 분리하여 전역변수로 지정함.
2. 중복을 허용하기 때문에 `boolean` 타입 리스트는 사용하지 않음.
3. `depth`를 통해 최대 깊이에 도달할 때 까지 +1 하여 재귀 호출 한다.
4. M 과 같아지면 호출을 끝내고 `StringBuilder`에 담았던 문자열을 출력한다.
   

### 풀이

```java
import java.io.*;

public class Main {

    public static int N;
    public static int M;
    public static int depth;
    public static int [] arr;
    public static StringBuilder sb = new StringBuilder();
    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        String input = br.readLine();
        N = Integer.parseInt(input.split(" ")[0]);
        M = Integer.parseInt(input.split(" ")[1]);

        arr = new int[M];
        solve(0);
        bw.write(sb.toString());
        bw.flush();
    }

    public static void solve(int depth) {
        if (depth == M) {
            for(int i = 0; i < arr.length; i++) {
                sb.append(arr[i]).append(" ");
            }
            sb.append("\n");
            return;
        }
        for(int i = 1; i <= N; i++) {
            arr[depth] = i;
            solve(depth+1);
        }
    }
}
```
