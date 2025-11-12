
***************************************************************************************************************************************************************
<h1> Find The Way</h1>

You are given a binary matrix of dimensions m*n. A mouse enters the matrix at cell (0,0) in left to right direction.

He goes in the same direction if he encounters a 0 and he takes a right turn when he encounters a 1, and changes that specific 1 to 0. Otherwise he may get stuck in a cycle!

You have to find the co-ordinates from where this mouse will exit the matrix.

Input Format
First line contains the values m and n.

Next m lines contain n spaced integers.

Output Format
Return the co-ordinates from where this mouse will exit the matrix separated by space.

Example 1
Input

1 2
0 0
Output

0 1
Explanation

The mouse will enter at (0,0) and keep going ahead and come out of (0,1).

Example 2
Input

3 3
0 1 0
0 1 0
1 0 1
Output

1 0


***************************************************************************************************************************************************************
```java____
import java.util.*;

public class Main {
    public static int[] findTheWay(int[][] matrix) {
        int row = matrix.length;
        int col = matrix[0].length;
        int i =0,j=0;
        int dir =0;

        while(true){

            dir = (dir+matrix[i][j])%4;

            if(dir ==0){
                j++;

            }else if(dir==1){
                i++;
            }else if (dir ==2){
                j--;
            
            }else if (dir==3){
                i--;
            }

            if(i<0){
                i++;
                break;
            }
            if(j<0){
                j++;
            break;
            }
            if(i==row){
                i--;
                break;
            }
            if(j==col){
                j--;
                break;
            }

        }
       
        int[] res = new int[]{i,j};//last coordinate
        return res;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int m, n;
        m = sc.nextInt();
        n = sc.nextInt();
        int[][] matrix = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++)
                matrix[i][j] = sc.nextInt();
		}
        int result[] = findTheWay(matrix);
        for (int i = 0; i < result.length; i++) {
            System.out.print(result[i] + " ");
        }
        System.out.println();
        sc.close();
    }
}
