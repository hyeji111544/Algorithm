##   <a href="https://www.acmicpc.net/problem/28279">📖 백준 28279 (덱 2) 📖</a>

### 문제

![image](https://github.com/user-attachments/assets/e9ec1d03-a8c0-4895-b10e-51a543fae34b)

### 접근법

자바 `Deque(덱/데크)` 구조를 확인 하여 인터페이스 메소드를 활용하면 된다.<br>
1. 입력 받은 숫자에 맞게 출력시켜주면 된다.
2. 모든 명령을 입력받고 명령의 결과를 한 줄에 하나 씩 입력하기 위해 StringBuilder를 사용해준다.
    (systemout 사용 시 시간초과 발생함)

### 풀이

```java
public class Main_28279 {
	public static void main(String[] args) throws IOException{
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		StringBuilder sb = new StringBuilder();
		int n = Integer.parseInt(br.readLine());
		
		Deque<Integer> deq = new ArrayDeque<>();
		for(int i=0; i<n; i++) {
			String k = br.readLine();
			String[] list = k.split(" ");
			String command = list[0];
		
			switch(command) {
				case "1" : {
					deq.addFirst(Integer.parseInt(list[1]));
					break;
				}
				case "2" : {
					deq.add(Integer.parseInt(list[1]));
					break;
				}
				case "3" : {
					if(deq.isEmpty()) {
						sb.append("-1\n");
					}else {
						sb.append(deq.removeFirst()).append("\n");
					}
					break;
				}
				
				case "4" : {
					if(deq.isEmpty()) {
						sb.append("-1\n");
					}else {
						sb.append(deq.removeLast()).append("\n");
					}
					break;
				}
				case "5" : {
					sb.append(deq.size()).append("\n");
					break;
				}
				case "6" : {
					if(deq.isEmpty()) {
						sb.append("1\n");
					}else {
						sb.append("0\n");
					}
					break;
				}
				case "7" : {
					if(deq.isEmpty()) {
						sb.append("-1\n");
					}else {
						sb.append(deq.getFirst()).append("\n");
					}
					break;
				}
				
				case "8" : {
					if(deq.isEmpty()) {
						sb.append("-1\n");
					}else {
						sb.append(deq.getLast()).append("\n");
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
