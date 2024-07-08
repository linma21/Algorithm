##  [🩶 백준 1931 (회의실 배정) 🩶](https://www.acmicpc.net/problem/1931)


### 메모
```

```

### 정리


### 내 답안 
```java
public class Main {

    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        int[][] time = new int[N][2];

        StringTokenizer st;
        for (int i = 0; i < N; i ++) {
            st = new StringTokenizer(br.readLine());
            time[i][0] = Integer.parseInt(st.nextToken()); // 시작
            time[i][1] = Integer.parseInt(st.nextToken()); // 종료
        }
        Arrays.sort(time, (a, b) -> {

                if(a[1] == b[1]) { 
                    // end가 같으면 시작시간 기준
                    return a[0] - b[0];
                }
                // end 기준으로 정렬
                return a[1] - b[1];
        });
        int count = 0;
        int nowEnd = 0;
        
        for (int i = 0; i < N; i++) {
            if(nowEnd <= time[i][0]) {
                nowEnd = time[i][1];
                count++;
            }
        }

        System.out.println(count);

        br.close();
    }
}

```
