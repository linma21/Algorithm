##  [🩶 백준 2605 (줄 세우기) 🩶](https://www.acmicpc.net/problem/2605)



### 메모


### 정리


### 내 답안

``` java

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        // 첫 번째 줄에서 숫자 n을 읽어옴
        int n = Integer.parseInt(br.readLine().trim());

        // 숫자를 담을 리스트 생성
        List<Integer> num = new ArrayList<>();
        
        // 두 번째 줄에서 n개의 숫자를 읽어옴
        StringTokenizer st = new StringTokenizer(br.readLine());

        for (int i = 0; i < n; i++) {
            int k = Integer.parseInt(st.nextToken());
            // i-k 인덱스에 i+1 값을 추가
            num.add(i - k, i + 1);        
        }

        // 결과 출력
        for (int m : num) {
            bw.write(m + " ");
        }
        bw.flush();
        br.close();
        bw.close();
    }
}

```

