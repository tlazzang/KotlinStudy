# Object Expressions and Declarations

#### Object 용도
- 어떤 class에서 조금 변경된 객체를 생성 할 때
- 새로운 subclass의 명시적인 선언 없이 객체 생성

#### Object Expressions
- Java익명 객체

#### Object Declarations
- 싱글턴

#### Companion Object
- 싱글턴 + Class Method (static)

#### 객체 표현식 문법
- 어떤 클래스를 상속 받은 익명 객체를 생성

```
window.addMouseListener(object : MouseAdapter(){
	override fun mouseClicked(e: MouseEvent){ }
    override fun mouseEntered(e: MouseEvent){ }
})
```

#### 객체 표현식 상
- 슈퍼타입의 생성자가 있는 경우, 반드시 값을 전달 해 주어야함
- 슈퍼타입이 여러 개인 경우 콤마로 구분해서 명시 해주면 됨

```
open class A(x: Int){
	public open val y: Int = x
}

interface B {...}

val ab: A = object : A(1), B {
	override val y = 15
}
```

#### 객체 표현식 상속 없는 경우
- 특별히 상속 받을 supertypes가 없는 경우, 간단하게 작성가능

```
val adHoc = object{
	var x: Int = 0
    var y: Int = 0
}
print(adHoc.x + adHoc.y)
```

#### 객체 표현식 특징
- 익명 객체의 코드는 enclosing scope의 변수를 접근 할 수 있음
- Java와는 다르게 final variables 제약 조건이 없음

```
fun countClicks(window: JComponent){
	var clickCount = 0
    var enterCount = 0
    window.addMouseListener(object : MouseAdapter(){
    	override fun mouseClicked(e: MouseEvent){
        	clickCount++
        }
        override fun mouseEntered(e: MouseEvent){
        	enterCount++
        }
    })
}
```

#### 객체 선언 문법
- object 키워드 뒤에 항상 이름이 있어야 함
- object declaration은 object expression이 아님
- 그래서 할당 구문의 우측에 사용 될 수가 업슴

```
object DataProviderManager{
	fun registerDataProvider(provider: DataProvider){}
    val allDataProviders: Collection<DataProvider>
}

DataProviderManager.registerDataProvidder(...)
```

#### 동반자 객체(Companion Object)
- 클래스 내부의 object declaration은 companion 키워드를 붙일 수 있음

```
class MyClass{
	companion object Factory{
    	fun create() : Myclass = MyClass()
    }
}

val instance = MyClass.create()
```

