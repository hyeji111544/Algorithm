##   <a href="https://www.acmicpc.net/problem/10828">📖 백준 10828 (스택) 📖</a>



### 접근법

```
push X: 정수 X를 스택에 넣는 연산이다.
pop: 스택에서 가장 위에 있는 정수를 빼고, 그 수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.
size: 스택에 들어있는 정수의 개수를 출력한다.
empty: 스택이 비어있으면 1, 아니면 0을 출력한다.
top: 스택의 가장 위에 있는 정수를 출력한다. 만약 스택에 들어있는 정수가 없는 경우에는 -1을 출력한다.
위의 명령을 처리하는 프로그램
```

스택의 선언은 다음과 같다. `Stack<Integer> stack = new Stack<>();` <br>
`push` 는 `stack.push(숫자)` <br>
`pop` 은 요소를 제거한 뒤 제거된 수를 반환함. `stack.pop()`<br>
`size` 는 `stack.size` <br>
`empty` 는 `stack.isEmpty()` 이는 boolean 타입으로 리턴된다.<br>
`top` 의 경우 `stack.peek()`  이다. <br>

기본적으로 제공되는 메서드를 활용할 수 있으며 시간 초과 방지를 위해
`buffer` 를 사용하여 작성하며 각 케이스는 `swich` 로 해결한다.


### 풀이

```
public class Main {
	public static void main(String[] args) {
        try {
                BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
                BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(System.out));
                
                int N = Integer.parseInt(reader.readLine()); // 명령의 수
                
                Stack<Integer> stack = new Stack<>();
                
                for(int i=0; i<N; i++) {
                    String input = reader.readLine();
                    String[] stackList = input.split(" ");
                    String name = stackList[0];
                    // 입력된 명령어에 따른 case 처리
                    switch (name) {
                        case "push": {
                            Integer num= Integer.parseInt(stackList[1]);
                            stack.push(num);
                            break;
                        }
                        case "pop":{	
                            if(stack.isEmpty()) {
                                writer.write(String.valueOf(-1)+ "\n");
                            }else {
                                writer.write(String.valueOf(stack.pop()) + "\n");
                            }
                            break;
                        }
                        case "size" : {
                            writer.write(String.valueOf(stack.size()) + "\n");
                            break;
                        }
                        case "empty" : {
                            if(stack.isEmpty()) {
                                writer.write(String.valueOf(1) + "\n");
                            }else {
                                writer.write(String.valueOf(0) + "\n");
                            }
                            break;
                        }
                        case "top" : {
                            if(stack.isEmpty()) {
                                writer.write(String.valueOf(-1) + "\n");
                            }else {
                                writer.write(String.valueOf(stack.peek()) + "\n");
                            }
                            break;
                        }
                    }
    
                }
        writer.flush();
        writer.close();
        reader.close();
                
        }catch (Exception e) {
            e.printStackTrace();
        }
		
	}
}

```
