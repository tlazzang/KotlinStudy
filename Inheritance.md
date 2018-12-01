#Class and Inheritance

####상속
+ 코틀린의 최상위 클래스는 Any임
+ 클래스에 상위타입을 선언하지 않으면 Any가 상속됨
```
class Example1 //암시적인 Any 상속
class Example2 : Any() //명시적인 Any 상속
```

+ Any는 java.lang.Object와는 다른 클래스임
  + equals(), hashCode(), toString()만 있음

```
package kotlin

public open class Any{
	public open operator fun equals(other: Any?) : Boolean
    public open fun hashCode(): Int
    public open fun toString(): String
}
```

+ 명시적으로 상위타입을 선언하려면,클래스헤더의 콜론(:) 뒤에 상위타입을 선언하면 됨

```
open class Base(p: Int)

class Derived(p: Int) : Base(p)
```
+ 파생클래스에 기본생성자가 있으면 파생클래스의 기본생성자에서 상위타입의 생성자를 호출해서 초기화 할 수 있음
+ open 어노테이션은 Java의 final과 반대임
+ open class는 다른 클래스가 상속할 수 있음
+ 기본적으로 코틀린의 모든 class는 final임


####메소드 오버라이딩
+ 오버라이딩 될 메소드
 + open 어노테이션이 요구됟
+ 오버라이딩 된 메소드
 + override 어노테이션이 요구됨

```
open class Base{
	open fun v(){}
    fun nv(){}
}

class Derived(): Base(){
	override fun v(){}
}
```

####프로퍼티 오버라이딩
+ 메소드 오버라이딩과 유사한 방식으로 오버라이딩 가능

```
open class Foo{
	open val x: Int get {...}
}

class Bar1 : Foo(){
	override val x: Int = ...
}
```

####오버라이딩 규칙
+ 같은 멤버에 대한 중복된 구현을 상속받은 경우, 상속받은 클래스는 해당 멤버를 오버라이딩하고 자체 구현을 제공해야 함
+ super + <클래스명>을 통해서 상위클래스를 호출 할 수 있음
```
open class A{
	open fun f(){print("A")}
    fun a(){print("a")}
}

interface B{
	fun f(){print("B")}
    fun b(){print("b")}
}

class C() : A(), B{
	override fun f(){
    	super<A>.f() // call to A.f()
        super<B>.f() // call to B.f()
    }
}
```

####추상 클래스
+ abstract 멤버는 구현이 없음
+ abstract 클래스나 멤버는 open이 필요 없음
```
abstract class AbsClass{
	abstract fun f()
}

class MyClass() : AbsClass(){
	override fun f(){/* 구현 */}
}
```
