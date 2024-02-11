# جایگشت قرار گیری
### توضیحات:
برنامه ای بنویسید که باتوجه به فرمول n = bk مقادیر K(تعداد اتاق های یکو هتل) و b (ظرفیت افراد داخل هر اتاق) را دریافت کرده و حرف الفیای لنگلیسی را به عنوان افراد در تاق های مختلف قرار داده و تمام حالات را محاسبه کند.
#


<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_22-02-56_8u67.png" border="0"/></a>

## code:
 برای درک بهتر از کامنت های گذاشته شده استفاده کنید
```cpp
#include<iostream>
using namespace std;


//------------ Stack ---------------------
const int stackSize= 128;
int stackPointer= 0;
char stack[stackSize];

char pop(){
    if(stackPointer == 0) return 0;
    return stack[--stackPointer];
}
void push(char item){
    if(stackPointer == stackSize) return;
    stack[stackPointer++] = item;
}
//----------------------------------------

// stats
int num= 0;
// declaration
void printPartition(int k, int b, char chars[]);

void printCombinationForPartition(int n, int r, char chars[], int start, int k, int b){

    if(r == 0){ // when r=0, one of combinations is pushed to stack
        // separate remaining elements to pass to next partition
        char *toPartition= (char*) malloc(sizeof(char) * (k-1)*b);
        int appendingIndex= 0;
        bool inStack= false;
        for(int i=0; i < k*b - 1; i++){
            inStack= false;
            for(int j= stackPointer - b; j < stackPointer && !inStack; j++) inStack= chars[i] == stack[j];
            if(!inStack) toPartition[appendingIndex++]= chars[i];
        }
        // when k=1, the last set of current partition is pushed to stack. print the stack
        if(k == 1){
            for(int i= 0; i < stackPointer; i++){
                cout<< stack[i];
                if(i % b == (b-1) && i != stackPointer-1) cout<< ",";
            }
        }
        // start processing next set of the partition, using the remaining elements
        printPartition(k-1, b, toPartition);
        // deallocate the array of remaining elements
        free(toPartition);
    } else { // when r != 0, combinations is not complete yet
        // somehow this works...
        // it's hard to explain  :)
        for(int i=0; i < n-r+1; i++){
            push(chars[start+i]);
            printCombinationForPartition(n-i-1, r-1, chars, start+i+1, k, b);
            pop();
        }
    }
}

void printPartition(int k, int b, char chars[]){
    if(k == 0){ // when k=0, partition is pushed and printed.
        // insert new line and count up num variable.
        cout<< endl;
        num++;
        // exit the function, ending the chain of recursion
        return;
    }
    if(b == 1){ // special case of b=1
        // print every element and count.
        for(int i=0; i < k; i++){
            cout<< chars[i];
            if(i != k-1) cout<< ",";
        }
        cout<< endl;
        num++;
        return;
    }
    // separate first element from rest
    char *rest= (char*) malloc(sizeof(char) * (b-1));
    for(int i=0; i < k*b - 1; i++) rest[i]= chars[i+1];
    // push the first element and process every combination of other elements
    push(chars[0]);
    printCombinationForPartition(b*k-1, b-1, rest, 0, k, b);
    pop();
    // deallocate that array
    free(rest);
}

int main(){
    // variables
    char chars[]= "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"; // characters to use
    int k, b;
    // ui
    cout << "Please enter number of partitions (rooms / k) : ";
    cin >> k;
    cout << "Please enter number of elements in each partition (students per room / b) : ";
    cin >> b;
    if(k*b > 52){
        cout<< "too many!";
        return 0;
    }
    // do the thing
    printPartition(k, b, chars);
    // print stats
    cout<< "\n\n" << num << " combinations overall!\n\n";

    return 0;
}
```
