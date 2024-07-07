##  [🩶 백준 1417 (국회의원 선거) 🩶](https://www.acmicpc.net/problem/1417)

### 메모
```
가장 많은 표를 받는 후보자의 지지자를 하나씩 빼오면 된다.

```

### 정리


### 내 답안

``` java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        int[] numbers = new int[N];

        for(int i = 0; i < N; i++){
            numbers[i] = Integer.parseInt(br.readLine());
        }

        int count = 0;

        while(numbers.length > 1){

            // 다솜을 제외한 사람 중 가장 큰 값
            int maxIndex = 1;
            for (int i = 1; i < N; i++) {
                if (numbers[i] > numbers[maxIndex]) {
                    maxIndex = i;
                }
            }

            // numbers[0]이 가장 크면 종료
            if (numbers[0] > numbers[maxIndex]) {
                break;
            }

            // 가장 큰 값에서 1을 빼고 numbers[0]에 1을 더함
            numbers[maxIndex]--;
            numbers[0]++;
            count++;
        }
        System.out.println(count);
        
        br.close();
    }
}

```
