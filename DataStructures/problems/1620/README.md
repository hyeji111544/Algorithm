##   <a href="https://www.acmicpc.net/problem/1620">📖 백준 1620 (나는야 포켓몬 마스터 이다솜) 📖</a>



### 접근법

```
26 5 첫번째 수는 도감에 등록된 포켓몬N, 두번째는 문제의 개수M 이다.
문제가 알파벳으로 들어오면 숫자를, 숫자가 들어오면 해당하는 포켓몬의 이름을 출력한다.
```
포켓몬의 이름과 번호를 저장해야 하기 때문에 `Map`을 사용했다.<br>
이때 문제가 알파벳으로 검색하거나 숫자로도 검색할 수 있어야 하는데, <br>
`Map` 은 value 의 값으로는 검색할 수 없다는 특성이 있음.  <br>
따라서 `key` 가 숫자인 map 과 이름인 map 두개를 선언하여 저장함.  <br>

### 풀이

```
public class Main_27160 {
	public static void main(String[] args) {
			
		try {
			BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
			BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(System.out));
			
			String[] input = reader.readLine().split(" ");
			
			int N = Integer.parseInt(input[0]);
			int M = Integer.parseInt(input[1]);
			
			HashMap<String, Integer> nameList = new HashMap<String, Integer>();
			HashMap<Integer, String> keyList = new HashMap<Integer, String>();
			
			 for (int i =0; i<N; i++) {
				 String name = reader.readLine();
	                nameList.put(name, i+1);
	                keyList.put(i+1, name);
	         }

			for(int k = 0; k<M ; k++) {
				String q = reader.readLine();
				if(nameList.containsKey(q)) {
				    // 입력받은 q 가 nameList 의 key 인 경우
					writer.write(String.valueOf(nameList.get(q))+"\n");
				}else {
				    // 입력받은 q 가 숫자인 경우 String 으로 받았기 때문에 타입변환 시킴.
					writer.write(String.valueOf(keyList.get(Integer.parseInt(q))+"\n"));
				}
			}
			
			
	        writer.flush();
	        writer.close();
	        reader.close();
		}catch (Exception e) {
			e.printStackTrace();
		}
		
		
	}
}
```
