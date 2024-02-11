# چاپ روبیک سه بعدی
### توضیحات:

 ابعاد یک ماتریس n*n رو دریافت کنه و اونرو با مقادیر دو رقمی رندوم پر کنه و از جهات بالا و روبرو و راست لایه به لایه 
اونرو چاپ کنه

#
<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_23-42-36_nwf2.png" border="0" /></a>


## code:
```cpp
#include <iostream>
#include <cmath>
#include <cstdlib>
#include <time.h>
using namespace std;

int main()
{
    int n, i, j, k;
    cin >> n;
    int arr[n][n][n];
    srand(time(0));
    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            for (k = 0; k < n; k++)
                arr[i][j][k] = rand() % 100;
    for (i = 0; i < n; i++)
    {
        for (j = 0; j < n; j++)
        {
            cout << "[";
            for (k = 0; k < n; k++)
                cout << arr[i][j][k] << " ";
            cout << "] ";
        }
        cout << "\n";
    }

    // FROM up
    cout << "\nFROM upLooking:\n";
    int temp[n][n];
    for (int layer = (n - 1); layer >= 0; layer--)
    {
        cout << "layer number " << layer << "\n";
        for (i = 0; i < n; i++)
            for (j = 0; j < n; j++)
                temp[i][j] = arr[i][j][layer];

        for (i = 0; i < n; i++)
        {
            for (j = 0; j < n; j++)
                cout << temp[i][j] << " ";
            cout << "\n";
        }
        cout << "\n";
    }

    // FROM front
    cout << "\nFROM frontLooking:\n";
    for (int layer = (n - 1); layer >= 0; layer--)
    {
        cout << "layer number " << layer << "\n";
        for (i = 0; i < n; i++)
            for (j = 0; j < n; j++)
                temp[i][j] = arr[layer][i][j];

        for (i = 0; i < n; i++)
        {
            for (j = 0; j < n; j++)
                cout << temp[i][j] << " ";
            cout << "\n";
        }
        cout << "\n";
    }

    // FROM RightSide
    cout << "\nFROM RightSide:\n";
    for (int layer = (n - 1); layer >= 0; layer--)
    {
        cout << "layer number " << layer << "\n";
        for (i = 0; i < n; i++)
            for (j = 0; j < n; j++)
            {
                
                temp[i][j] = arr[i][layer][j];
            }

        for (i = 0; i < n; i++)
        {
            for (j = 0; j < n; j++)
                cout << temp[i][j] << " ";
            cout << "\n";
        }
        cout << "\n";
    }

    return 0;
}
```
