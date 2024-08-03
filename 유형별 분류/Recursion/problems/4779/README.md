##  [🩶 백준 4779 (칸토어 집합) 🩶](https://www.acmicpc.net/problem/4779)

### 메모
```

```

### 정리
```java
while ((input = br.readLine()) != null) {
 }
```
- 입력값 개수가 주어지지 않았을 때 사용 

### 내 답안
```java

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;

public class Main {

    static char[] line;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        String input;

        while ((input = br.readLine()) != null && !input.isEmpty()) {
            int N = Integer.parseInt(input);

            // 3^N
            int length = (int) Math.pow(3, N);
            line = new char[length];

            // 배열의 모든 인덱스에 '-'를 값으로 넣기
            for (int i = 0; i < length; i++) {
                line[i] = '-';
            }

            recursion(0, length);

            bw.write(String.valueOf(line) + "\n");
        }

        bw.flush();
        bw.close();
        br.close();

    }

    static void recursion(int start, int length) {
        if (length <= 1) return;

        int slice = length / 3;

        for (int i = start + slice; i < start + slice * 2; i++) {
            line[i] = ' ';
        }

        recursion(start, slice);

        // 세번째 구역
        recursion(start + slice * 2, slice);
    }
}

```
