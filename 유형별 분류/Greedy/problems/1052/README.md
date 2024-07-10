##  [💛 백준 1052 (물병) 💛](https://www.acmicpc.net/problem/1052)

### 메모
```
N을 2의 제곱수로 만들면 되는 문제??
-> 2로 나눠지는 만큼 계속 나누다가 K보다 작아지면 굳이 물병 구매 안해도 됨

```

### 정리
```
while (Integer.bitCount(N) > K) {
    count++;
    N++;
}

```
- `.bitCount(N)` : N의 이진수 표현의 1의 개수 반환 
- N이 K보다 크면 K보다 `bitCount`가 크기 때문에 물병 수가 K보다 작아질 때까지 반복 
### 내 답안
1. 제출안함 -> N이 홀수일 때 무조건 보틀을 구매하기 때문에 틀린듯?
```java
public class Main {

    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int N = Integer.parseInt(st.nextToken());
        int K = Integer.parseInt(st.nextToken());

        int count = 0;
        int water = 1;
        while (true) {
            if(N <= K) {
                break;
            }else if(N % 2 != 0) {
            // N이 홀수 일 때 물양만큼 물병 구매
                count += water;
                N = (N + 1)/ 2;
                water *= 2;
            }else {
                N = N / 2;
                water *= 2;
            }
        }
        System.out.println(count);
        
        br.close();
    }
}

```
2. 물병 수 따로 count하기 
```java
public class Main {

    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int N = Integer.parseInt(st.nextToken());
        int K = Integer.parseInt(st.nextToken());

        int count = 0;
        while (true) {
            int copy_N = N;
            int nowBottles = 0;
            
            // 물병을 2로 계속 나눔
            while (copy_N > 0) {
                if (copy_N % 2 == 1) {
                    nowBottles++;
                    copy_N -= 1;
                }
                copy_N /= 2;
            }
            if (nowBottles <= K) {
                break;
            }
            
            count++;
            // 현재 N으로는 물병 < K를 만들 수 없으니 물병 하나를 사서 다시 도전
            N++;
        }
        System.out.println(count);
        

        br.close();
    }
}

```