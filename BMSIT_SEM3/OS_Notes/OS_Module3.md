<!--markdownlint-disable MD025-->
# Questions

## Feb2023

1. question5
   1. what are the necessary conditions for dealock
   2. explain the different methods to recovery from deadlocks
   3. Banker's algorithm
2. question6
   1. what is paging hardware with tlb
   2. explain structure of page table with respect to hierarchial paging
   3. explain the process of segmentation

## Feb 2021

1. question5
   1. discuss briefly about semaphores in synchronization
   2. discuss in detail about deadlock characteristics
   3. discuss in detail about memory allocation with illustration
   4. discuss in detail about paging in a memory management scheme

## BMSIT Paper

1. Exlain critical section problem. analyse the requirements in which the critical section problem must satisfy. Explain peterson
2. Banker's algorithm
3. discuss briefly about semaphores in synchronization. Analyse how semaphores are used to solve producer consumer problem
4. Banker's algorithm

# Solutions

## ProducerConsumerProblem

- Semaphore is simply a variable which is non-negative shared between threads. used to solve the critical section problem ; synchronization in the multiprocessing

```algo
    P(Semaphore S){
        while(S<=0) // stuck in loop until S is greater than 0
            ;
        S--; // then decrements to indicate using the resource
    }

    V(Semaphore S){
        S++ ; // to indicate the resource is freed
    }
```

Types of Semaphores:

1. Binary (Mutex):
   1. val can range between 0 and 1
   2. called mutex as they provide mutual exclusion
2. Counting :
   1. range is unrestricted
   2. used to control access to a resource that has multiple instances

```C
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <semaphore.h>

#define BUFFER_SIZE 5

int buffer[BUFFER_SIZE];
int in = 0, out = 0;

sem_t empty;  // Tracks empty slots in the buffer
sem_t full;   // Tracks full slots in the buffer
pthread_mutex_t mutex;  // Ensures mutual exclusion

void *producer(void *param) {
    int item;
    while (1) {
        item = rand() % 100; // Produce an item

        sem_wait(&empty); // Wait for an empty slot
        pthread_mutex_lock(&mutex); // Enter critical section

        buffer[in] = item;
        printf("Produced: %d\n", item);
        in = (in + 1) % BUFFER_SIZE;

        pthread_mutex_unlock(&mutex); // Exit critical section
        sem_post(&full); // Increment the number of full slots
    }
}

void *consumer(void *param) {
    int item;
    while (1) {
        sem_wait(&full); // Wait for a full slot
        pthread_mutex_lock(&mutex); // Enter critical section

        item = buffer[out];
        printf("Consumed: %d\n", item);
        out = (out + 1) % BUFFER_SIZE;

        pthread_mutex_unlock(&mutex); // Exit critical section
        sem_post(&empty); // Increment the number of empty slots
    }
}

int main() {
    pthread_t prod_tid, cons_tid;

    // Initialize semaphores and mutex
    sem_init(&empty, 0, BUFFER_SIZE);
    sem_init(&full, 0, 0);
    pthread_mutex_init(&mutex, NULL);

    // Create producer and consumer threads
    pthread_create(&prod_tid, NULL, producer, NULL);
    pthread_create(&cons_tid, NULL, consumer, NULL);

    // Join threads (though in this infinite loop case, they won't actually join)
    pthread_join(prod_tid, NULL);
    pthread_join(cons_tid, NULL);

    // Destroy semaphores and mutex
    sem_destroy(&empty);
    sem_destroy(&full);
    pthread_mutex_destroy(&mutex);

    return 0;
}

```

## Critical Section Problem

- Critical section of a program is the part of the program that contains / deals with changing common variables, updating tables etc.
- that is, interruptions or sharing of execution cannot take place during the execution of critical section

Peterson's solution

1. `int turn`: indicates turn to enter critical section
2. `boolean flag[2]` : indicates intention to enter critical section

```algo
do{
    flag[i] = TRUE;
    turn=j;
    while(turn = j && flag[j]==TRUE); // wait
    <critical section> 
    flag[i] = FALSE;
    <remainder section>
}while(TRUE)
```

