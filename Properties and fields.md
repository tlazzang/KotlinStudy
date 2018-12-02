#### 프로퍼티 선언
+ 코틀린 클래스는 프로퍼티를 가질 수 있음
 + var(mutable) / val(immutable)
```
class Address{
	var name: String = "Kotlin"
    var city: String = "Seoul"
}
```
+ 프로퍼티 사용은 자바의 필드를 사용하듯이 하면 됨
```
fun copyAddress(address: Address): Address{
	val result = Address()
    result.name = address.name
    //...
    return result
}
```

#### 프로퍼티 문법
- 전체문법
```
var <propertyName>[: <PropertyType>] [=<property_initializer>][<getter>][<setter>]
```
- 옵션(생략가능)
 - PropertyType (initializer에서 타입 추론 가능한 경우)
 - property_initializer
 - getter
 - setter

#### var(mutable) 프로퍼티
- mutable하기 때문에 getter와 setter 둘다 존재

#### val(immutable) 프로퍼티
- immutable하기 때문에 getter만 존재

#### Custom accessors(getter, setter)
- custom accessor는 프로퍼티 선언 내부에, 일반 함수 처럼 선언 할 수 있음
- 관습적으로 setter의 파라미터의 이름은 value임(변경가능)

#### 프로퍼티
- accessor에 가시성 변경이 필요하거나
- accessor에 어노테이션이 필요한 경우
- 기본 accessor의 수정 없이 body없는 accessor를 통해 정의 가능
```
var setterVisibility: String = "abc"
	private set
var setterWithAnnotation: Any? = null
	@inject set
```
- Body를 작성해 주어도 됨
```
var setterVisibility: String = "abc"
	private set(value){
    	field = value
    }
```

#### Backing Fields
- 코틀린 클래스는 field를 가질 수 없음
- 'field'라는 식별자를 통해 접근할 수 있는, automatic backing field를 제공함
- field는 프로퍼티의 accessor에서만 사용가능 함

```
var counter = 0
	set(value){
    	if(value >= 0) field = value
    }
```



