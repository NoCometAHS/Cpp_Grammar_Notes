Attribute
-------
### 사용 방법

타입, 코드, 객체 등등에 다음과 같은 코드를 추가한다.   
"코드"라는 말이 들어간 것에 맞게 별별 곳에 다 쓸 수 있는 듯 하다.

```c++
[[attribute-list]]
[[using attribute-namespace: attribute-list]] //c++17 이상부터
```

_attribute-list_ 는 다음과 같은 요소들을 0개 이상 콤마를 통해 구분한 것이다.
```c++
identifier
identifier(argument-list)
namespace::identifier
namespace::identifier(argument-list)
```

### 표준 attribute
표준 attribute들에는 다음과 같은 것들이 있다고 한다.   
표준 attribute는 구문 오류가 없어야 하고, 옳은 타겟에 적용되야하며 argument들은 ODR-use?를 따라야한다.

* [[noreturn]]  //c++11   
  해당 attribute를 가진 함수가 return을 하지 않음을 알린다. (무한 루프던, 예외던, 앱 종료든 간에 말이다.)
  함수가 실제로 리턴을 하는 상황은 정의되지 않았다고 한다.

  사용 방법은 함수 선언할 때 함수의 이름에 attribute를 쓰면 된다.
  [[noreturn]]를 쓰는 함수 선언이 하나라도 있다면, 첫번째 선언에 무조건 [[noreturn]]을 명시해줘야 한다.
  그렇지 않으면 ill-formed; no diagnostic required라고 하는 오류는 있으나 컴파일러가 감지 못하는 경우가 된다.
  
  ```c++
  [[noreturn]]
  void func(){
    throw;
  }
  /*
  or
  void  func [[noreturn]] () {
    throw;
  }
  */
  int main() {
      func();
      return 0;
  }
  ```
  
* [[carries_dependency]]  //c++11
  뭔가 atomic 나오는 것 보니깐 멀티 스래딩 할 때 쓰는 것 같은데, 잘 모르겠다.
  순서가 상관 없는 변수의 성능 높여 준다는 것 같은데.
  
* [[deprecated]], [[deprecated("reason")]]  //c++14
  어떤 이름이나 개체를 쓰지 못 하게 말리는 그런 느낌?
  
* [[fallthrough]]  //c++17
* [[maybe_unused]]  //c++17
* [[nodiscard]] //c++17,[[nodiscard("reason")]]  //c++20
* [[likely]], [[unlikely]]  //c++20
* [[no_unique_adress]]  //c++20
* [[assume(expression)]]  //c++23
* [[indeterminate]]  //c++26
