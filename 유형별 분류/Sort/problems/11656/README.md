##  [🩶 백준 11656 (접미사 배열) 🩶](https://www.acmicpc.net/problem/11656)



### 메모


### 정리


### 내 답안 
```java
public class Main {

    public static void main(String[] args) throws IOException {
        
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String input = br.readLine();
        int length = input.length();

        String[] sub = new String[length];
        for (int i = 0; i < length; i++) {
            sub[i] = input.substring(i);
        }

        Arrays.sort(sub);
        for (String str : sub) {
            System.out.println(str);
        }
        br.close();
    }
}


```

