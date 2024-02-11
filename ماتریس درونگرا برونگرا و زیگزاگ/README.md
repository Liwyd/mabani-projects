# ماتریس درونگرا برونگرا و زیگزاگ
### توضیحات:
یک عدد دریافت کند و به طول آن یک ماتریس درنگرا / برونگرا / زیگزاگ چاپ کند.
#

### مثال درونگرا :
<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_23-24-14_xbsy.png" border="0"/></a>

## code:
#### درونگرا
```cpp
#include <iostream>
using namespace std;
int main()
{
    int n;
    cout << "Enter the size of the array :";
    cin >> n;
    int A[n][n], len = n, k = 1, p = 0, i;

    while (k <= n * n)
    {
        for (i = p; i < len; i++) // first row
            A[p][i] = k++;
        for (i = p + 1; i < len; i++) // last column
            A[i][len - 1] = k++;
        for (i = len - 2; i >= p; i--) // last row
            A[len - 1][i] = k++;
        for (i = len - 2; i > p; i--) // first column
            A[i][p] = k++;

        p++;
        len = len - 1;
    }
    for (i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
            cout << A[i][j] << "\t";
        cout << endl;
    }
    return 0;
}
```
#### برونگرا
```cpp
#include <iostream>
using namespace std;
int main()
{
    int n;
    cout << "Enter the size of the array :";
    cin >> n;
    int A[n][n], len = n, k = n * n, p = 0, i;

    while (k > 0)
    {
        for (i = p; i < len; i++) // first row
            A[p][i] = k--;
        for (i = p + 1; i < len; i++) // last column
            A[i][len - 1] = k--;
        for (i = len - 2; i >= p; i--) // last row
            A[len - 1][i] = k--;
        for (i = len - 2; i > p; i--) // first column
            A[i][p] = k--;

        p++;
        len = len - 1;
    }
    for (i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
            cout << A[i][j] << "\t";
        cout << endl;
    }
    return 0;
}

```
#### زیگزاگ
```cpp
E
```
