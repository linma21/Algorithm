##  [🩶 백준 2161 (카드1) 🩶](https://www.acmicpc.net/problem/2161)



### 메모


### 정리
| 메서드            | 반환 값                          | 예외 처리                           | 사용 용도                             |
|-------------------|----------------------------------|-------------------------------------|---------------------------------------|
| `offer`           | `boolean` (추가 성공 여부)        | 용량 제한 시 `false` 반환           | 큐가 용량 제한을 가질 수 있는 경우 안전하게 사용 |
| `add`             | `boolean` (항상 true 또는 예외 발생) | 용량 제한 시 `IllegalStateException` 던짐 | 예외 상황을 별도로 처리할 필요가 없는 경우 |
| `poll`            | 큐의 앞쪽 요소 또는 `null`         | 큐가 비어 있으면 `null` 반환        | 큐가 비어 있을 때 예외를 피하고 싶은 경우 |
| `remove`          | 큐의 앞쪽 요소                    | 큐가 비어 있으면 `NoSuchElementException` 던짐 | 큐가 비어 있을 때 예외를 통해 처리하고 싶은 경우 |


### 내 답안

``` java

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        // 첫 번째 줄에서 숫자 n을 읽어옴
        int n = Integer.parseInt(br.readLine().trim());

        // 숫자를 담을 큐 생성
        Queue<Integer> queue = new LinkedList<>();

        // 입력받은 N 개 만큼의 카드를 queue 에 저장
        for (int m = 1; m <= n; m++) {
            queue.add(m);
        }

        // 큐가 비어있지 않은 동안 반복
        while (queue.size() > 1) {
            // 제일 위 카드 방출 후 출력
            int s = queue.poll();
            System.out.print(s + " ");

            if (!queue.isEmpty()) {
                // 두번째 카드 방출 후 큐의 끝에 추가
                int qu = queue.poll();
                queue.add(qu);
            }
        }
        System.out.print(queue.poll());

        bw.flush();
        br.close();
        bw.close();
    }
}

```

