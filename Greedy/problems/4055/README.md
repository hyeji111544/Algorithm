##   <a href="https://www.acmicpc.net/problem/4055">📖 백준 4055 (파티가 좋아 파티가 좋아) 📖</a>

### 문제
![image](https://github.com/user-attachments/assets/aca37e89-5bbc-4346-8158-2a3e1d8176fa)

## 접근법
파티를 최소 30분 참석하기 때문에 9:00 - 10:00에 파티가 2개 열려도 9:00 과 9:30분 둘 다 참석할 수 있다.<br>
파티 시간이 끝났다면 그 파티는 참석이 불가능 하다.<br>

### 1. 파티 참석 시간 저장
처음엔 for 문을 사용하여 파티를 참석한 다음의 현재 시간을 저장했으나 반례에서 실패하는 경우가 발생함.<br>
```angular2html
5
8 24
8 9
8 9
9 10
9 10
```
5개 다 참석 가능한 시간이지만 시작시간 오름차순+같을 시 끝나는 시간 오름차순 으로 하자 9 시에 열리는 파티는 1개만 참석이 가능했다...

### 2. 시간을 30분단위로 변환하여 참석한 시간 체크
24시간을 30분 단위로 나타내기 위해 입력 값에서 *2 를 하여 30분 단위로 저장했다. <br>
이미 참석한 시간대는 `boolean` 배열 안에서 true 로 저장하여 참석 여부 표시를 한다. <br>
시작 시간이 아닌 끝나는 시간을 오름차순으로 정렬한다.

이렇게 해서 위의 입력을 받았을 때 `parties` 에는 다음과 같이 저장된다.
```java
parties[0] = {16, 48}
parties[1] = {16, 18}
parties[2] = {16, 18}
parties[3] = {18, 20}
parties[4] = {18, 20}
```

끝시간을 기준으로 정렬한 뒤
```java
parties[1] = {16, 18}
parties[2] = {16, 18}
parties[3] = {18, 20}
parties[4] = {18, 20}
parties[0] = {16, 48}
```
정렬된 첫번째 파티는 `{8, 18}` 이다. <br>
이를 30분단위로 변환하면 `{16, 18}` 이 된다. <br>
attend[i] 에 해당하는 시간(16)을 true 로 바꾼다. <br>

두번째 파티 역시 `{8, 18}` 에 열렸다. <br>
이를 30분단위로 변환하면 `{16, 18}` 이 되는데 16은 true 이기 때문에 i 가 ++ 되게 된다.<br>
따라서 17에 참석 가능하게 되고 17은 true 가 된다.<br>

이러한 방법으로 모든 파티에 참석 가능한 시간대를 체크하여 cnt 를 계산한다.

### 풀이

```java
public class Main_4055 {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int day = 1;

        while (true) {
            int p = Integer.parseInt(br.readLine());
            if (p == 0) break;

            int[][] parties = new int[p][2];
            boolean[] attend = new boolean[50]; // 24시간을 30분 단위로 나타내기 위해 50 크기의 배열 사용

            for (int i = 0; i < p; i++) {
                String[] input = br.readLine().split(" ");
                int st = Integer.parseInt(input[0]);
                int en = Integer.parseInt(input[1]);

                parties[i][0] = st * 2; // 시작 시간을 30분 단위로 변환
                parties[i][1] = en * 2; // 끝 시간을 30분 단위로 변환
            }

            Arrays.sort(parties, (a, b) -> a[1] - b[1]); // 끝 시간을 기준으로 오름차순 정렬

            int cnt = 0;
            for (int[] party : parties) {
                int startTime = party[0];
                int endTime = party[1];

                for (int i = startTime; i < endTime; i++) {
                    if (!attend[i]) {
                        attend[i] = true;
                        cnt++;
                        break;
                    }
                }
            }

            System.out.println("On day " + day + " Emma can attend as many as " + cnt + " parties.");
            day++;
        }

        br.close();
    }
}
```
