# CTDL-GT_Queue_2.cpp
Queue
Nguon tham khao : https://laptrinhtudau.com/cai-dat-hang-doi-queue-bang-mang-c-c/
Vi du : Ve hang doi QUEUE trong mang

#include <stdio.h>
#define MAX 100
typedef struct queue
{
    int A[MAX];
    int front, rear;
};
typedef struct queue QUEUE;
void Init(QUEUE &q){
    //gan front bang 0
    q.front = 0;
    //gan rear bang -1
    q.rear = -1;
}
int IsEmpty(QUEUE q){
    //neu front > rear thi hang doi rong va tra ve 1
    if (q.front > q.rear){
        return 1;
    }
    //nguoc lai khong rong thi tra ve 0
    return 0;
}
int IsFull (QUEUE q){
    //neu rear == MAX - 1 thi hang doi day va tra ve 1
    if (q.rear==MAX-1){
        return 1;
    }
    //nguoc lai hang doi chua day
    return 0;
}
void Add (QUEUE &q, int x){
    //Neu queue chua day
    if (IsFull(q)==0) {
        //tang chi so rear len 1 don vi
        q.rear++;
        //them phan tu x vao cuoi hang doi
        q.A[q.rear] = x;
    }
}
int Remove(QUEUE &q){
    int x;
    //neu hang doi khong rong
    if (!IsEmpty(q)) {
        //gan x bang phan tu dau tien cua hang doi
        x = q.A[q.front];
        //tang bien front len 1 don vi 
        q.front++;
        //tra ve phan tu lay duoc
        return x;
    }
    else{//nguoc lai hang doi rong
        q.front = 0; q.rear = -1;
    }
}
void Input(QUEUE &q, int n){
    //duyet tu 0 den n
    for(int i = 0; i< n; i++){
        //thuc hien nhap gia tri vao bien x
        int x;
        printf("Nhap gia tri phan tu thu %d: ",i);
        scanf("%d",&x);
        //thuc hien add phan tu x vao queue
        Add(q,x);
    }
}
void Output(QUEUE q){
    //duyet tu phan tu dau ve phan tu cuoi queue
    for(int i = q.front; i <= q.rear; i++){
        //hien thi ra ket qua
        printf("%d \t",q.A[i]);
    }
}
