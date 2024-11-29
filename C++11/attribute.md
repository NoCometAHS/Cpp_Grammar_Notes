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


표준 attribute들에는 다음과 같은 것들이 있다고 한다.
* [[noreturn]]  //c++11   
  해당 attribute를 가진 함수가 return을 하지 않음을 알린다. (무한 루프던, 예외던, 앱 종료든 간에 말이다.)
  함수가 실제로 리턴을 하는 상황은 정의되지 않았다고 한다.
  
  The first declaration of the function must specify this attribute if any declaration specifies it.
  이게 뭔 소리인지 모르겠네.
  
* [[carries_dependency]]  //c++11
* [[deprecated]], [[deprecated("reason")]]  //c++14
* [[fallthrough]]  //c++17
* [[maybe_unused]]  //c++17
* [[nodiscard]] //c++17,[[nodiscard("reason")]]  //c++20
* [[likely]], [[unlikely]]  //c++20
* [[no_unique_adress]]  //c++20
* [[assume(expression)]]  //c++23
* [[indeterminate]]  //c++26
