##   <a href="https://www.acmicpc.net/problem/1052">📖 백준 1052 (물병) 📖</a>



### 문제
![image](https://github.com/user-attachments/assets/b9345737-fc47-4bb4-8f7d-519cf5214218)


### 접근법
이 문제는 `비트마스킹` 문제로 이진수로 바꾸어 풀면 간단하다고 한다..!<br>
예제의 `3 1` 을 이진법으로 표현했을 때 `N=3` 은 `11(2)` 이다. 이때 1의 개수가 물병의 개수를 의미한다.<br>
한번에 들고갈 수 있는 물병의 수는 `K=1` 임으로 `N` 이 갖고있는 `1` 의 개수가 `K` 와 같거나 작아야 한다.<br>

`11(2)` 에 1을 더할 시 `100(2)` 가 되어 문제를 충족하게 된다. 

### 풀이
1. `while` 루프 안에서 필요한 물병 수를 계산한다.
2. `int count = Integer.bitCount(N);` 입력받은 N의 이진수에서 `1` 의 개수를 센다.
3. 1의 개수가 `K`와 같거나 작으면 루프 종료.
4. 아닐 시 N과 물병수를 증가시키고 1번으로 돌아감.

```java
public class Main_1052 {
  public static void main(String[] args) throws IOException{
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

    String[] input = br.readLine().split(" ");
    int N = Integer.parseInt(input[0]);
    int K = Integer.parseInt(input[1]);

    int bottles = 0;

    while (true) {
      int count = Integer.bitCount(N);
      if (count <= K) {
        break;
      }
      N++;
      bottles++;
    }

    bw.write(String.valueOf(bottles));
    bw.flush();
    bw.close();
    br.close();
  }
}
```
