##   <a href="https://www.acmicpc.net/problem/31562">📖 백준 31562 (전주 듣고 노래 맞히기) 📖</a>



### 접근법

```
4 4
11 TwinkleStar C C G G A A G
8 Marigold E D E F E E D
23 DoYouWannaBuildASnowMan C C C G C E D
12 Cprogramming C C C C C C C
E D E
C G G
C C C
C C G
```
입력을 위와 같이 받았을 때 `C C G` 등 으로 시작하는 노래의 제목을 찾아야 한다. <br>
`Map` 을 사용해서 저장할 때 `key` 는 검색항목인 노래가 되고, 제목이 `value` 가 된다.
<br><br>
입력 값은 key 의 첫 3개가 같은 것을 찾는 것이기 때문에 Map 의 함수인 `String` 클래스의 `startWith` 메서드를 사용하여 `result` 에 저장하고<br>
`count` 를 이용해 출력 조건을 충족 시킨다. <br>
`출력 조건: 첫 세 음이 동일한 노래가 하나만 있다면 해당 노래의 제목을, 두 개 이상이면 ?을, 없다면 !을 한 줄에 하나씩 출력`

### 풀이

```
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		String input = sc.nextLine();
		String[] containers = input.split(" ");
		
		int N = Integer.parseInt(containers[0]);
		int M = Integer.parseInt(containers[1]);
		
		Map<String, String> map = new HashMap<>();
		for(int i=0; i<N; i++) {
			String music = sc.nextLine();
			String[] c = music.split(" ");
			String title = c[1];
			String code = c[2]+c[3]+c[4]+c[5]+c[6]+c[7];
			map.put(code, title);
		}
		
		for(int t=0; t<M; t++) {
			String q = sc.nextLine();
			String[] qq = q.split(" ");
			String splitedQ = qq[0]+qq[1]+qq[2];
			int count = 0;
			String result = null;
			
			for(String key : map.keySet()) {
				if(key.startsWith(splitedQ)) {
					count++;
					result = map.get(key);
				}
			}
			
			if(count ==1) {
				System.out.println(result);
			}else if(count > 1) {
				System.out.println("?");
			}else {
				System.out.println("!");
			}
		}
		sc.close();
	}
}
```
