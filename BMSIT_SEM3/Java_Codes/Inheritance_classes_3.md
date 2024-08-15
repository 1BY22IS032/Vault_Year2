```java
package com.bmsit_programs.program3;

class shape{
    public int state = 0;
    public void draw(){
        System.out.println("Shape has been drawn");
        state=1;
    }
    public void erase(){
        System.out.println("Shape has been deleted");
        state=0;
    }
}
class circle extends shape{
    void check(){
        if(state==0){
            draw();
        }
        else{
            erase();
        }
    }
}

class triangle extends shape{
    void check(){
        if(state==0){
            draw();
        }
        else{
            erase();
        }
    }
}

class square extends shape{
    void check(){
        if(state==0){
            draw();
        }
        else{
            erase();
        }
    }
}

public class program3 {
    public static void main(String[] args) {
        circle circle1 = new circle();
        circle1.state = 1;
        triangle triangle1 = new triangle();
        
        square square1 = new square();
    }
}

```
