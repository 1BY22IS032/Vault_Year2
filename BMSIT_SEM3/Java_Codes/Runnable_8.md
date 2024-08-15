```java
package com.bmsit_programs.program8;

class myThreads implements Runnable{
    @Override
    public void run(){
        try{
            System.out.println(Thread.currentThread().getName()+" has started running");
            Thread.sleep(500);
        }
        catch (InterruptedException e){
            System.out.println(Thread.currentThread().getName()+" Has been interrupted");
        }
    }
}
public class program8 {
    public static void main(String[] args){
        Thread thread1 = new Thread(new myThreads(),"thread1");
        Thread thread2 = new Thread(new myThreads(),"thread2");
        Thread thread3 = new Thread(new myThreads(),"thread3");

        thread1.start();
        thread2.start();
        thread3.start();
    }
}

```
