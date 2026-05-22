#include <stdio.h>
#include <stdlib.h>

#define MAX 5


int queue[MAX];
int front = -1;
int rear = -1;

//-----------------------global methord declar--------------------


void enqueue();
void dequeue();
void display();




int main() {
    int choice;


    while (1) {
        printf("\nChoose an option:\n");
        printf("(1) Enqueue\n");
        printf("(2) Dequeue\n");
        printf("(3) Display\n");
        printf("(4) Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                enqueue();
                break;
            case 2:
                dequeue();
                break;
            case 3:
                display();
                break;
            case 4:
                printf("Thank you.\n");
                exit(0);
            default:
                printf("Invalid option. Please try again.\n");
        }
    }
    return 0;
}


//-----------------insert value--------------------------------------



void enqueue() {
    int num;
    printf("Enter a number to enqueue: ");   //input value with user,
    scanf("%d", &num);

    if (rear == MAX - 1) {
        printf("Queue is full\n");
        return;
    }
    else if(front == -1 && rear == -1)
		front = rear = 0;
	else
		rear++;

	queue[rear] = num;
    display();
}

//----------------------delete value in queue------------------------


void dequeue() {

   if (rear == -1) {
        printf("Queue is empty\n");
        return;
    }

    int val = queue[0];
    printf("Dequeued element: %d\n", val);

    for (int i = 0; i < rear; i++) {         //index swap one by one,and rear -1,
        queue[i] = queue[i + 1];
    }

    rear--;
    display();
}



//-------------------------------show queue inserted value----------------------------


void display() {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }

    for (int i = 0; i <= rear; i++) {
        printf("%d ", queue[i]);
    }

}
