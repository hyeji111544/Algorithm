##   <a href="https://www.acmicpc.net/problem/1417">📖 백준 1417 (국회의원 선거) 📖</a>



### 접근법

```
국회의원 후보는 N 명, 다솜이는 기호 1번이며 다솜이가 당선되기 위해 
매수해야 하는 사람의 최솟값 출력하기

입력 : 첫째 줄에 후보의 수 N이 주어진다. 
둘째 줄부터 차례대로 기호 1번을 찍으려고 하는 사람의 수, 
기호 2번을 찍으려고 하는 수, 이렇게 총 N개의 줄에 걸쳐 입력이 들어온다. 
N은 50보다 작거나 같은 자연수이고, 득표수는 100보다 작거나 같은 자연수이다.

출력 : 첫째 줄에 다솜이가 매수해야 하는 사람의 최솟값을 출력한다.
  
```
우선순위 큐를 사용하여 내부 요소를 자동 정렬 시킨다.(내림차순으로)<br>
따라서 제일 앞에 있는 요소는 큐 내부에서 가장 높은 수가 됨.

`while` 안에서 다솜의 득표수가 가장 클때까지 진행<br>
`if` 가 없었을 때 후보 1명이 처리가 안되어 런타임 에러 발생. <br>
후보가 1명일 경우 위해서 if 문 추가함.

### 풀이

```
public class Main_1417 {
	public static void main(String[] args) throws IOException {
		//국회의원 선거
		
		 BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	     BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
	     
	     //사람 수
	     int N = Integer.parseInt(br.readLine());
	     
	     int dasom = Integer.parseInt(br.readLine());
	     
	     PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
	     
	     for(int i = 0; i< N-1; i++) {
	    	 pq.add(Integer.parseInt(br.readLine()));
	     }
	     int count = 0;
	     
	     if (N == 1) {
	            bw.write(String.valueOf(count));
	            bw.flush();
	            bw.close();
	            return;
	     }
	     
	     while(dasom<=pq.peek()) {
	    	 int top = pq.poll();
	    	 pq.add(top - 1);
	         count++;
	         dasom++;
	     }
	     
	     bw.write(String.valueOf(count));
	     bw.flush();
	     bw.close();
	     
	}
}
```
