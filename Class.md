#Kotlin classes and Inheritance (클래스와 상속)

-클래스
클래스는 class 키워드로 선언함
클래스 이름
클래스 헤더(형식 매개변수, 기본 생성자 등)
클래스 바디(중괄호{})

```
class Invoice(data: Int){

}
```

헤더와 바디는 옵션이고, 바디가 없으면 {}도 생략 가능
```
class Empty
```

-기본생성자
클래스 별로 1개만 가질 수 있음
클래스 헤더의 일부
클래스 이름 뒤에 작성

```
class Person constructor(firstName: String){

}
```

어노테이션이나 접근지정자가 없을 때는, 기본생성자의 constructor 키워드를 생략가능

```
class Person (firstName: String){

}
```

기본생성자는 코드를 가질 수 없음
초기화는 초기화(init) 블록 안에서 작성해야 함
초기화 블록은 init 키워드로 작
기본생성자의 파라미터는 init블록 안에서 사용 가능함

```
class Customer(name: String){
	init{
    	logger.info("Customer initialized with value ${name}")
    }
}
```

-기본생성자의 파라미터는 프로퍼티 초기화 선언에도 사용 가능
```
class Customer(name: String){
	val customerKey = name.toUpperCase()
}
```

-프로퍼티 선언 및 초기화는 기본생성자에서 간결한 구문으로 사용 가능
```
class Person(val FirstName: String, val lastName: String){

}
```

-기본생성자에 어노테이셔 접근지정자 등이 있는 경우 constructor 키워드가 필요함
```
class Customer public @inject constructor(name: String){...}
```

-보조생성자
클래스 별로 여러 개를 가질 수 있음
constructor 키워드로 선언

```
class Person{
	constructor(parent: Person){
    	parent.children.add(this)
    }
}
```

보조생성자
클래스가 기본 생성자를 가지고 있다면, 각각의 보조생성자들은 기본생성자를 직접 or 간접적으로 위임해 주어야 함
this 키워드를 이용
직접적 : 기본생성자에 위임
간접적 : 다른 보조생성자에 위임

```
class Person(val name: String){
	constructor(name: String, parent: Person) : this(name){
    
    }
    
    constructor() : this("홍길동", Person()){
    
    }
}
```

-생성된 기본생성자 (디폴트 생성자)
클래스에 기본생성자 or 보조생성자를 선언하지 않으면, 생성된 기본생성자가 만들어짐
generated primary constructor
매개변수가 없음
가시성이 publicdla
만약 생성된 기본생성자의 가시성이 public이 아니어야 한다면, 다른 가시성을 가진 빈 기본생성자를 선언해야 함

```
class DontCreateMe private constructor(){

}
```

####인스턴스 생성
+ 코틀린은 new 키워드가 없음
+ 객체를 생성하려면 생성자를 일반 함수처럼 호출 하면 됨
```
val invoice = Invoice()

val customer = Customer("Joe Smith")
```

####클래스가 포함할 수 있는 것들
+ Constructors and initializer blocks
+ Functions
+ Properties
+ Nested and Inner Classes
+ Object Declarations