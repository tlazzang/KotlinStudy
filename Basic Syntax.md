# Kotlin - Basic Syntax

코틀린에서 리턴타입 Unit은 자바에서 void와 같다.
코틀린에서 리턴타입이 Unit인 경우 생략이 가능하다.
변수는 val 또는 var로 선언할 수 있고 val은 immutable(읽기전용) 변수고
var는 mutable 변수이다 val은 immutable하기 때문에 선언과 동시에 초기화가 되어야 한다.
```
val a : int = 3; == val a = 3;
```
변수의 타입을 명시적으로 지정해주지 않아도 대입된 값에 맞는 타입을 생성해준다.

String Interpolation(문자열 보간법)

```
var a = 1;
var s1 = "a is $a"
```

```
fun maxOf(a: Int, b: Int) : Int{
	if(a > b){
    return a;
    }else {
    return b;
    }
}
```
아래와 같이 조건식으로도 사용이 가능하다.
```
fun maxOf(a: Int, b: Int) = if(a > b) a else b
```

-nullable
값이 null일 수 있는 경우 타입에 nullable 마크를 명시해야 함
```
fun parseInt(str: String): Int?{

}
```
nullable 타입의 변수를 접근 할 때는 반드시 null 체크를 해야 함
그렇지 않으면 컴파일 오류가 발

-자동 타입 변환
타입 체크만 해도 자동으로 타입 변환이 됨
```
fun getStringLength(obj: Any): Int?{
	if(obj is String){
		return obj.length
	}
	return null
}
```
위 코드에서 Any타입은 모든 Object의 최상단 객체
자바에서의 Object와 유사함 String, Int 모든 객체를 받을 수 있는 객체
위에서 obj는 Any타입으로 받았지만 if문에서 String으로 타입 체크만 해줘도 자동으로 String으로 타입 변환이 됨.

-when expression (자바의 switch case와 유사)
```
fun describe(obj: Any): String =
	when(obj){
    	1 -> "One"
    	"Hello" -> "Greeting"
    	is Long -> "Long"
    	!is String -> "Not a String"
    	else -> "Unknown"
	}

```
-ranges
-In 연산자를 이용해서 숫자 범위를 체크 가능
```
var x = 3
if(x in 1..10){
	println("fits in range")
}
```

-range를 이용한 for loop
```
for(x in 1..5){
	print(x)
}
```

-collection
컬렉션도 in으로 loop가능

```
val items = listOf("apple", "banana", "kiwi")
for(item in items){
	println(item)
}
```