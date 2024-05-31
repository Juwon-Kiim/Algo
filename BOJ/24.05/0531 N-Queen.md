# BJ_G4_9663_N-Queen

https://www.acmicpc.net/problem/9663

<접근법>

```
완전탐색 알고리즘을 통해 문제 해결.
1. 1번째 행의 1번째 열부터 퀸을 놓는다
2. 2번째 행의 1번째 열부터 위, 왼쪽 대각 위, 오른쪽 대각 위에 퀸이 있는지 체크하고 없다면 퀸을 놓는다.
3. N개의 행에 N개의 퀸이 놓였다면 성공적으로 놓은 것이므로 count++해준다.
```

```java
import java.io.*;
import java.util.*;

public class Main {
    public static int N, count;
    public static int[][] board;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        N = Integer.parseInt(br.readLine());

        board = new int[N][N];

        nQueen(0);

        System.out.println(count);
    }
    public static void nQueen(int depth){
        if(depth==N){
            count++;
            return;
        }

        for(int i=0;i<N;i++){
            if(isPos(depth, i)){
                board[depth][i] = 1;
                nQueen(depth+1);
                board[depth][i] = 0;
            }
        }
    }

    public static boolean isPos(int r, int c){
        for(int i=0;i<r;i++){
            if(board[i][c]==1){
                return false;
            }
        }

        for(int i=1;i<=r;i++){
            if(r-i>=0&&c-i>=0&&board[r-i][c-i]==1){
                return false;
            }else if(r-i>=0&&c+i<N&&board[r-i][c+i]==1){
                return false;
            }
        }
        return true;
    }
}
```
