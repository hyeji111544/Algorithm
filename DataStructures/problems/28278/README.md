##   <a href="https://www.acmicpc.net/problem/28278">📖 백준 28278 (스택 2) 📖</a>



### 접근법

```
정수를 저장하는 스택을 구현한 다음, 입력으로 주어지는 명령을 처리하는 프로그램을 작성하시오.

명령은 총 다섯 가지이다.

1 X: 정수 X를 스택에 넣는다. (1 ≤ X ≤ 100,000)
2: 스택에 정수가 있다면 맨 위의 정수를 빼고 출력한다. 없다면 -1을 대신 출력한다.
3: 스택에 들어있는 정수의 개수를 출력한다.
4: 스택이 비어있으면 1, 아니면 0을 출력한다.
5: 스택에 정수가 있다면 맨 위의 정수를 출력한다. 없다면 -1을 대신 출력한다.

입력
첫째 줄에 명령의 수 N이 주어진다. (1 ≤ N ≤ 1,000,000)
둘째 줄부터 N개 줄에 명령이 하나씩 주어진다.
출력을 요구하는 명령은 하나 이상 주어진다.

출력
출력을 요구하는 명령이 주어질 때마다 명령의 결과를 한 줄에 하나씩 출력한다.

```
1. 입력 받은 숫자에 맞게 출력시켜주면 된다.
2. 모든 명령을 입력받고 명령의 결과를 한 줄에 하나 씩 입력하기 위해 StringBuilder를 사용해준다.
    (systemout 사용 시 시간초과 발생함)

### 풀이

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Stack;

public class Main_28278 {
	public static void main(String[] args) throws IOException{
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		StringBuilder sb = new StringBuilder();
		int n = Integer.parseInt(br.readLine());
		
		Stack<Integer> st = new Stack<>();
		for(int i=0; i<n; i++) {
			String k = br.readLine();
			String[] list = k.split(" ");
			String command = list[0];
		
			switch(command) {
				case "1" : {
					st.push(Integer.parseInt(list[1]));
					break;
				}
				case "2" : {
					if(st.isEmpty()) {
						sb.append("-1\n");
					}else {
						sb.append(st.pop()).append("\n");
					}
					break;
				}
				case "3" : {
					sb.append(st.size()).append("\n");
					break;
				}
				
				case "4" : {
					if(st.isEmpty()) {
						sb.append("1\n");
					}else {
						sb.append("0\n");
					}
					break;
				}
				case "5" : {
					if(st.isEmpty()) {
						sb.append("-1\n");
					}else {
						sb.append(st.peek()).append("\n");
					}
					break;
				}
			}
		}
		bw.write(sb.toString());
        bw.flush();
        bw.close();
        br.close();
	}

}
```
