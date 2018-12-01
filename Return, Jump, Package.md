#Package, Return and Jumps

소스코드 맨 위에 패키지로 시작하지 않는 것은 디폴트 패키지에 포함되게 된다.

foo.Bar
bar.Bar 이름이 충돌 나는 경우 'as'키워드로 로컬 리네임 가능
import bar.Bar as bBar

3가지 Jump 표현식
return : 함수나 익명 함수에서 반환
break : 루프를 종료 시킴
continue: 루프의 다음 단계로 진행

Label로 Break and Continue

레이블 표현: label@, abc@, fooBar@

```
loop@ for(i in 1..10){
	println("---i: $i ---")
    
    for(j in 1..10){
    	println("j: $j")
        if(i+j > 12){
        	break@loop
        }
    }
}
```

함수가 중첩되어 있을때 함수의 return은 그 함수만 종료시킨다.

함수안에 람다식에서 return은 함수 전체를 종료 시킨다
람다는 함수가 아님.

-람다식에서 return할 때 주의사항
람다식에서 return시 nearest enclosing함수가 return됨
람다식에서 대해서만 return 하려면 label을 이용해야 함.

```
fun foo3(){
	var ints = listOf(0, 1, 2, 3)
    ints.forEach label@ {
    	if(it == 1) return@label
        print(it)
    }
    print("End")
}
```

-암시적 레이블
람다식에서만 return하는 경우 label을 이용해서 return해야 함
직접 label을 사용하는 것 보다 암시적 레이블이 편리함
암시적 레이블은 람다가 사용된 함수의 이름과 동일함

```
fun foo3(){
	var ints = listOf(0, 1, 2, 3)
    ints.forEach {
    	if(it == 1) return@forEach
        print(it)
    }
    print("End")
}
```

-레이블 return시 값을 반환할 경우
return + @label + 값

```
fun foo3(): List<String>{
	var ints = listOf(0, 1, 2, 3)
    val result = ints.map {
    	if(it == 0){
        	return@map "zero"
        } 
        "number $it"
    }
    return result
}

```