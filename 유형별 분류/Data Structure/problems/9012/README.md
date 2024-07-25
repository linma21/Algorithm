##  [🩶 백준 9012 (괄호) 🩶](https://www.acmicpc.net/problem/9012)


### 메모
```
1. (와 )의 개수가 같아야함.
2. ()가 순서상 한 쌍을 이뤄야함
```

### 정리


### 내 답안
```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int N = Integer.parseInt(br.readLine());

        for (int i = 0; i < N; i++) {

            String ps = br.readLine();
            Stack<Character> psStack = new Stack<>();

            boolean isValid = true; 

            for (int j = 0; j < ps.length(); j++) {
                char ch = ps.charAt(j);

                if (ch == '(') {
                    psStack.push(ch);
                } else if (ch == ')') {
                    // 짝이 맞는 (가 없으면
                    if (psStack.isEmpty()) {
                        isValid = false;
                        break;

                        // 짝이 맞는 ( 가 있으면 삭제
                    } else {
                        psStack.pop();
                    }
                }
            }
            // 짝이 맞아서 stack이 비어있으면
            if (isValid && psStack.isEmpty()) {
                bw.write("YES\n");
            } else {
                bw.write("NO\n");
            }
        }
        bw.flush();
        bw.close();
        br.close();
    }
}


```
