##  [🩶 백준 1620 (나는야 포켓몬 마스터 이다솜) 🩶](https://www.acmicpc.net/problem/1620)



### 메모
```
숫자를 입력받으면 문자를, 문자를 입력받으면 숫자를 출력해야 함

```

### 정리
- `Character.isDigit(문자)` : 문자가 숫자면 true

| 데이터 구조 | 시간 복잡도 | 성능 문제 |
|-------------|-------------|-----------|
| `ArrayList` | - 요소 추가: <br> O(1) per element, <br> 총 O(N)<br>  <br> - 조회: <br> 숫자 쿼리: O(1) <br> 문자열 쿼리: O(N) (최악의 경우 전체 리스트 검색) | 문자열 쿼리에서 선형 검색으로 인해 최악의 경우 O(N*M)의 시간 복잡도 발생 |
| `HashMap` | - 요소 추가: <br> 평균 O(1) per element, <br> 총 O(N) <br> <br> - 조회: <br> 숫자 쿼리: 평균 O(1) <br> 문자열 쿼리: 평균 O(1) | 두 종류의 쿼리가 평균적으로 상수 시간 안에 처리되어 쿼리 처리의 전체 복잡도가 O(M)으로 줄어든다. |

### 내 답안
1. `ArrayList` 를 사용 -> <span style="background-color:#FFE6E6"> 시간초과! </span>

``` java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.ArrayList;
import java.util.StringTokenizer;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        // 입력받은 도감 포켓몬 수(N)과 문제 수(M) 분리 
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		
        // 도감 포켓몬들 입력받기 
        ArrayList<String> pokemon = new ArrayList<>();
		for(int i=0;i<N;i++) {
			pokemon.add(br.readLine());
		}
		
        // 문제 입력받기 
		for(int i =0;i< M; i++) {
			String str = br.readLine();

            // 숫자 입력 -> 문자 출력
			if(Character.isDigit(str.charAt(0))) {
				int num = Integer.parseInt(str);
				bw.write(pokemon.get(num-1)+"\n");

                // 문자 입력 -> 숫자 출력
			} else {
				int num = pokemon.indexOf(str);
				bw.write(num+1+"\n");
			}
		}
		
		bw.flush();
		bw.close();
		br.close();
	}
}
```

2. `HashMap` 두개 쓰기
```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.HashMap;
import java.util.Map;
import java.util.StringTokenizer;

public class Main {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        // 입력받은 도감 포켓몬 수(N)과 문제 수(M) 분리 
		StringTokenizer st = new StringTokenizer(br.readLine());
		int N = Integer.parseInt(st.nextToken());
		int M = Integer.parseInt(st.nextToken());
		
        // <번호, 이름> , <이름, 번호>인 map 각각 생성
		Map<Integer, String> keyisNum = new HashMap<>();
		Map<String, Integer> keyisName = new HashMap<>();

		// map 값 추가
		for(int i = 0; i < N; i++) {
			String pokemon = br.readLine();
			keyisNum.put(i + 1, pokemon);
			keyisName.put(pokemon, i + 1);
		}
		
        // 문제 입력받기 
		for(int i =0;i< M; i++) {
			String str = br.readLine();

            // 숫자 입력 -> 문자 출력
			if(Character.isDigit(str.charAt(0))) {
				int num = Integer.parseInt(str);
				bw.write(keyisNum.get(num)+"\n");

                // 문자 입력 -> 숫자 출력
			} else {
				bw.write(keyisName.get(str)+"\n");
			}
		}
		bw.flush();
		bw.close();
		br.close();
	}
}
```
