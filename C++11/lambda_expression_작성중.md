Lambda Expression

람다 표현식에서 필수적인 요소만 표현하면

```c++
[captures] (parameters) {body}
```
이다.

c++23 부터는 매개변수가 없을 시
```c++
[] {}
```
라고만 써도 된다고 한다.

* capture
  **캡쳐(capture)** 란 람다 함수가 **접근 할 수 있게**
  람다 함수 몸체 밖의 변수들을 콤마로 구분한 변수 리스트를 말한다.
  캡쳐들 앞에 선택적으로 *capture-default*를 붙일 수 있다.

  capture-deafault란 두가지가 다음과 같이 존재한다.
  * **&** automatic storage duration 1)에 있는 사용되는 변수들을 참조형태로 캡쳐한다.
  * **=** automatic storage duration에 있는 사용되는 변수들을 값 복사 형태로 캡쳐한다.
  
  캡쳐들은 다음과 같은 종류들이 있다.
  *identifier*
  :값 복사를 통한 캡쳐
  *identifier*...
  :값 복사를 통한 pack expansion
  &*identifier*
  :참조에 의한 캡쳐
  &*identifier*...
  :참조에 의한 pack expansion
  *this*
  :참조에 의한 현제 객체 (람다가 속해있는 객체가 없으면 캡쳐 되지 않는 듯)
  *identifier initializer* (c++14)
  : 복사에 의한 이니셜라이져
  &*identifier initializer* (c++14)
  : 참조에 의한 이니셜라이져
  **this* (c++17)
  :값 복사에 의한 현제 객체
  ...*identifier initializer*
  &...*identifier initializer*
  위의 두 개는 pack expansion인 이니셜라이져를 캡쳐한건데 pack expansion이 아직 뭔지 모르겠네

  capture default를 쓰고 같은 형식의 캡쳐를 넣으면 에러가 뜬다.
  ex)
  ```c++
  [&, this] (){}; //this도 &도 참조이기 때문에 에러난다.
  ```


1) 자동 저장 기간으로 흔히 스택에 있는 변수들을 말하는 것 같다.
  기억존속시간(https://en.cppreference.com/w/cpp/language/storage_duration)
