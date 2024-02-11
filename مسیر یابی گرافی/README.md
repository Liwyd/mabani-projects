# مسیر یابی گرافی
### توضیحات:
برنامه ای بنویسد یک عدد را به عنوان n دریافت کند سپس یک ماتریس با ابعاد n*n که تمام مقادیر آن به صورت bool هستند را دریافت کند مه همان نشاندهنده وجود راه بین دو شهر هستند 

سپس تمام راه های موجود میان شهر ورودی مبدا و مقضد را چاپ کند.
#


<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_22-52-34_h0op.png" border="0" /></a>


## code:
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


void getRoads(int *roads, int n){
    int index;
    int connection;
    cout<< "Please enter 0 or 1\n";
    for(int i=0; i < n; i++){
        cout<< "Ways from point " << (char) (i+'A') << " to:\n";
        for(int j=0; j < n; j++){
            index= i*n + j;
            cout<< "   point " << (char) (j+'A') << ": ";
            connection= 0;
            if(i == j) cout<< 0 << endl;
            else cin>> connection;
            roads[index]= connection;
        }
    }
}
void showRoads(int *roads, int n){
    cout<< "  ";
    for(int i=0; i < n; i++){
        cout<< (char) (i+'A') << " ";
    }
    cout<< endl;
    for(int i= 0; i < n; i++){
        cout<< (char) (i+'A') << " ";
        for(int j=0; j < n; j++){
            cout<< roads[i*n + j];
            if(j == n-1) cout<< endl;
            else cout<< " ";
        }
    }
}
void findPaths(int *roads, int n, int start, int destination){
    int roadIndex;
    
    if(start == destination){
        for(int i=0; i < stackPointer; i++) cout<< (char) (stack[i]+'A') << " -> ";
        cout<< (char) (start+'A') << endl;
        return;
    }

    for(int i=0; i < n; i++){
        roadIndex= start*n + i;
        if(roads[roadIndex] == 0) continue;
        roads[roadIndex]= 0;
        push(start);
        findPaths(roads, n, i, destination);
        pop();
        roads[roadIndex]= 1;
    }
}


int main(){
    int n;
    char inp;
    int start;
    int end;
    cout<< "Please enter n: ";
    cin>> n;
    int *roads= (int*) malloc(sizeof(int) * n * n);

    getRoads(roads, n);
    cout<< endl;
    cout<< "basic map:\n\n";
    showRoads(roads, n);
    cout<< endl;
    cout<< "Please enter starting point (upper-case): ";
    cin>> inp;
    start= inp - 'A';
    cout<< "Please enter destination point (upper-case): ";
    cin>> inp;
    end= inp - 'A';
    cout<< "\nFinding paths from " << (char) (start+'A') << " to " << inp << "...\n\n\n";
    findPaths(roads, n, start, end);
    
    return 0;
}
```
