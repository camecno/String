```
#include <iostream>
using namespace std;
class Mystring
{
private:
    char* mdata;
    size_t msize;
public:
    Mystring(const char* sizeString) { // конструктор
        msize = 0;
        while (sizeString[msize] != '\0') {
            ++msize;
        }
        mdata = new char[msize + 1]; // выделяем память для массива символов
        for (size_t i = 0; i <= msize; ++i) { // копируем символы строки
            mdata[i] = sizeString[i];
        }
    }

    ~Mystring() { //деструктор
        delete[] mdata;
    }

    size_t size() const {
        return msize;
    }
    size_t find(const char* substr) const {
        size_t substrLen = 0;
        while (substr[substrLen] != '\0') {
            ++substrLen;
        }
        for (size_t i = 0; i <= msize - substrLen; ++i) {
            size_t j = 0;
            while (j < substrLen && mdata[i + j] == substr[j]) {
                ++j;
            }
            if (j == substrLen) {
                return i; // подстройкв найдена, возвращение
            }
        }
        return static_cast<size_t>(-1); // Подстрока не найдена(переобразование)
    }

};

int main()
{
    {
        Mystring sizeString("Prietsuhjo   asd fhuoihsdf");
        cout << "size of string  " << endl << sizeString.size() << endl;
        const char* substr = "ive d d"; // Определяем подстроку которую мы ищем
        size_t foundPos = sizeString.find(substr);
        if (foundPos != size_t(-1)) {
            cout << "podstroka naydena na pozicii: " << foundPos << endl;
        }
        else {
            cout << "podstroka ne naydena" << endl;
        }

    }
}

```
