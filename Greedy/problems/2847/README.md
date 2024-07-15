##   <a href="https://www.acmicpc.net/problem/2847">📖 백준 2847 (게임을 만든 동준이) 📖</a>


### 문제
```
0과 1로만 이루어진 행렬 A와 행렬 B가 있다. 이때, 행렬 A를 행렬 B로 바꾸는데 필요한 연산의 횟수의 최솟값을 구하는 프로그램을 작성하시오.
행렬을 변환하는 연산은 어떤 3×3크기의 부분 행렬에 있는 모든 원소를 뒤집는 것이다. (0 → 1, 1 → 0)
```
### 출력
```
첫째 줄에 문제의 정답을 출력한다. 만약 A를 B로 바꿀 수 없다면 -1을 출력한다.
```
### 접근법
1. 3*3 으로 탐색한다.
2. 부분 행렬에 있는 `모든` 원소를 뒤집는다. -> 모든 원소를 뒤집는 메서드`change` 
3. 변환이 끝난 A,B 두 행렬이 동일한지 확인하여 -1 또는 연산 횟수를 출력.

### 풀이

```java
public class Main_1052 {
  static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

  public static void main(String[] args) throws IOException{

    StringTokenizer token = new StringTokenizer(br.readLine());
    int N = Integer.parseInt(token.nextToken());
    int M = Integer.parseInt(token.nextToken());

    int[][] A = new int[N][M];
    int[][] B = new int[N][M];

    // A,B 행렬에 값 넣기
    procession(A, N, M);
    procession(B, N, M);

    int count = 0;

    // 접근법 1. 3*3 으로 탐색
    for(int i = 0; i<=N-3; i++) {
      for(int k=0; k<=M-3; k++) {
        if(A[i][k] != B[i][k]) {
            // 행렬의 원소가 같은지 확인 후 change 호출
          change(A, i, k);
          count++;
        }
      }
    }

    // 행렬 동일한지 확인
    for(int i = 0; i<N; i++) {
      for(int k =0; k<M; k++) {
        if(A[i][k] != B[i][k]) {
          System.out.println(-1+"\n");
          return;
        }
      }
    }
    System.out.println(count+"\n");
    br.close();
  }

  // 행렬에 값 넣기
  public static void procession(int[][] R, int N, int M) throws IOException {
    for(int i = 0; i<N; i++) {
      String[] tokens = br.readLine().split("");
      for(int k=0; k<M; k++) {
        R[i][k] = Integer.parseInt(tokens[k]);
      }
    }
  }
  // 접근법 2. 3*3 형식으로 행렬 뒤집기
  public static void change(int[][] A, int x, int y) {
    for(int i = x; i<x+3; i++) {
      for(int k=y; k<y+3; k++) {
        A[i][k] = 1- A[i][k];
      }
    }

  }
}
```
