##  [🤎 백준 28417 (스케이트보드) 🤎](https://www.acmicpc.net/problem/28417)



### 메모


### 정리


### 내 답안 
```java

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 첫 번째 줄에서 숫자 n을 읽어옴
        int n = Integer.parseInt(br.readLine().trim());
        int bestScore = 0;

        // 2개의 런, 5개의 트릭점수 입력
        for (int k = 0; k < n; k++) {
            StringTokenizer st = new StringTokenizer(br.readLine());

            // 두 값 중 큰 값을 score에 할당
            int first = Integer.parseInt(st.nextToken());
            int second = Integer.parseInt(st.nextToken());
            int score = first > second ? first : second;

            List<Integer> trickScores = new ArrayList<>();
            for (int i = 0; i < 5; i++) {
                trickScores.add(Integer.parseInt(st.nextToken()));
            }
            // 점수 큰 순 정렬
            Collections.sort(trickScores, Collections.reverseOrder());

            score += trickScores.get(0) + trickScores.get(1);

            if (score > bestScore) {
                bestScore = score;
            }
        }
        System.out.println(bestScore);

        br.close();
    }
}

```

