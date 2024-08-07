##   <a href="https://www.acmicpc.net/problem/1427">📖 백준 1427 (소트인사이드) 📖</a>

### 문제

![image](https://github.com/user-attachments/assets/8c52b642-da71-4c50-ba37-73de3104452e)

### 접근법


### 풀이

```java
public class Main_1427 {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		String input = br.readLine();
		List<Character> charList = new ArrayList<>();
        for (char c : input.toCharArray()) {
            charList.add(c);
        }
        
		Collections.sort(charList, Collections.reverseOrder());
		        
		StringBuilder sb = new StringBuilder();
		for (char c : charList) {
		    sb.append(c);
		}
		
		System.out.println(sb.toString());
		
		br.close();
	}
}

```
