##   <a href="https://www.acmicpc.net/problem/4779">📖 백준 4779 (칸토어 집합) 📖</a>



### 문제
![image](https://github.com/user-attachments/assets/89c03dfe-3635-4bc9-911f-9681cd62a4b1)


### 접근법

![image](https://github.com/user-attachments/assets/3521f5d6-4472-4b30-b979-708997818b28)

1. 입력이 2라고 가정했을 때 StringBuilder `sb` 에는 위의 입력과 같이 저장된다. <br>
2. 첫번째 3,4,5 를 빈 문자열 `' '` 로 변경하기 위해 3,4,5 에 해당하는 숫자를 구한다. <br>
   이는 코드상의 `middle` 과 `start+2*middle` 에 해당함. <br>
3. 이후 `start, middle` : 위의 예시에서 0,3 / `start+2*middle, middle` : 예시에서 6,3 으로 재귀호출 한다.  <br>

- 문자를 하나만 바꾸기 위해 `StringBuilder` 의 `setCharAt` 사용
- 입력의 끝을 체크하기 위해 while 내부에서 `number` 를 확인함

### 풀이

```java
public class Main_4779 {
	static StringBuilder sb;
	
	public static void recursion(int start, int length) {
		if(length==1) {
			return;
		}
		int middle = length/3;
		for(int i = start+middle; i<start+2*middle; i++) {
			sb.setCharAt(i, ' ');;
		}
		
		recursion(start, middle);
		recursion(start+2*middle, middle);
	}
    
    public static void main(String[] args)throws IOException{
    	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    	BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
    	
		while(true) {
			String number = br.readLine();
			if (number == null || number.trim().isEmpty()) {
                break;
			}
			sb = new StringBuilder();
			int length = (int) Math.pow(3, Integer.parseInt(number));

	    	
			for(int i = 0; i<length; i++) {
				sb.append('-');
			}
			recursion(0, length);
			bw.write(sb.toString()+'\n');
			bw.flush(); 
			
		}
       
  }
	
}

```
