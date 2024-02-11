# ماتریس x شکل
### توضیحات:
خودمم نمیدونم از کجا اومده ولی اگه دقت کنید یه الگوی خاصی توی هر سطر و ستون و قطر هست و اینکه شیوه حلش اینجوریه که 

<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_23-28-13_vihv.png" border="0" /></a>

هر بخش رو با یک حلقه چاپ میکنه 
# نتیجه :
<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_23-30-05_q26.png" border="0" /></a>

## code:
```cpp
#include <iostream>
using namespace std;

int main()
{
    char ch;
    cin >> ch;

    int w = ch - 'A'; // D
    char h = 'A', k = 'B', g = 'B', j = 'B', ch1 = ch;
    int dor = 2 * w + 1, rou = w + 1;
    while (dor != -1)
    {
        if (dor <= 2 * w)
        {
            for (char s = g; s >= k; s--)
                cout << s;
            g++;
        }

        for (char c = h; c <= ch; c++)
            cout << c;
        for (char x = ch - 1; x >= h; x--)
            cout << x;
        ch--;
        if (dor <= 2 * w)
        {
            for (char o = 'B'; o <= j; o++)
                cout << o;
            j++;
        }

        cout << endl;
        dor--;
        if (dor == rou - 1)
            break;
    }
    int maindor = w;
    char g1 = ch1 - 1, h1 = 'A', ch2 = 'B', k1 = 'B', j1 = ch1 - 1;
    while (maindor > 0)
    {
        for (char s1 = g1; s1 >= k1; s1--)
            cout << s1;
        g1--;
        for (char c1 = 'A'; c1 <= ch2; c1++)
            cout << c1;
        for (char x1 = h1; x1 >= 'A'; x1--)
            cout << x1;
        h1++;
        ch2++;
        for (char o1 = 'B'; o1 <= j1; o1++)
            cout << o1;
        j1--;
        cout << endl;
        maindor--;
    }
}
```
