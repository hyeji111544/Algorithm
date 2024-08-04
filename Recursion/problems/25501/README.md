##   <a href="https://www.acmicpc.net/problem/25501">📖 백준 25501 (재귀의 귀재) 📖</a>



### 문제
첫째 줄에 테스트케이스의 개수 
$T$가 주어진다. (
$1 \leq T \leq 1\,000$)

둘째 줄부터 
$T$개의 줄에 알파벳 대문자로 구성된 문자열 
$S$가 주어진다. (
$1 \leq \vert S\vert \leq 1\,000$)

각 테스트케이스마다, isPalindrome 함수의 반환값과 recursion 함수의 호출 횟수를 한 줄에 공백으로 구분하여 출력한다.

### 접근법
풀이를 위한 재귀 함수 `recursion` 와 호출하는 `isPalindrome` 는 문제에서 주어진다.
재귀 함수의 호출 횟수를 출력하기 위해 `static int result`를 사용함.
`static` 을 초기화 하기 위해 for 문 안에서 0 으로 초기화 한다.


```java
public class Main {
	
	static int result;
	public static int recursion(String s, int l, int r){
		result++;
        if(l >= r) return 1;
        else if(s.charAt(l) != s.charAt(r)) return 0;
        else return recursion(s, l+1, r-1);
    }
    public static int isPalindrome(String s){
        return recursion(s, 0, s.length()-1);
    }
    
    public static void main(String[] args)throws IOException{
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
    		int N = Integer.parseInt(reader.readLine());
    		for(int i = 0 ; i<N; i++) {
    			String testCase = reader.readLine();
    			result = 0;
    			int e = isPalindrome(testCase);
    			System.out.println(e+" "+ result);
    		}
    	
    }
}

```
