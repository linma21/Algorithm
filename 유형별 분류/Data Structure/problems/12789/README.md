##  [🩶 백준 12789 (도키도키 간식드리미) 🩶](https://www.acmicpc.net/problem/12789)


### 메모
```
```

### 정리


### 내 답안
```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int N = Integer.parseInt(br.readLine());

        // 기존 대기줄
        Queue<Integer> oldWait =  new LinkedList<>();

        // 추가 대기줄
        Stack<Integer> newWait = new Stack<>();

        StringTokenizer st = new StringTokenizer(br.readLine());

        for (int i = 0; i < N; i++) {
            oldWait.offer(Integer.parseInt(st.nextToken()));
        }

        // 현재 순서
        int num = 1;

        while (!oldWait.isEmpty()) { 
            
            if(oldWait.peek() == num){
                // 기존 대기줄 맨앞이 간식을 받을 차례면
                oldWait.poll();
                num++;
            }else if(!newWait.isEmpty() && newWait.peek() == num) {
                // 추가 대기줄 맨뒤가 간식을 받을 차례면
                newWait.pop();
                num++;
            }else{
                // 둘 다 아니면 추가 대기줄에 보내기
                newWait.push(oldWait.poll());
            }
        }
        while(!newWait.isEmpty()) {

            if(newWait.peek() == num) {
                newWait.pop();
                num++;
            }else {
                break;
            }

        }
        System.out.println((num > N && newWait.isEmpty()) ? "Nice" : "Sad");
    }
}


```
