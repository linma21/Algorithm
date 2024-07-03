##  [🤎 백준 20124 (모르고리즘 회장님 추천 받습니다) 🤎](https://www.acmicpc.net/problem/20124)



### 메모


### 정리
`compareTo` 메서드

| 반환 값          | 의미                                    |
|------------------|-----------------------------------------|
| 음수             | 현재 객체가 비교 대상 객체보다 작음     |
| 0                | 현재 객체가 비교 대상 객체와 같음       |
| 양수             | 현재 객체가 비교 대상 객체보다 큼       |


### 내 답안 
```java

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 첫 번째 줄에서 숫자 n을 읽어옴
        int n = Integer.parseInt(br.readLine().trim());
		String president = "";
		int score = 0;
        // n명의 후보와 점수 입력
        for (int k = 0; k < n; k++) {
			String aa = br.readLine();
			String[] stf = aa.split(" ");
			String name = stf[0];
			Integer record= Integer.parseInt(stf[1]);

			if(score < record){
				score = record;
				president = name;
			}else if(score == record){
				// 점수가 같을 경우 이름을 사전순으로 정렬
                if (name.compareTo(president) < 0) {
                    president = name;
                }
			}
        }
        System.out.println(president);

        br.close();
    }
}

```

