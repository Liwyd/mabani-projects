# Gray Code
### توضیحات:
برنامه ای بنویسید که یک مبنا دریافت کرده و سپس یک عدد را به عنوان تعداد ارقام دلخواه دریافت کند سپس تمام اعداد با آن طول ارقام را چاپ کند به ترتیبی که از شیوه grayCode پیروی کند.

درواقع gray code هست ولی نیست :))
#




<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_22-44-36_v8wv.png" border="0" /></a>

## code:
```cpp
#include<iostream>
#include<math.h>

using namespace std;

//------------ Stack ---------------------
const int stackSize= 128;
int stackPointer= 0;
int stack[stackSize];

int pop(){
    if(stackPointer == 0) return 0;
    return stack[--stackPointer];
}
void push(int item){
    if(stackPointer == stackSize) return;
    stack[stackPointer++] = item;
}
//----------------------------------------


void printGray(int base, int digits, int slope){
    if(digits == 0){
        for(int i= 0; i < stackPointer; i++) cout<< stack[i];
        cout<< endl;
        return;
    }
    int end= (slope == 1)? base : -1;
    int nextSlope= (base%2 == 0)? 1 : slope;
    for(int i= (slope == 1)? 0 : base-1; i != end; i+= slope){
        push(i);
        printGray(base, digits-1, nextSlope);
        pop();
        nextSlope= -nextSlope;
    }
}

int main(){

    int base, digits;
    cout<< "Please enter base: ";
    cin>> base;
    cout<< "Please enter digits: ";
    cin>> digits;
    
    printGray(base, digits, 1);

    return 0;
}
```
