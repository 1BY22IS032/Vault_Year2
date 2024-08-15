```java
package com.bmsit_programs.program1;
import java.util.Scanner;
public class program1 {
    public program1(int n){
       Scanner sc = new Scanner(System.in);

       System.out.println("Enter the Row count of the Matrices");
        int Row = sc.nextInt();
        System.out.println("Enter the Column count of the Matrices");
        int Col = sc.nextInt();

        int[][] A = new int[Row][Col];
        int[][] B = new int[Row][Col];
        int[][] Result = new int[Row][Col];

        System.out.println("Enter the values of A");
        for(int i=0;i<Row;i++){
            for(int j=0;j<Col;j++){
                A[i][j] = sc.nextInt();
            }
        }

        System.out.println("Now Enter the values of B");
        for(int i=0;i<Row;i++){
            for(int j=0;j<Col;j++){
                B[i][j]= sc.nextInt();
            }
        }

        for(int i=0;i<Row;i++){
            for(int j=0;j<Col;j++){
                Result[i][j] = A[i][j] + B[i][j];
            }
        }

        for(int i=0;i<Row;i++){
            for(int j=0;j<Col;j++){
                System.out.print(Result[i][j] + " ");
            }
            System.out.println();
        }

    }
}


```