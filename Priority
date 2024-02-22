#include <string.h>
#include <stdlib.h>
#include <stdio.h>
#define MAXIMUM 2000

//create a structure that will contain our task name, priority and CPU burst
typedef struct Hold {
char name[MAXIMUM];
int priority;
int burst;
}
Hold;

//this program should use a linked list, so we must create a structure that represents the node of a linked list
typedef struct LL {
Hold n;
struct LL* linked;
}
LL;

//now we must declare our functions as well as the parameters of those functions
void Priority(LL** front, Hold n);
void order(LL* front);

//now we do our main function which will allow any file to be input
int main(int count, char *inputFile[]) {

//open our given file to read "r" the file (in this case, it's schedule.txt) using [1] to get our file which comes after the name of our file
FILE *input = fopen(inputFile[1], "r");

//we must also error check and make sure that our file was actually opened
if (input == NULL) {
printf("Issue with opening file.\n");
return 1;
}

//here we initilaize the front of our linked list to NULL so it is initially empty
LL* front = NULL;

//we must also allocate memory for array
char array[MAXIMUM];

//now we begin reading from our input file
//as long as fgets() keeps reading, we keep looping
//also, fgets() has 3 parameters, our array, the maximum number of characters, and our input
while (fgets(array, MAXIMUM, input) != NULL) {
//place data from our input file into our hold structure via sscanf
Hold n;
sscanf(array, "%[^,], %d, %d", n.name, &n.priority, &n.burst);
//and now we add to our linkd list via the Priority function call that includes two parameters, address of pointer to front of linkd list and n task
Priority(&front, n);
}

//now, we will display the order via a function call to the order function. This function has one parameterr representing the pointer to the front of our linked list
order(front);

//finally, we close our file when finished
fclose(input);

return 0;

}
//end main


//**************** below are our functions *******************


//first is our Priority function which sorts by CPU burst
void Priority(LL** front, Hold n) {
//allocate memory using malloc
LL* sequence = malloc(sizeof(LL));
//set newest node link to null
sequence->linked = NULL;
//assign task info
sequence->n = n;

//traverse list
LL* now = *front;
//keep traversing until we locate insertion point based on priority
//compare priorities
while(now && now->n.priority > n.priority) {
//update front
front = &(now->linked);
//continue to next node
now = now->linked;
}

//insert and update
sequence->linked = now;
*front = sequence;
}


//now we do our order function
void order(LL* front) {
while (front != NULL) {
printf("Running Task = [%s] [%d] [%d] for %d units. \n", front->n.name, front->n.priority, front->n.burst, front->n.burst);
//update
front = front->linked;
}
}

