```C
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>

#define BUFFER_SIZE 20

sem_t empty, full;
int buffer[BUFFER_SIZE];
int in = 0;
int out = 0;
int size = 50;

void* producer(void* arg) {
    int item = 1; // defining item
    while (1) { //infina loop
        sem_wait(&empty);  //wait till empty 
        buffer[in] = item++; // set item value and then increment 
        printf("Produced: %d\n", buffer[in]); //print out satement 
        in = (in + 1) % BUFFER_SIZE; // circular increment 'in'
        sem_post(&full); // post message full
        if (item > size) break; // break loop if size limit reached
    }
    printf("Sending completed\n ");f
    pthread_exit(NULL); // exiting
}

void* consumer(void* arg) {
    int item; // declare item;
    while (1) { // infina looop
        sem_wait(&full);  // wait till full
        item = buffer[out]; // set item to buffer[out]
        printf("Consumed: %d\n", item); // print statement 
        out = (out + 1) % BUFFER_SIZE;// circular increment 
        sem_post(&empty); //post message
        if (item == size) { //break loop
            printf("Received all\n");
            break;
        }
    }
    pthread_exit(NULL); // exiting
}

int main() {
    pthread_t producer_thread, consumer_thread; // create variables
    sem_init(&empty, 0, BUFFER_SIZE); // initialize semaphores (pointer,this thread,value)
    sem_init(&full, 0, 0); // same applies to this
    pthread_create(&producer_thread, NULL, producer, NULL); // 
    pthread_create(&consumer_thread, NULL, consumer, NULL);
    pthread_join(producer_thread, NULL);
    pthread_join(consumer_thread, NULL);
    sem_destroy(&empty);
    sem_destroy(&full);
    return 0;
}

```