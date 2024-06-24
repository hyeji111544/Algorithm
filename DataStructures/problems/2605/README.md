##   <a href="https://www.acmicpc.net/problem/2605">📖 백준 2605 (줄 세우기) 📖</a>



### 접근법
| 학생 번호 | 번호를 뽑은 후 순서                 |
|------------|--------------------------------------|
| 첫 번째    | 1                                    |
| 두 번째    | 2 1                                  |
| 세 번째    | 2 3 1                                |
| 네 번째    | 4 2 3 1                              |
| 다섯 번째  | 4 2 5 3 1                            |

문제의 결과는 다음과 같이 주어진다.
따라서 첫 번째 학생은 index[0]번을 갖게 되고
두번째부터 학생은 뽑은 번호만큼 앞으로가서 리스트에 저장 된다.

즉 for문 안에서 배열의 길이인 i 를 사용해 학생의 수인 n만큼의 배열을 만들고
입력 받은(앞으로갈 번호) k 를 사용해 `list.add(i-k, i+1);` 원하는 index 위치에 저장할 수 있게 한다.


### 풀이

```
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		List<Integer> list = new ArrayList<>();
		
		int n = sc.nextInt();
		
		for(int i =0; i< n; i++) {
			int k= sc.nextInt();
			list.add(i-k, i+1);		
		}
		
		for(int m : list) {
			System.out.print(m + " ");
		}
	}
}
```
