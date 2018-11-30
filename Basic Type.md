#Kotlin - Basic Type

-숫자(Numbers)
Java의 숫자형과 거의 비슷하게 처리
Kotlin에서 Number는 클래스임, java의 primitive type에 직접 접근 할 수 없음
Java에서 숫자형이던 char가 kotlin에서는 숫자형이 아님.

-배열
배열은 Array 클래스로 표현됨
get, set ([]연산자 오버로딩됨)
size 등 유용한 멤버 함수 포함

```
var array: Array<String> = arrayOf("코틀린", "강좌")
println(array.get(0))
println(array[0])
println(array.size)
```

-특별한 Array 클래스
Primitive 타입의 박싱 오버헤드를 없애기 위한 배열
IntArray, ShortArray, IntArray
Array를 상속한 클래스들은 아니지만, Array와 같은 메소드와 프로퍼티를 가짐
size 등 유용한 멤버 함수 포함
