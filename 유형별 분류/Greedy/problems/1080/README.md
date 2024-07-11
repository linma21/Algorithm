##  [🩶 백준 1080 (행렬) 🩶](https://www.acmicpc.net/problem/1080)

### 메모
```
모든 값이 일치 해야 하기 때문에 처음부터 하나하나 비교해서 다르면 무조건 뒤집어야함 
```

### 정리


### 내 답안
1. <span style="background-color:#FFE6E6">예제 3) -1이 안됨 </span> : 꼭 (3 * 3) 씩 바꿔야 하기 때문에 N - 3 번까지만 반복
```java
public class Main {

    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int N = Integer.parseInt(st.nextToken());
        int M = Integer.parseInt(st.nextToken());

        int[][] A = new int[N][M];
        int[][] B = new int[N][M];

        // 행렬 A
        for (int i = 0; i < N; i++) {
            String[] tokens = br.readLine().split("");
            for (int k = 0; k < M; k++) {
                A[i][k] = Integer.parseInt(tokens[k]);
            }
        }

        // 행렬 B
        for (int i = 0; i < N; i++) {
            String[] tokens = br.readLine().split("");
            for (int k = 0; k < M; k++) {
                B[i][k] = Integer.parseInt(tokens[k]);
            }
        }
        int count = 0;
        
        // 뒤집기
		for (int i = 0; i < N; i++) { // 행렬의 x좌표(값?)
			for (int k = 0; k < M; k++) { // 행렬의 y좌표

                // 값 하나가 다르면 무조건 뒤집어야함
				if (A[i][k] != B[i][k]) {

                    // 뒤집을 값들 (3 * 3)
                    for (int j = i; j < i + 3 && j < N; j++) {
                        for (int c = k; c < k + 3 && c < M; c++) {
                            A[j][c] = A[j][c] == 1 ? 0 : 1;
                        }
                    }
					count++;
				}
			}
		}
        // 다 뒤집고 다시 비교
        boolean same = true;
        for (int i = 0; i < N; i++) {
			for (int k = 0; k < M; k++) {

                // 하나라도 다르면 false
				if (A[i][k] != B[i][k]) {
					same = false;
                    break;
				}
			}
		}
        count = same ? count : -1;
        System.out.println(count);
        
        br.close();
    }
}

```
2. 뒤집기 범위 수정 
```java
public class Main {

    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int N = Integer.parseInt(st.nextToken());
        int M = Integer.parseInt(st.nextToken());

        int[][] A = new int[N][M];
        int[][] B = new int[N][M];

        // 행렬 A
        for (int i = 0; i < N; i++) {
            String[] tokens = br.readLine().split("");
            for (int k = 0; k < M; k++) {
                A[i][k] = Integer.parseInt(tokens[k]);
            }
        }

        // 행렬 B
        for (int i = 0; i < N; i++) {
            String[] tokens = br.readLine().split("");
            for (int k = 0; k < M; k++) {
                B[i][k] = Integer.parseInt(tokens[k]);
            }
        }
        int count = 0;
        
        // 뒤집기
		for (int i = 0; i <= N - 3; i++) { // 행렬의 x좌표(값?)
			for (int k = 0; k <= M - 3; k++) { // 행렬의 y좌표

                // 값 하나가 다르면 무조건 뒤집어야함
				if (A[i][k] != B[i][k]) {

                    // 뒤집을 값들 (3 * 3)
                    for (int j = i; j < i + 3 && j < N; j++) {
                        for (int c = k; c < k + 3 && c < M; c++) {
                            A[j][c] = A[j][c] == 1 ? 0 : 1;
                        }
                    }
					count++;
				}
			}
		}
        // 다 뒤집고 다시 비교
        boolean same = true;
        for (int i = 0; i < N; i++) {
			for (int k = 0; k < M; k++) {

                // 하나라도 다르면 false
				if (A[i][k] != B[i][k]) {
					same = false;
                    break;
				}
			}
		}
        count = same ? count : -1;
        System.out.println(count);
        
        br.close();
    }
}

```
