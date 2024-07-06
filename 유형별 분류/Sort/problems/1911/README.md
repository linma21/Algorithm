[백준](https://www.acmicpc.net/problem/1620)##  [🩶 백준 1911 (흙길 보수하기) 🩶](https://www.acmicpc.net/problem/1911)


### 메모
```
111222..333444555.... // 길이 3인 널빤지
.MMMMM..MMMM.MMMM.... // 웅덩이
012345678901234567890 // 좌표
```

### 정리
Comparator 예시
다음은 Comparator가 배열의 여러 요소를 비교하는 과정을 예시로 설명합니다:

```java
코드 복사
Size[] pools = new Size[] {
    new Size(5, 10),
    new Size(2, 7),
    new Size(8, 12),
    new Size(1, 4)
};

// 정렬
Arrays.sort(pools, (a, b) -> Integer.compare(a.start, b.start));
```

정렬 과정에서 a와 b는 배열의 요소를 가리키는 임시 변수로 사용됩니다.<br>
Arrays.sort 메서드는 내부적으로 다음과 같은 순서로 배열을 정렬합니다:<br>

```
첫 번째 비교: new Size(5, 10)와 new Size(2, 7)를 비교합니다.
두 번째 비교: new Size(5, 10)와 new Size(8, 12)를 비교합니다.
세 번째 비교: new Size(5, 10)와 new Size(1, 4)를 비교합니다.
네 번째 비교: new Size(2, 7)와 new Size(8, 12)를 비교합니다.
다섯 번째 비교: new Size(2, 7)와 new Size(1, 4)를 비교합니다.
여섯 번째 비교: new Size(8, 12)와 new Size(1, 4)를 비교합니다.
```

### 내 답안 
1. <span style="background-color:#FFE6E6"> 메모리 초과 </span>
```java

import java.io.IOException;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) throws IOException {
        Scanner sc = new Scanner(System.in);

        String input = sc.nextLine();
        String[] parts = input.split(" ");
        int N = Integer.parseInt(parts[0]);
        int L = Integer.parseInt(parts[1]);

        // 웅덩이 범위 입력
        int[] start = new int[N];
        int[] end = new int[N];

        for (int i = 0; i < N; i++) {
            String pool = sc.nextLine();
            String[] poolSize = pool.split(" ");
            start[i] = Integer.parseInt(poolSize[0]);
            end[i] = Integer.parseInt(poolSize[1]);
        }

        // end 배열 정렬
        Arrays.sort(end);

        // end 배열의 가장 큰 값 찾기
        int maxLength = end[end.length - 1];

        // 땅땅
        List<Character> ground = new ArrayList<>();
        for (int i = 0; i < maxLength; i++) {
            ground.add('G'); // 기본값을 'G'로 초기화
        }

        // 지정된 구간에 웅덩이 넣기
        for (int i = 0; i < N; i++) {
            for (int j = start[i]; j < end[i]; j++) {
                ground.set(j, 'P');
            }
        }
        
        int count = 0;
        while (!ground.isEmpty()) {
            if (ground.get(0) == 'G') {
                ground.remove(0);
            } else if (ground.get(0) == 'P') {
                count++;

                // 발판 길이만큼 삭제
                for (int k = 0; k < L && !ground.isEmpty(); k++) {
                    ground.remove(0);
                }

            }
        }
        System.out.println(count);

        sc.close();
    }
}

```
2. 객체 생성해서 풀기
```java
import java.io.IOException;
import java.util.Arrays;
import java.util.Scanner;

class Size {
    int start;
    int end;

    public Size(int start, int end) {
        this.start = start;
        this.end = end;
    }
}

public class Main {

    public static void main(String[] args) throws IOException {
        Scanner sc = new Scanner(System.in);

        // 개수(N)와 발판의 길이(L)
        int N = sc.nextInt(); 
        int L = sc.nextInt();

        Size[] pools = new Size[N];

        // 웅덩이 범위 입력
        for (int i = 0; i < N; i++) {
            int start = sc.nextInt(); 
            int end = sc.nextInt(); 
            pools[i] = new Size(start, end);
        }

        // 웅덩이 시작 위치 기준으로 정렬
        Arrays.sort(pools, (a, b) -> Integer.compare(a.start, b.start));

        int count = 0;
        int here = 0;

        // 웅덩이마다 발판 설치
        for (int i = 0; i < N; i++) {

            if (here < pools[i].start) {
                // 현재 위치가 웅덩이 시작 위치보다 앞 (땅 위) -> 웅덩이 시작 위치로 이동
                here = pools[i].start; 
            }

            // 현재 위치가 웅덩이 끝을 넘길 때까지
            while (here < pools[i].end) {
                // 현재 위치 이동
                here += L; 
                count++;
            }
        }

        System.out.println(count);

        sc.close();
    }
}

```