##   <a href="https://www.acmicpc.net/problem/28417">📖 백준 28417 (스케이트보드) 📖</a>



### 접근법

```
두 차례의 런에서 받은 최고 점수와 다섯 차례의 트릭 연기를 통해 받은 점수 중 상위 2개의 점수, 
총 3개의 점수를 더한 값이 최종 점수가 된다.
출전한 선수들의 점수표가 주어졌을 때, 우승자의 최종 점수를 구해 보자.

2
1 2 4 2 3 1 1
5 5 5 5 5 5 5
```
입력을 위와 같이 받았을 때 `1 2`, `4 2 3 1 1` 으로 run 과 trick 으로 나누어 저장하여 run 의 상위 1개, trick 의 상위 2개의 값을 더한다.<br>
<br><br>
`Collections.sort(runList, Collections.reverseOrder());` 을 사용하여 저장된 값을 내림차순 정렬한 뒤<br>
runList, trickList 의 0, 0, 1번째 값을 모두 더하여 기존 값과 비교하여 저장한다.<br>

### 풀이

```
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		sc.nextLine();
		
		int maxScore = 0;
	
		for(int i=0; i<N; i++) {
			String input = sc.nextLine();
			String[] split = input.split(" ");
			
			List<Integer> runList = new ArrayList<>();
			List<Integer> trickList = new ArrayList<>();
			
			runList.add(Integer.parseInt(split[0]));
			runList.add(Integer.parseInt(split[1]));

		
			for (int j = 2; j < split.length && j <= 6; j++) {
				trickList.add(Integer.parseInt(split[j]));
			}
			
			Collections.sort(runList, Collections.reverseOrder());
			Collections.sort(trickList, Collections.reverseOrder());
			
			Integer score = runList.get(0)+trickList.get(0)+trickList.get(1);
			
			if(score > maxScore) {
				maxScore = score;
			}
		
		}
		System.out.println(maxScore);
		
		sc.close();
	}
}
```
