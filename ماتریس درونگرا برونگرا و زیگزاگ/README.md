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
#include <iostream>
#include <iomanip>
#include <conio.h>
using namespace std;
int main(){
	int **s,n;
	cout<<"Please enter a number: ";
	cin>>n;
	s= new int*[n];
	for(int i=0;i<n;i++){
		s[i]=new int[n];
	}
	for(int i=0;i<n;i++){
		for(int j=0;j<n;j++)
		s[i][j]=0;
	}
	int i=1,r=0,c=0;
    s[r][c]=1;
    i++;
    while(i<=n*n){
	if(c+1<n)
	c++;
	else
		r++;
	s[r][c]=i;
	i++;
	if(i>n*n)
		break;
	while(r<n-1 && c>0){
		r++;
		c--;
		s[r][c]=i;
		i++;
		if(i>n*n)
	break;}
    if(r+1<n)
		r++;
	else
		c++;
	s[r][c]=i;
	i++;
	if(i>n*n)
		break;
	while(r>0 && c<n-1){
		r--;
		c++;
		s[r][c]=i;
		i++;
		if(i>n*n)
	break;}
   }
    for(r=0;r<n;r++){
	    for(c=0;c<n;c++)
		cout<<setw(3)<<s[r][c];
        cout<<"\n";}
    getch();
return 0;
}
```
