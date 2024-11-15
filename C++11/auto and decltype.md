Auto and Decltype
-----
### Auto

* 초기화하는 값의 타입으로 초기화 할 변수의 타입을 자동 지정.
* 변수 선언 외에도 문법이 업데이트 됨에 따라 다른 용도들이 생겼다.

 auto가 없었을 때는 밑과 같이 변수를 만들 때 타입을 직접 명시해야 했다. 
 ``` c++
int a;
char b = 'c';
vector<int> arr;
vector<int>::iterator it = arr.begin();
 ```
*vector<int>::iterator it = arr.begin()* 같이 뭔지 뻔히 알지만서도 일일이 타입을 직접 명시해줘야 했었다.

auto를 쓰게 된다면,
```c++
int a;
auto b = 'c';
vector<int> arr;
auto it = arr.begin();
```
과 같이 편하게 쓸 수 있다.

위에서 보는 것과 같이 auto는 변수의 타입 지정에 초기화하는 값을 이용하기 때문에 단순히
```c++
auto a;
```
라고 쓸 수 없다.

상수를 만들기 위한 const나 참조자로 만들기 위한 &를 auto에도 붙일 수 있다.
```c++
cosnt auto& n = 1;
// == const int& n = 1;
```

auto의 타입 유추는 [이 글][auto_deduction_link]을 보면된다.
대충 해석 하면 auto를 쓴 식을 템플릿 함수처럼 생각하면 된다고 한다.
글에서 나온 예시를 하나 봐보자.
```c++
const auto& x = 1 + 2
```
이런 변수 선언을
```c++
template<typename U>
void F(const U& x);

F(1+2);
```
로 봤을 때, U가 치환되는 타입이 auto가 유추한 타입이 된다.

c++문법이 업그래이드 됨면서 다음과 같은 용도로 쓸 수 있게 되었다.
* trailing return type(c++14)
* Structured binding (c++17)
  
더 있는 것 같은데 지금은 잘 모르겠으니 배워가면서 추가하고 링크도 추가해야겠다.

-----


[auto_deduction_link]: https://en.cppreference.com/w/cpp/language/template_argument_deduction#Other_contexts
