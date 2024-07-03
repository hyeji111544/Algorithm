##   <a href="https://www.acmicpc.net/problem/2751">📖 백준 2751 (수 정렬하기2) 📖</a>



### 접근법

```
N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.
시간제한 2초
```

1. 각 값을 list 에 저장한다. ()
2. list 의 값을 내림차순 정렬한다.
3. 정렬된 값을 출력한다. (for문 안에서 배열 순회하며 출력하면 시간초과)
4. 따라서 `StringBuilder`를 사용하여 배열안의 수를 문자열로 저장한 뒤 출력.

### 풀이

```
public class Main {
    public static void main(String[] args) {
        try {
            BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
            
            int N = Integer.parseInt(reader.readLine());
            List<Integer> list = new ArrayList<>();
            
            for(int i = 0; i < N; i++) {
                list.add(Integer.parseInt(reader.readLine()));
            }
            
            Collections.sort(list);
        
            StringBuilder sb = new StringBuilder();
            
            for(int k : list) {
               sb.append(k).append('\n');
            }
            
            System.out.println(sb.toString());
            
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
