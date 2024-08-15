```java
package com.bmsit_programs.program7;

class DivBy0 extends Exception{
    public DivBy0(String message){
        super(message);
    }
}

public class program7 {
    public static void main(String[] args){
        try{
            int divisor = 0;
            int dividend = 10;
            if(divisor ==0){
                throw new DivBy0("Division by 0 is not possible");
            }
        }
        catch (DivBy0 e){
            System.out.println(e.getMessage());
        }
        finally {
            System.out.println("Execution Complete");
        }
    }
}
```