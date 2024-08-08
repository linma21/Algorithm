##  [🩶 백준 14889 (스타트와 링크) 🩶](https://www.acmicpc.net/problem/14889)

### 메모
```
최소값만 출력하면 되는 문제.
```

### 정리
`Math.abs()` : 절댓값
### 내 답안
```java
public class Main {

    static int N;
    static int[][] arr;
    static boolean[] check; // 선수별 팀 유무
    static int MIN_GAP = Integer.MAX_VALUE;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        N = Integer.parseInt(br.readLine());
        arr = new int[N][N];
        check = new boolean[N];

        // 배열 값 넣기
        for (int i = 0; i < N; i++) {
            StringTokenizer st = new StringTokenizer(br.readLine());
            for (int k = 0; k < N; k++) {
                arr[i][k] = Integer.parseInt(st.nextToken());
            }
        }
        backtracking(0, 0);
        System.out.println(MIN_GAP);

        br.close();

    }

    static void backtracking(int player, int index) {
        int start = 0;
        int link = 0;

        // 팀나누기가 완료되면 
        if (player == N) {

            for (int i = 0; i < N - 1; i++) {
                for (int j = i + 1; j < N; j++) {

                    if (check[i] && check[j]) {
                        // check가 true인 경우 스타트 팀
                        start += arr[i][j];
                        start += arr[j][i];

                    } else if (!check[i] && !check[j]) {
                        // check가 false인 경우 링크 팀
                        link += arr[i][j];
                        link += arr[j][i];
                    }

                }
            }
            // 최소값 갱신
            if (MIN_GAP > Math.abs(start - link)) {
                MIN_GAP = Math.abs(start - link);
            }
            return;
        }

        // 아직 팀이 없는 사람이 있는 경우
        for (int i = index; i < N; i++) {
            if (!check[i]) {
                check[i] = true;
                backtracking(player + 2, i + 1);
                check[i] = false;
            }
        }
    }
}

```
