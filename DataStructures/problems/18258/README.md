##   <a href="https://www.acmicpc.net/problem/18258">📖 백준 18258 (큐 2) 📖</a>

![image](https://github.com/user-attachments/assets/5444098e-3324-452d-a3dd-990e0db4ac70)

### 접근법

큐를 사용하여 입력문에 적절한 수행하는 프로그램을 만든다.<br>
`push` 는 `offer` <br>
`pop` 은 `poll` (값을 리턴하고 삭제한다) <br>
`front` 는 `peek`(값만 리턴함) <br>
`back` 을 위해  저장을 할 때 `last` 에 마지막에 입력된 수를 저장함. <br>

### 풀이

```java
public class Main_18258  {
	public static void main(String[] args) throws IOException{

		 BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	     BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
	        
	     int n = Integer.parseInt(br.readLine());
	     
	     Queue<Integer> queue = new LinkedList<>();
	     int last = -1;
	     
	     for(int i = 0 ; i<n ; i++) {
	    	 String k = br.readLine();
	    	 String[] list = k.split(" ");
	    	 String name = list[0];
	    	 
	    	 switch (name) {
				case "push": {
					int value = Integer.parseInt(list[1]);
					queue.offer(value);
					last = value;
					break;
				}
				case "pop": {
					if(queue.isEmpty()) {
						bw.write("-1\n");
					}else {
						bw.write(queue.poll()+"\n");
					}
					break;
							}
				case "size": {
					bw.write(queue.size()+"\n");
					break;
				}
				case "empty": {
					bw.write(queue.isEmpty() ? "1\n" : "0\n");
					break;
				}
				case "front": {
					if(queue.isEmpty()) {
						bw.write("-1\n");
					}else {
						bw.write(queue.peek()+"\n");
					}
					break;
				}
				case "back": {
					 if (queue.isEmpty()) {
	                        bw.write("-1\n");
	                    } else {
	                        bw.write(last + "\n");
	                    }
					break;
				}
				
			}
	     }
			bw.flush();
			bw.close();
			br.close();
    }
	
}
```
