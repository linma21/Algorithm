##  [🩶 백준 14729 (칠무해) 🩶](https://www.acmicpc.net/problem/14729)



### 메모


### 정리


### 내 답안 
1. <span style="background-color:#FFE6E6"> 메모리초과 </span>
```java

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        ArrayList<Double> scoreList = new ArrayList<>();

        for (int i = 0; i < N; i++) {
            double score = Double.parseDouble(br.readLine());
            scoreList.add(score);
        }

        Collections.sort(scoreList);

        for(int k = 0; k < 7; k++){
            System.out.println(scoreList.get(k));
        }

        br.close();
    }
}


```
2. `double` -> `int`

```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        int[] scoreList = new int[N];

        for (int i = 0; i < N; i++) {
            double score = Double.parseDouble(br.readLine()) * 1000;
            scoreList[i] = (int) score;
        }

        Arrays.sort(scoreList);

        for(int k = 0; k < 7; k++){
            System.out.printf("%.3f\n", scoreList[k] / 1000.0);
        }

        br.close();
    }
}

```