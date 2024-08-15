```java
package com.bmsit_programs.program5;


import java.lang.Math;
abstract class shape{
    public abstract double calculateArea();
    public abstract double calculatePerimeter();
}
class circle extends shape{
    public double radius = 5.0;
        @Override
    public double calculateArea() {
            return (Math.PI*radius*radius);
        }
        @Override
    public double calculatePerimeter(){
            return (2*Math.PI*radius);
        }
}

class triangle extends shape{

    double side1;
    double side2;
    double side3;
    double s ;


    public triangle(int a, int b, int c){
        this.side1 = a;
        this.side2 = b;
        this.side3 = c;
        this.s =  (side1+side2+side3)/2.0;
    }
    @Override
    public double calculateArea(){
        System.out.println(s+" "+side1+" "+side2+" "+side3);
        return Math.sqrt((s-side1)*(s-side2)*(s-side3)*s);
    }
    @Override
    public double calculatePerimeter(){
        return s*2;
    }
}
public class program5 {
    public static void main(String[] args){
        circle Circle = new circle();
        System.out.println(Circle.calculateArea()+" "+Circle.calculatePerimeter());

        triangle Tri = new triangle(3,4,5);
        System.out.println(Tri.calculateArea()+" "+ Tri.calculatePerimeter());
    }

}

```