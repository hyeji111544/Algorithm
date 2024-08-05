##   <a href="https://www.acmicpc.net/problem/27433">📖 백준 27433 (팩토리얼 2) 📖</a>



### 문제

![image](https://github.com/user-attachments/assets/0c6a2445-a6ef-443b-a86e-ed8a29b66f1c)


### 접근법
1. 재귀함수를 통해 팩토리얼 문제를 풀어야 한다. 이때 1부터 입력받은 N 까지 곱해야 함. <br>
2. 재귀함수에 사용하기 위해 1부터 증가될 `input_num`와 합계를 저장할 `result` 를 `static` 으로 선언 <br>
3. 루프 방지를 위해 `input_num` 이 입력받은 N 보다 큰지 확인한다.  <br>
4. 문제의 최대 입력값은 20인데 이를 팩토리얼 계산하면 `2432902008176640000` int 의 범위를 넘어섬으로 `long` 타입으로 result 를 지정함.

### 풀이

```java
public class Main_27433 {
	static int input_num=1;
	static long result=1;
	public static long factorial(int s) {
		if(s==0) return 1;
		else if(input_num<=s){
			result*=input_num;
			//System.out.println(input_num+" : " +result);
			input_num++;

			return factorial(s);
		}
		else return result;
		
	}
	public static void main(String[] args) throws IOException{
	
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
	int n = Integer.parseInt(br.readLine());
	
	System.out.println(factorial(n));
	}

}
```
