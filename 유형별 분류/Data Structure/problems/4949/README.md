##  [🩶 백준 4949 ( 균형잡힌 세상) 🩶](https://www.acmicpc.net/problem/4949)


### 메모
```
9012와 같음
```

### 정리


### 내 답안
```java

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Stack;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        while (true) {

            String ps = br.readLine();
            if(ps.equals(".")) break;
            Stack<Character> psStack = new Stack<>();

            boolean isValid = true; 

            for (int j = 0; j < ps.length(); j++) {
                char ch = ps.charAt(j);

                if (ch == '(' || ch == '[') {
                    psStack.push(ch);

                } else if (ch == ')') {
                    // 짝이 맞는 ( 가 없으면
                    if (psStack.isEmpty() || psStack.peek() != '(') {
                        isValid = false;
                        break;

                        // 짝이 맞는 ( 가 있으면 삭제
                    } else {
                        psStack.pop();
                    }
                } else if (ch == ']') {
                    // 짝이 맞는 [ 가 없으면
                    if (psStack.isEmpty() || psStack.peek() != '[') {
                        isValid = false;
                        break;

                        // 짝이 맞는 [ 가 있으면 삭제
                    } else {
                        psStack.pop();
                    }
                }
            }
            // 짝이 맞아서 stack이 비어있으면
            if (isValid && psStack.isEmpty()) {
                bw.write("yes\n");
            } else {
                bw.write("no\n");
            }
        }
        bw.flush();
        bw.close();
        br.close();
    }
}


```
