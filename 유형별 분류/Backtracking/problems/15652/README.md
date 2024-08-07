##  [🩶 백준 15652 (N과 M (4)) 🩶](https://www.acmicpc.net/problem/15652)


### 메모
```
재귀
```

### 정리


### 내 답안
```java
public class Main {

    static int N;
    static int M;
    static int[] arr;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

		StringTokenizer st = new StringTokenizer(br.readLine());
		N = Integer.parseInt(st.nextToken());
		M = Integer.parseInt(st.nextToken());
		arr = new int[M];

        backtracking(1, 0);

        bw.flush();
        bw.close();
        br.close();

    }

    // start: 시작 값, size: 현재 수열의 길이
    public static void backtracking(int start, int size) {

        // 수열 길이가 M -> 출력
        if(size == M) {
            for (int a : arr) {
                System.out.print(a + " ");
            }
            System.out.println();
            return;
        }

        // start(1)부터 N까지 반복
        for (int i = start; i <= N; i++) {
            arr[size] = i;
            backtracking(i, size + 1);
        }
        
    }
}

```
