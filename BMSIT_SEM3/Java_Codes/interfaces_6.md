```java
package com.bmsit_programs_testing;

interface Resizeable{
    void resizeWidth(int new_width);
    void resizeHeight(int new_height);
}

class Rect implements Resizeable{
    public int height =0 ,width =0;
    public void resizeWidth(int new_width){
        width = new_width;
    }
    public void resizeHeight(int new_height){
        height = new_height;
    }
    void get_width_height(){
        System.out.println("Width: "+width+" Height: "+height);
    }

}


public class program6 {
    public static void main(String[] args){
        Rect rect = new Rect();
        rect.resizeHeight(10);
        rect.resizeWidth(20);
        rect.get_width_height();
    }
}

```
