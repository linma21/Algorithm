##   <a href="https://www.acmicpc.net/problem/20124">📖 백준 27522 (모르고리즘 회장님 추천 받습니다 ) 📖</a>



### 메모
```
retire가 없고, 모든 레이서가 서로 다른 시각에 들어온다는 걸 문제에서 보장해주기 때문에 그냥 시간 순으로 정렬하면 된다.
``` 

### 정리
- `Comparator` 사용을 위해 배열로 값을 받는다. <br>
- `comparingLong`는 `Override`할 필요없이 사용가능 <br>
- `.reversed()` 붙이면 내림차순 

### 내 답안 

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.Comparator;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

        int redTeamScore = 0;
        int blueTeamScore = 0;
        String[] inputs = new String[8];

        // 문자열 입력받기
        for (int i = 0; i < 8; i++) {
           
            inputs[i] = reader.readLine();
        }

        for (int i = 0; i < 8; i++) {
            String input = inputs[i];

            // ":"과 " " (공백)을 기준으로 분리
            String[] parts = input.split(":");
            int m = Integer.parseInt(parts[0]);
            int ss = Integer.parseInt(parts[1]);
            int sss = Integer.parseInt(parts[2].split(" ")[0]);
            String team = parts[2].split(" ")[1];

            // 전체 밀리초로 변환
            long totalMilliseconds = m * 60 * 1000 + ss * 1000 + sss;

            // 배열에 저장
            inputs[i] = totalMilliseconds + " " + team;
        }

        // 시간 오름차순으로(빠른순) 정렬
        Arrays.sort(inputs, Comparator.comparingLong(s -> Long.parseLong(s.split(" ")[0])));

        // 점수 부여
        int score[] = {10,8,6,5,4,3,2,1};
        for (int i = 0; i < 8; i++) {
            String[] parts = inputs[i].split(" ");
            String team = parts[1];

            if (team.equals("R")) {
                redTeamScore += score[i];
            } else if (team.equals("B")) {
                blueTeamScore += score[i];
            }
        }
        // 승자 결정
        String winner = (redTeamScore > blueTeamScore) ? "Red" : "Blue";
        System.out.print(winner);
    }
}


```

