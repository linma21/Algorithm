##  [💛 백준 3190 (뱀) 💛](https://www.acmicpc.net/problem/3190)


### 메모
```
사과가 놓여있는 위치와 움직임에 대한 정보(시간,방향)을 저장하자.
map에 있는 뱀의 위치는 선입선출인 queue를 활용하자. 그리고 한 이동마다 시간을 카운트해주고 그 카운트해준 시간이 Map의 Key에 존재하면 방향을 바꿔주자. 
    >  queue 사용 이유 : 새로운 칸으로 이동할 때마다 먼저 들어온 꼬리 칸 부분을 빼놔야 하기 때문이다. 
```

### 정리


### 내 답안
```java
public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 순서대로 상 우 하 좌
        int[] dirX = {-1, 0, 1, 0};
        int[] dirY = {0, 1, 0, -1};

        // dirX와 dirY 공용 인덱스 (처음 시작할 땐 오른쪽)
        int dirI = 1;
        int N = Integer.parseInt(br.readLine());
        int K = Integer.parseInt(br.readLine());

        int[][] map = new int[N + 1][N + 1];

        // 사과 위치
        for (int i = 0; i < K; i++) {
            StringTokenizer st = new StringTokenizer(br.readLine());

            int x = Integer.parseInt(st.nextToken());
            int y = Integer.parseInt(st.nextToken());

            map[x][y] = 1;
        }

        // 방향 변환
        int L = Integer.parseInt(br.readLine());

        // 방향 전환 정보
        Queue<Turn> turns = new LinkedList<>();
        for (int i = 0; i < L; i++) {
            StringTokenizer st = new StringTokenizer(br.readLine());

            int time = Integer.parseInt(st.nextToken());
            String direction = st.nextToken();

            turns.offer(new Turn(time, direction));
        }

        // 뱀의 위치를 저장하는 덱 (Deque)
        Deque<Position> snake = new LinkedList<>();
        snake.add(new Position(1, 1));

        // 게임 시간
        int time = 0;

        // 방향 전환 정보
        Turn nextTurn = turns.poll();
        
        while (true) {

            time++;

            // 현재 뱀의 머리 위치
            Position head = snake.peekFirst();
            int nextX = head.x + dirX[dirI];
            int nextY = head.y + dirY[dirI];

            // 벽에 닿으면 게임 오버
            if (nextX < 1 || nextX > N || nextY < 1 || nextY > N) {
                break;
            }
            // 자기 몸에 닿으면 게임 오버
            boolean collision = false;
            for (Position pos : snake) {
                if (pos.x == nextX && pos.y == nextY) {
                    collision = true;
                    break;
                }
            }
            if (collision) {
                break;
            }

            // 새로운 위치에 머리를 추가
            snake.addFirst(new Position(nextX, nextY));

            // 사과가 있으면 머리만 추가되고 꼬리는 그대로
            if (map[nextX][nextY] == 1) {
                map[nextX][nextY] = 0;
            } else {
                // 사과가 없으면 꼬리 삭제
                snake.removeLast();
            }

			// 방향 전환
            if (nextTurn != null && time == nextTurn.time) {
				// direction이 D면 index += 1, L이면 -= 1
                if (nextTurn.direction.equals("D")) {
                    dirI = (dirI + 1) % 4;
                } else if (nextTurn.direction.equals("L")) {
                    dirI = (dirI + 3) % 4;
                }
				nextTurn = turns.poll();
            }
        }

        System.out.println(time);
    }

}

class Turn {

    int time;
    String direction;

    Turn(int time, String direction) {
        this.time = time;
        this.direction = direction;
    }
}

class Position {

    int x, y;

    Position(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

```
