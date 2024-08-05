##   <a href="https://www.acmicpc.net/problem/10870">📖 백준 10870 (피보나치) 📖</a>



### 문제

![image](https://github.com/user-attachments/assets/10166c62-ea28-4fd9-94ec-2794466a51ed)


### 접근법
1. 0, 1, 1, 2, 3 처럼 앞의 두 수를 더하여 뒤의 수가 나오게 됨. 따라서 `result1,2,3` 을 선언 <br>
2. 재귀함수의 무한루프 방지를 위해 `count` 가 입력받은 N 보다 큰지 확인한다.(이때 0부터 카운트함) <br>


### 풀이

```java
public class Main_10870 {
	static int count=0;
	static int result1=0;
	static int result2=1;
	static int result3;
	public static int fibo(int s) {
		if(s==0) return 0;
		else if(count<=s){
			result3 = result1;
			result1 = result2;
			result2 += result3;
			
			//System.out.println(count+" : " +result3);
			count++;

			return fibo(s);
		}
		else return result3;
		
	}
	public static void main(String[] args) throws IOException{
		
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	
	int n = Integer.parseInt(br.readLine());
	
	System.out.println(fibo(n));
	}

}
```
