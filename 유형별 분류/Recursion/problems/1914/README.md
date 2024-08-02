##  [💛 백준 1914 (하노이 탑) 💛](https://www.acmicpc.net/problem/1914)


### 메모
```
11729와 같음
```

### 정리
N이 100이하의 자연수이기 때문에 이동 횟수를 `int`나 `long`으로 처리 불가. `BigInteger` 사용

1. **BigInteger.TWO**
   - **설명**: 값이 2인 `BigInteger` 상수임.
   - **사용 예시**: `BigInteger.TWO`는 2를 표현하는 `BigInteger` 객체를 반환함.

2. **pow(int exponent)**
   - **설명**: 이 `BigInteger` 값을 `exponent` 제곱함.
   - **사용 예시**: 
     ```java
     BigInteger result = BigInteger.TWO.pow(N);
     ```
     `BigInteger.TWO.pow(N)`는 \(2^N\)을 계산함.

3. **subtract(BigInteger val)**
   - **설명**: 이 `BigInteger` 값에서 지정된 `BigInteger` 값을 뺌.
   - **사용 예시**: 
     ```java
     BigInteger num = BigInteger.TWO.pow(N).subtract(BigInteger.ONE);
     ```
     `BigInteger.TWO.pow(N).subtract(BigInteger.ONE)`는 \(2^N - 1\)을 계산함.

4. **BigInteger.ONE**
   - **설명**: 값이 1인 `BigInteger` 상수임.
   - **사용 예시**: `BigInteger.ONE`는 1을 표현하는 `BigInteger` 객체를 반환함.

### 내 답안
```java
// 한 층
class Floor {

    int x, y;

    Floor(int x, int y) {
        this.x = x;
        this.y = y;
    }

    @Override
    public String toString() {
        return x + " " + y + "\n";
    }
}

public class Main {

    static List<Floor> result = new ArrayList<>();

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int N = Integer.parseInt(br.readLine());

        // 결과 출력
        BigInteger num = BigInteger.TWO.pow(N).subtract(BigInteger.ONE);
        bw.write(num + "\n");

        // N이 20 이하인 경우에만 실제 이동 과정을 출력
        if (N <= 20) {
            //(원판수, 출발지, 도착지, 경유지)
            Hanoi(N, 1, 3, 2);
            for (Floor move : result) {
                bw.write(move.toString());
            }
        }
        bw.flush();
        bw.close();

    }

    public static void Hanoi(int n, int from, int to, int inter) {
        if (n == 0) {
            return;
        }
        // N-1개의 원판을 출발지에서 경유지로 이동
        Hanoi(n - 1, from, inter, to);
        // 가장 큰 원판을 출발지에서 목적지로 이동
        result.add(new Floor(from, to));
        // N-1개의 원판을 경유지에서 목적지로 이동
        Hanoi(n - 1, inter, to, from);
    }
}

```
