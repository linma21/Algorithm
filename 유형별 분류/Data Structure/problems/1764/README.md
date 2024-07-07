##  [🩶 백준 1764 (듣보잡) 🩶](https://www.acmicpc.net/problem/1764)



### 메모
```
각각의 명단들은 중복되지 않는다. N+M으로 한 번에 입력받아도 된다.
```

### 정리
- `add(E e)` : 세트에 e가 이미 포함되어 있지 않은 경우에만 e가 추가 <br>
	```
	true: Set에 e가 성공적으로 추가된 경우 (즉, e가 원래 Set에 포함되어 있지 않았을 경우).
    false: Set에 e가 이미 포함되어 있어 추가되지 않은 경우.
    ```
    
### 내 답안

``` java

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        String input = br.readLine();
        String[] inputs = input.split(" ");
        int N = Integer.parseInt(inputs[0]);
        int M = Integer.parseInt(inputs[1]);

        Set<String> namesSet = new HashSet<>();
        List<String> nugu = new ArrayList<>();

        // 듣도 + 보도 
        for (int i = 0; i < N + M; i++) {
            String name = br.readLine();

            // 입력된 값이 이미 있으면 ( = 듣도보도)
            if (!namesSet.add(name)) {
                nugu.add(name);
            }
        }

        // 사전 순으로 정렬
        Collections.sort(nugu);

        System.out.println(nugu.size());
        for (String who : nugu) {
            System.out.println(who);
        }

        br.close();
    }
}

```
