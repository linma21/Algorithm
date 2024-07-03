##  [🩶 백준 31562 (전주 듣고 노래 맞히기) 🩶](https://www.acmicpc.net/problem/31562)


### 메모


### 정리
- `.replaceAll("\\s", "")` : 공백문자 제거
- `trim()` : 앞뒤 공백문자 제거

### 내 답안

``` java

import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) throws IOException {
        Scanner sc = new Scanner(System.in);

        // 첫 번째 줄에서 숫자 n과 m을 읽어옴
        int n = sc.nextInt();
        int m = sc.nextInt();
		sc.nextLine(); // 개행 문자 소비
		
        Map<String, String> map = new HashMap<>();

        for (int i = 0; i < n; i++) {
            String str = sc.nextLine();
            String[] strs = str.split(" ");
            String music = strs[1];
            String code = strs[2] + strs[3] + strs[4];
            // 이미 있는 code면 기존 value를 "?"로 바꾸기
            if (map.containsKey(code)) {
                map.put(code, "?");
            } else {
                map.put(code, music);
            }
        }

        for (int i = 0; i < m; i++) {
			// 공백문자 제거
			String findKey = sc.nextLine().replaceAll("\\s", "");
			String result = map.get(findKey);
			
            // map에 키가 없으면 "!" 출력
            if (result == null) {
                System.out.println("!");
            } else {
                System.out.println(result);
            }
        }

        sc.close();
    }
}

```


