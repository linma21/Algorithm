##  [🩶 백준 10828 (스택) 🩶](https://www.acmicpc.net/problem/10828)



### 메모
```


```

### 정리
| Stack 명령어              | 설명              |
|-------------------|-------------------|
| `push(E item)`    | 요소를 추가       |
| `pop()`           | 요소를 제거 및 반환|
| `peek()`          | 요소를 반환        |
| `isEmpty()`       | 비어 있는지 확인   |
| `search(Object o)`| 객체의 위치 찾기   |
| `size()`          | 요소의 개수 반환   |


### 내 답안

``` java

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int N = Integer.parseInt(br.readLine());

        Stack<Integer> stack = new Stack<>();

        for(int i = 0; i < N; i++){

            String input = br.readLine();
            String[] inputs = input.split(" ");
            String order = inputs[0];

            switch (order){
                case "push" : {
                    int X = Integer.parseInt(inputs[1]);
                    stack.push(X);
                    break;
                }
                case "pop" : {
                    if(stack.isEmpty()) {
                        bw.write("-1 \n");
                    }else {
                        bw.write(String.valueOf(stack.pop()) + "\n");
                    }
                    break;
                }
                case "size" : {
                    bw.write(String.valueOf(stack.size()) + "\n");
                    break;
                }
                case "empty" : {
                    if(stack.isEmpty()) {
                        bw.write("1 \n");
                    }else {
                        bw.write("0 \n");
                    }
                    break;
                }
                case "top" : {
                    if(stack.isEmpty()) {
                        bw.write("-1 \n");
                    }else {
                        bw.write(String.valueOf(stack.peek()) + "\n");
                    }
                    break;
                }
            }

        }
        bw.flush();
        bw.close();
        br.close();
    }
}

```
