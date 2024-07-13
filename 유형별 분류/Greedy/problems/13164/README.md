##  [💛 백준 13164 (행복 유치원) 💛](https://www.acmicpc.net/problem/13164)


### 메모
```
차이가 큰 순으로 정렬해서 팀 수 -1 개만큼 삭제?
```

### 정리
`add()` : 에러 발생 시 예외 던짐 <br>
`offer()` : 에러 발생 시 false 반환 <br><br>
`Integer::intValue` :
Integer::intValue는 Integer 객체의 인스턴스 메서드 intValue를 참조합니다. 이 메서드는 Integer 객체를 기본형 int로 변환합니다.

### 내 답안
```java

public class Main {
	public static void main(String[] args) throws IOException {
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		String[] inputs = br.readLine().split(" ");
		int N = Integer.parseInt(inputs[0]);
		int M = Integer.parseInt(inputs[1]);

		StringTokenizer st = new StringTokenizer(br.readLine());

		int[] height = new int[N];

        // 키 입력
		for (int i = 0; i < N; i++) {
			height[i] = Integer.parseInt(st.nextToken());
		}

		Queue<Integer> gaps = new PriorityQueue<>(Comparator.comparingInt(Integer::intValue).reversed());

		for (int i = 0; i < N - 1; i++) {
			gaps.add(height[i + 1] - height[i]);
		}

		for (int i = 0; i < M - 1; i++) {
			gaps.remove();
		}
		br.close();
		
        // 남아 있는 gaps 값들의 합 계산
        int sum = 0;
        while (!gaps.isEmpty()) {
            sum += gaps.remove();
        }

        System.out.println(sum);
   }
}
```
