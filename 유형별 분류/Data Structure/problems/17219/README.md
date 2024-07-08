##  [🩶 백준 17219 (비밀번호 찾기) 🩶](https://www.acmicpc.net/problem/17219)

### 메모

### 정리
    
### 내 답안

``` java
public class Main {

    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String inputs = br.readLine();

        int N = Integer.parseInt(inputs.split(" ")[0]);
        int M = Integer.parseInt(inputs.split(" ")[1]);

        Map<String, String> pass = new HashMap<>();

        for(int i = 0; i < N; i++) {
            String keyValue = br.readLine();
            pass.put(keyValue.split(" ")[0], keyValue.split(" ")[1]);
        }

        for(int k = 0; k < M; k++){
            String site = br.readLine();
            bw.write(pass.get(site) + "\n");
        }

        bw.flush();
        bw.close();
        br.close();
    }
}

```
