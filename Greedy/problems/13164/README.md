##   <a href="https://www.acmicpc.net/problem/13164">📖 백준 13164 (행복 유치원) 📖</a>

### 문제
![image](https://github.com/user-attachments/assets/dce50c9e-c7c5-45b0-b6a1-196d3601eac2)

### 접근법
키 순으로 원생들이 주어지며 인접한 원생들의 키 차이를 구한다. <br>
이때 조에 누가 들어있는지는 중요하지 않음. <br>

예제는 다음과 같다.
```
5 3
1 3 5 6 10
```
3개의 그룹을 만들기 위해서는 가장 작은 차이를 가진 그룹을 `2번`만 합치면 3개의 그룹이 된다. <br>
`M-1 번 만큼  조를 만듬` <br>

인접한 원생의 키 차이는 다음과 같다.
```angular2html
1, 3 -> 2
3, 5 -> 2
5, 6 -> 1
6, 10 -> 4
```
정렬하면 1, 2, 2, 4 가 된다.(코드상에선 역정렬 하였다.)

1. `cost` 에 `list[k+1]-list[k]` 를 저장한다. (원생의 키 차이)
2. 저장된 cost 를 역정렬 한다.
3. `M-1` 만큼 조를 만들기 때문에 `cost` 를 계산하는 for 문은 `M-1` 번 부터 시작한다. 


### 풀이

```java
public class Main_13164 {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

    String[] input = br.readLine().split(" ");
    int N = Integer.parseInt(input[0]);
    int M = Integer.parseInt(input[1]);

    int[] list = new int[N];

    String[] inputList = br.readLine().split(" ");
    for(int i=0 ; i<N; i++) {
      list[i] = Integer.parseInt(inputList[i]);
    }

    List<Integer> cost = new ArrayList<>();
    for(int k=0; k<N-1; k++) {
      cost.add(list[k+1]-list[k]);
    }
    Collections.sort(cost, Collections.reverseOrder());

    int sum =0;
    for(int i = M-1; i<cost.size(); i++) {
      sum += cost.get(i);
    }
    bw.write(String.valueOf(sum));

    bw.flush();
    bw.close();
    br.close();

  }
}
```
