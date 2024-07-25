##  [💛 백준 1889 (선물 교환) 💛](https://www.acmicpc.net/problem/1889)



### 메모
```

```

### 정리


### 내 답안
1. 시간 초과
```java
public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        List<Gift> student = new ArrayList<>(N + 1);

        // 학생들에게 주어지는 선물 쌍 입력 받기
        for (int i = 0; i < N; i++) {
            String[] input = br.readLine().split(" ");
            Gift gift = new Gift(Integer.parseInt(input[0]), Integer.parseInt(input[1]));
            student.add(gift);
        }

        distributeGifts(student, N);
    }

    public static void distributeGifts(List<Gift> student, int N) {
        int[] arr = new int[N + 1];
        List<Integer> toRemove = new ArrayList<>();

        // 각 학생의 선물 쌍 확인
        for (Gift gift : student) {
            arr[gift.one]++;
            arr[gift.two]++;
        }

        boolean twoGiftsOK = true;
        // 모든 학생이 두 개의 선물을 받았는지 확인 -> 두 개 미만인 학생 제거 목록 추가
        for (int i = 1; i <= N; i++) {
            if (arr[i] != 2) {
                twoGiftsOK = false;
                if (arr[i] < 2) {
                    toRemove.add(i);
                }
            }
        }

        if (twoGiftsOK) {
            // 모든 학생이 두 개의 선물을 받은 경우
            System.out.println((student.size() - 1) * 2 / 2);
            for (int i = 0; i < N; i++) {
                if (arr[i] == 2) {
                    System.out.print(i + " ");
                }
            }
        } else {
            // 선물이 부족한 학생 제거
            System.out.println((student.size() - 1) * 2);
            System.out.println(toRemove.size()); 
            for (int i = toRemove.size() - 1; i >= 0; i--) {
                int removeIndex = toRemove.get(i);
                student.removeIf(gift -> gift.one == removeIndex || gift.two == removeIndex);
            }
            // 재귀 호출로 변경된 선물 목록 처리
            distributeGifts(student, N);  
        }
    }
}

class Gift {
    int one;
    int two;

    public Gift(int one, int two) {
        this.one = one;
        this.two = two;
    }
}

```
