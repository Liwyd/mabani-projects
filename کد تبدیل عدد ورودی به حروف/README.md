# کد تبدیل عدد ورودی به حروف
### توضیحات:
برنامه ای بنویسید که یک عدد حداکثر ۱۲ رقمی از ورودی دریافت و آنا به حروف و به صورت فینگلیش چاپ کند 
#


<a href="https://uupload.ir/" target="_blank"><img src="https://s8.uupload.ir/files/image_2024-02-11_21-35-58_gzff.png" border="0" /></a>

## code:

```cpp
#include <iostream>
#include <cmath>
using namespace std;

void Quarter(int, int, int);
void valueDefiner(long long int);

int main()
{
    long long num;
    bool os = 0; // windows=1 & other=0
#ifdef _WIN32
    os = 1;
#elif _WIN64
    os = 1;
#else
    os = 0;
#endif
    (os == 0) ? system("clear") : system("cls");

    while (true)
    {
        string number;
        cout << "[$] Enter a number: ";
        getline(cin, number);
        bool flag = 0;
        for (char c : number)
        {
            if ((c < '0' || c > '9') && (c != '-'))
            {
                cout << "[!]: Enter only Numbers!\n\n";
                flag = 1;
                break;
            }
        }
        if (flag)
            continue;

        try
        {
            num = stoi(number);
        }
        catch (const exception &e)
        {
            cout << "[!]: OUT OF RANGE!" << endl;
            flag = 1;
        }

        if (flag)
            continue;

        cout << "[fa]: ";
        valueDefiner(num);
        cout << " .\n\n";
    }
    return 0;
}

void Quarter(int a1, int a2, int a3)
{
    const string Ones[20] = {
        "",
        "yek",
        "do",
        "se",
        "chahar",
        "panj",
        "shish",
        "haft",
        "hasht",
        "noh",
        "dah",
        "yaazDah",
        "davazDah",
        "sizDah",
        "chaharDah",
        "panezDah",
        "shonzDah",
        "hefDah",
        "hejDah",
        "noozDah",
    };
    const string Tens[10] = {
        "",
        "dah",
        "bist",
        "si",
        "chehel",
        "panjah",
        "shast",
        "haftad",
        "hashtad",
        "navad",
    };
    const string Hundreds[10] = {
        "",
        "sad",
        "divist",
        "sisad",
        "chaharSad",
        "ponsad",
        "shishsad",
        "haftsad",
        "hashtsad",
        "nohSad",
    };
    const string sep = " o "; // seperator " و "
    if (a1 != 0 && a2 != 0)
    {
        cout << Hundreds[a1] << sep;
    }
    else if (a1 != 0 && a2 == 0)
    {
        cout << Hundreds[a1];
    }
    if (a2 == 1 && a3 != 0)
        cout << Ones[((a2 * 10) + a3)];
    else if (a2)
    {
        if (a3 == 0)
            cout << Tens[a2];
        else
            cout << Tens[a2] << sep << Ones[a3];
    }
    else
    {
        cout << Ones[a3];
    }
}
void valueDefiner(long long int num)
{
    int value = 0;
    const string Big[4] = {
        "",
        " hezar",
        " milion",
        " miliyard",
    };

    if (num == 0)
    {
        cout << "sefr";
        return;
    }
    if (num < 0)
    {
        cout << "manfie ";
        num = -num;
    }
    if (num >= 1000 && num < 1000000)
        value = 1;
    if (num >= 1000000 && num < 1000000000)
        value = 2;
    if (num >= 1000000000)
        value = 3;

    for (int counter = value; counter >= 0; counter--)
    {
        long long int tavan = pow(10, 3 * counter);
        int threeDigits, nextThreeDigits;
        // TESTCASE cout << "Test: " << num/(tavan*1000)<< " | tavan: "<< tavan << endl;
        if (num / (tavan * 1000) != 0)
        {
            threeDigits = (num / (tavan) - (num / (tavan * 1000) * 1000));
        }
        else
        {
            threeDigits = (num / (tavan));
        }

        // TESTCASE cout << threeDigits/100 << " | " << (threeDigits/10-((threeDigits/100)*10)) << " | " << threeDigits%10 << endl;
        Quarter(threeDigits / 100, (threeDigits / 10 - ((threeDigits / 100) * 10)), threeDigits % 10);
        if (threeDigits != 0 && counter != 0)
        {
            nextThreeDigits = (num / (tavan / 1000) - (num / (tavan) * 1000));
            if (nextThreeDigits != 0)
                cout << Big[counter] << " o ";
            else
                cout << Big[counter];
        }
    }
}
```
