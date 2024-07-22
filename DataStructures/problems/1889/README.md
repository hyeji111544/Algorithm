##   <a href="https://www.acmicpc.net/problem/1889">📖 백준 1889 ( 선물 교환 ) 📖</a>

### 문제
![image](https://github.com/user-attachments/assets/f652d1d4-4aa4-4a9f-876a-137f355915c1)


### 접근법


*최대한 많은 학생을 참석 시켜야 함.*
1. 선물을 누가 누구에게 줬는지 저장 해야함. <br>
    `list` 는 사람이 누구에게 받았는지 <br>
    `arr` 는 누구에게 줬는지 저장하는 배열.
2. `list.get(a).add(i)`, `list.get(b).add(i)` 를 통해 a,b 선물함에 i 가 줬다는걸 표시
3. `arr[i][0] = a` , `arr[i][1] = b` i 번째 사람이 누구에게 줬는지 저장
4. 재귀함수를 통해 모든 학생의 선물이 2개로 만듬. `minus` 호출
5. 첫번째 if 에서 선물함이 2개 미만일 시 `arr` 를 확인하여 `list` 에서 제거한다.<br>
    이때 재귀함수 호출을 하기 때문에 `answers == 1` 을 확인하여 무한루프에 빠지지 않게 함.
6. `list` 에 변동이 생기기 때문에 다시 `minus` 안에서 다시 `list` 를 확인하기 위해 재귀함수 호출.
7. `answers` 안에 1이 있는경우 선물을 2개 받은 사람이 있다는 뜻이기 때문에 `buffer` 에 추가


### 풀이

```java
public class Main_1052  {

	public static List<List<Integer>> lists = new ArrayList<>();
	public static int [][] arr;
	public static int [] answers;
	
    public static void main(String[] args) throws IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int size = Integer.parseInt(br.readLine());
		
		arr = new int [size+1][2];
		answers = new int [size +1];
		
		for(int i=0; i<=size ; i++){
			lists.add(new ArrayList<>());
			answers[i] = 1;
		}
		
		
		for(int i =1; i<=size; i++){
			StringTokenizer st = new StringTokenizer(br.readLine());
			int a =Integer.parseInt(st.nextToken());
			int b= Integer.parseInt(st.nextToken());
			
			lists.get(a).add(i);
			lists.get(b).add(i);
			
			arr[i][0] = a;
			arr[i][1] = b;
		}
		
		
		for(int i=1; i<=size ; i++){
			minus(i);
		}
        
		StringBuffer buffer = new StringBuffer();
	
		boolean has = false;
		int index =0;
		
		for(int i=1; i<=size ; i++){
			if(answers[i] == 1){
				buffer.append(i +" ");
				has = true;
				index ++;
			}
		}
		
		if(!has){
			System.out.println(0);
			System.exit(0);
		} else{
			System.out.println(index);
			System.out.println(buffer.toString());
		}
	}
		
	public static void minus(int i){
	
		if(lists.get(i).size() <2){
			if(answers[i] == 1){
                int a = arr[i][0] ;
                int b = arr [i][1] ;
                lists.get(a).remove(Integer.valueOf(i));
                lists.get(b).remove(Integer.valueOf(i));
                answers[i] = 0; 
		
				if(lists.get(a).size() <2){
				    minus(a);
				}
				if(lists.get(b).size() <2){
				    minus(b);
				}
			}
		}
    }
}
```
