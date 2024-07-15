##   <a href="https://www.acmicpc.net/problem/1052">📖 백준 1052 (행렬) 📖</a>



### 접근법

```
학교에서 그래픽스 수업을 들은 동준이는 수업시간에 들은 내용을 바탕으로 스마트폰 게임을 만들었다. 
게임에는 총 N개의 레벨이 있고, 각 레벨을 클리어할 때 마다 점수가 주어진다. 
플레이어의 점수는 레벨을 클리어하면서 얻은 점수의 합으로, 이 점수를 바탕으로 온라인 순위를 매긴다. 
동준이는 레벨을 난이도 순으로 배치했다. 하지만, 실수로 쉬운 레벨이 어려운 레벨보다 점수를 많이 받는 경우를 만들었다.

이 문제를 해결하기 위해 동준이는 특정 레벨의 점수를 감소시키려고 한다. 이렇게해서 각 레벨을 클리어할 때 주는 점수가 증가하게 만들려고 한다.

각 레벨을 클리어할 때 얻는 점수가 주어졌을 때, 몇 번 감소시키면 되는지 구하는 프로그램을 작성하시오. 
점수는 항상 양수이어야 하고, 1만큼 감소시키는 것이 1번이다. 항상 답이 존재하는 경우만 주어진다. 
정답이 여러 가지인 경우에는 점수를 내리는 것을 최소한으로 하는 방법을 찾아야 한다.
```
레벨의 수 : `4` , 점수 : `5 3 7 5` 입력을 받았을 때 <br>
가장 뒤의 점수가 제일 높고 순차적으로 작아져야 한다. <br>
따라서 for 문에서 배열의 뒤에서 부터 앞으로 탐색한다. <br>

- i = 2 일때 7, 5 를 비교하게 되고 필요한 차이는 `7 - 5 + 1 = 3` 이 됨.
  - scores[2] -= 3 을 하면 배열 상태는 `[5, 3, 4, 5]`
  - 3을 count 에 더한다.

- i = 1 일때 3, 4 는 옳기 때문에 변경할 필요 없음.
- i = 0 일때 5, 3 을 비교하여 필요한 차이를 구함 `5 - 3 + 1 = 3`
  - scores[0] -= 3 으라면 배열은 `[2, 3, 4, 5]` 가 됨
  - 필요한 차이인 3을 count 에 더한다.


### 풀이

```java
public class Main_2847 {
	public static void main(String[] args) throws IOException {
		//게임을 만든 동준이
		
		 BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	     BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
	     
	     int N = Integer.parseInt(br.readLine());
	     int[] scores = new int[N];
	     
	     for(int i = 0; i<N; i++) {
	    	 scores[i] = Integer.parseInt(br.readLine());
	     }
	     
	     int count = 0;
	     
	     for(int i = N-2 ; i>=0; i--) {
	    	 if(scores[i] >= scores[i+1]) {
	    		 int minus = scores[i] - scores[i+1] + 1;
	    		 scores[i] -= minus;
	    		 count += minus;
	    	 }	 
	     }
	     
	     bw.write(String.valueOf(count));
	     
	     bw.flush();
	     bw.close();
	     
	}
}
```
