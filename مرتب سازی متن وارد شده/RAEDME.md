# مرتب سازی متن وارد شده
### توضیحات:
یک متن دریافت کند فاصله های اضافی را پاک کند و وسط چین کند و ... خودتون  کد رو بخونید زیاده کاراش 
#


<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_23-14-12_ilbp.png" border="0" /></a>


## code:
```cpp
#include<iostream>
#include<stdio.h>
#include<conio.h>
using namespace std;

void justifyLine(char *text, int charPerLine, int margin, int startIndex, int endIndex, int spaceCount){
    int addingSpaces= charPerLine - (endIndex - startIndex);
    int addedSpaces= 0;
    bool onWord= false;
    if(text[startIndex] == ' '){
        addingSpaces++;
        startIndex++;
    }
    cout<< "  |";
    for(int i= 0; i < margin; i++) cout<< " ";
    for(int i=startIndex ; i < endIndex && text[i]; i++){
        if(text[i] != ' '){
            onWord= true;
        } else if(onWord){
            addedSpaces+= addingSpaces;
            for(int j=0; j < addedSpaces/spaceCount; j++) cout<< " ";
            addedSpaces%= spaceCount;
        }
        cout<< text[i];
    }
    for(int i= 0; i < margin; i++) cout<< " ";
    cout<< "|" << endl;
}

void justifyText(char *text, int size, int charPerLine, int margin){
    int wordCount= 0;
    int charCount= 0;
    bool onWord= false;
    int lastWordIndex= 0, lastWordEndIndex= 0;
    int firstWordIndex= 0;

    for(int i=0; text[i]; i++){
        if(text[i] != ' '){
            if(!onWord) lastWordIndex= i;
            onWord= true;
        }
        if(text[i+1] == ' ' && onWord){
            lastWordEndIndex= i;
            wordCount++;
            onWord= false;
        }
        charCount++;
        
        if(charCount >= charPerLine){
            justifyLine(text, charPerLine, margin, firstWordIndex, lastWordEndIndex+1, wordCount-1);
            firstWordIndex= lastWordEndIndex+1;
            i= firstWordIndex;
            charCount= 0;
            wordCount= 0;
            onWord= false;
        }
    }
    if(charCount != 0){
        justifyLine(text, charPerLine, margin, firstWordIndex, firstWordIndex + charCount+1, wordCount);
    }
}

int main(){
    char text[1024];
    char input;
    int inputIndex=0;

    cout<< "Enter the text to justify: ";
    gets(text);
    cout<< endl;
    justifyText(text, 1024, 40, 10);
    cout<< endl;

    return 0;
}
```
