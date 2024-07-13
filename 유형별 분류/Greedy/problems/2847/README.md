##  [🩶 백준 2847 (게임을 만든 동준이) 🩶](https://www.acmicpc.net/problem/2847)


### 메모
```
N개의 레벨 중에서 가장 높은 레벨 부터 역순으로 비교해서 차이만큼 count에 더해준다
```

### 정리


### 내 답안
```java
public class Main {
	public static void main(String[] args) throws IOException {
		
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int N = Integer.parseInt(br.readLine());
		int[] score = new int[N];
		
		for(int i = 0; i < N ; i++) {
			score[i] = Integer.parseInt(br.readLine());
		}
		
		int count = 0;
		
		for(int i = N - 2 ; i >= 0; i--) {
			if(score[i] >= score[i + 1]) {
				int gap = score[i] - score[i + 1] + 1;
				score[i] -= gap;
				count += gap;
			}	 
		}
		System.out.println(count);
		br.close();
		
   }
}

```
