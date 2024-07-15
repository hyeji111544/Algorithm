##   <a href="https://www.acmicpc.net/problem/1339">📖 백준 1339 (단어 수학) 📖</a>

### 문제
![image](https://github.com/user-attachments/assets/a388c6da-8c59-40d1-b5db-6874d97e6e79)

## 접근법
최댓값을 찾는 문제로 입력 받은 단어의 자릿수를 만들고 각 단어의 합을 구하여 높은 값부터 9,8,7,... 을 대입한다.<br>
- ABCDE
  - ABCDE = 10000 + 1000 + 100 + 10 + 1 로 나타낼 수 있다.
  - 즉 A = 10000, B = 1000, C = 100, D = 10, E = 1

이 가중치가 높은 순으로 9, 8, 7,... 을 곱해주면 된다.

### 코드 해설
1. 처음 배열 alpha 는 알파벳 갯수만큼 선언함.
2. pos 는 가중치를 의미한다.
3. `alpha[input[j] -'A'] += Integer.valueOf(pos);` 의 input[j]-A 는 입력된 문자열의 j번째 문자와 `A` 사이의 거리를 의미한다.<br>
   'A'는 0, 'B'는 1, ... 'Z'는 25가 된다. 따라서 input[j]가 'A'일 경우 `alpha[0]` 이다.
4. `alpha` 에는 [1, 0, 1000, 100, ...., 0] 이런식으로 가중치가 저장되게 된다. 이를 내림차순으로 정렬한다.
5. 높은 수 부터 9, 8, ... 을 곱하여 sum 에 더한다.

```java
2
GCF
ACDEB
일때
G = 100, C = 10, F = 1 
// alpha[6]=100, alpha[2] = 10, alpha[5]= 1
A = 10000, C = 1000, D = 100, E = 10, B=1 (C 는 1010 이 된다.)
// alpha[0]=10000, alpha[2] = 1000, alpha[3]=100, alpha[4]=10, alpha[1]=1

이를 정렬하면 다음과 같다.
[10000, 1010, 100, 100, 10, 1, 1, 0,...,0]
높은 수 부터 9 -> 1 로 곱하면
90000 + 8080 + 700 + 600 + 50 + 4 + 3 = 99437
```
### 풀이

```java
public class Main_1339 {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());
        Integer [] alpha = new Integer[26]; // 알파벳 수 만큼 배열 선언

        Arrays.fill(alpha, 0); // 배열을 0 으로 초기화

        for(int i=0; i<N; i++) {
            char input[] = br.readLine().toCharArray();
            int pos = 1;

            for(int j=input.length-1; j>=0; j--) {
                alpha[input[j] -'A'] += Integer.valueOf(pos);
                pos*= 10;
            }
        }

        Arrays.sort(alpha, Collections.reverseOrder());
        int num = 9;
        int sum = 0;

        for(int i=0; i<alpha.length; i++) {
            if(alpha[i]==0) {
                break;
            }
            sum += alpha[i] * num;
            num--;
        }
        System.out.println(sum);
    }
}
```
