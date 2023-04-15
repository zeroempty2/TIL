## Generic
>제네릭(Generic)이란 "타입을 일반화"하는 것을 의미하며 클래스 내부에서 정하는 것이 아닌 사용자 호출에 의해 타입이 지정되는 것을 의미한다. <br> 
즉, 특정 타입의 변수형에 지정되는 것이 아닌 필요에 의해 여러 가지를 타입(Integer, String 등)을 사용하고 싶을 경우 사용한다. <br> 
주로 우리가 쓰는 컬렉션 프레임워크의 List 인터페이스도 제네릭 타입이다.(List <Integer> list =  new ArrayList <>(); 에서 많이 봤을 바로 <>가 바로 제네릭 표현식이다.)<br>


<br>

## ▶️ 제네릭 타입을 사용하는 이유 
* 재사용성 증가 <br>
제네릭 타입은 여러 타입의 파라미터를 삽입해 객체를 생성할 수 있기 때문에 코드를 간결하게 하고 재사용성을 높인다.<br>
동일한 기능을 하는 메서드에서 파라미터 타입만 다르게 사용할 경우, 제네릭 타입이 유용하게 쓰일 수 있다. <br>

* 컴파일 시 타입 에러 발견 가능<br>
제네릭 타입의 경우 컴파일시 잘못 사용되는 타입 문제점을 제거하기 위해 강하게 타입 체크를 수행한다. <br>
이덕분에 컴파일 이후 런타임 단계에서 타입 문제가 발생될 가능성을 방지해준다. <br>

* 컴파일러가 타입 변환 수행 <br>
컴파일 단계에서 컴파일러가 타입 캐스팅을 수행해주기 때문에 불필요하게 코드에서 타입 캐스팅을 해줄 필요가 없다.<br> 


<br>

## ▶️ 제네릭 타입 예제 
## 클래스 및 인터페이스 선언<br> 
제네릭 클래스와 인터페이스의 경우, 타입 파라미터를 명시하고 사용이 가능하며 타입 파라미터 상속이 가능하다.<br> 
```java
public class ClassName <T, K> { ... }
 
public class Main {
	public static void main(String[] args) {
		ClassName<String, Integer> a = new ClassName<String, Integer>();
	}
}
```
생성된 제네릭 클래스를 사용할때 즉, 객체를 생성해야 하는데 이 때 구체적인 타입을 명시를 해주어야 사용이 가능하다.<br> 
위 예시대로라면 T는 String이 되고, K는 Integer가 된다.<br> 
이 때 주의해야 할 점은 타입 파라미터로 명시할 수 있는 것은 참조 타입(Reference Type)밖에 올 수 없다. 즉, int, double, char 같은 primitive type은 올 수 없다. <br> 
또한, 다음과 같이사용자가 정의한 클래스도 타입으로 올 수 있다.<br> 
```java
public class ClassName <T> { ... }
 
public class Student { ... }
 
public class Main {
	public static void main(String[] args) {
		ClassName<Student> a = new ClassName<Student>();
	}
}
```

	
<br>
	
## 제네릭 클래스

```java
class ClassName<E> {
	
	private E element;	// 제네릭 타입 변수
	
	void set(E element) {	// 제네릭 파라미터 메소드
		this.element = element;
	}
	
	E get() {	// 제네릭 타입 반환 메소드
		return element;
	}
	
}
 
class Main {
	public static void main(String[] args) {
		
		ClassName<String> a = new ClassName<String>();
		ClassName<Integer> b = new ClassName<Integer>();
		
		a.set("10");
		b.set(10);
	
		System.out.println("a data : " + a.get());
		// 반환된 변수의 타입 출력 
		System.out.println("a E Type : " + a.get().getClass().getName());
		
		System.out.println();
		System.out.println("b data : " + b.get());
		// 반환된 변수의 타입 출력 
		System.out.println("b E Type : " + b.get().getClass().getName());
		
	}
}
```
ClassName이란 객체를 생성할 때 <> 안에 타입 파라미터(Type parameter)를 지정한다.<br>
a는 String 타입을 지정하고 String값인 "10"을 set 해줬고 , b는 Integer 타입을 지정하고 Integer값인 10을 넣어주었다.<br>
이때, 둘의 값은 같은 10이 나오지만 타입을 출력해보면 각각 String, Integer이 나오는 것을 볼 수 있다.<br>
![image](https://user-images.githubusercontent.com/117061586/232072307-a88cfa59-b1eb-44a3-9aea-0ac749bcf7e2.png)<br>
이렇게 외부 클래스에서 제네릭 클래스를 생성할 때 <> 괄호 안에 타입을 파라미터로 보내 제네릭 타입을 지정해주는 것이 제네릭 프로그래밍이다.<br>

	
<br>
	
## 제네릭 메소드<br>
별도로 메소드에 한정한 제네릭도 사용할 수 있다.<br>
일반적으로 선언 방법은 다음과 같다. <br>
```java
public <T> T genericMethod(T o) {	// 제네릭 메소드
		...
}
 
[접근 제어자] <제네릭타입> [반환타입] [메소드명]([제네릭타입] [파라미터]) {
	// 텍스트
}
```
클래스와는 다르게 반환타입 이전에 <> 제네릭 타입을 선언한다.<br>

```java
class ClassName<E> {

  private E element;	// 제네릭 타입 변수

  void set(E element) {	// 제네릭 파라미터 메소드
    this.element = element;
  }

  E get() {	// 제네릭 타입 반환 메소드
    return element;
  }
  <T> T genericMethod(T o) {	// 제네릭 메소드
    return o;
  }
}

  public static void main(String[] args) {
    ClassName<String> a = new ClassName<String>();
    ClassName<Integer> b = new ClassName<Integer>();

    a.set("10");
    b.set(10);

    System.out.println("a 값 : " + a.get());
    // 반환된 변수의 타입 출력
    System.out.println("a 타입 : " + a.get().getClass().getName());

    System.out.println();
    System.out.println("b 값 : " + b.get());
    // 반환된 변수의 타입 출력
    System.out.println("b 타입 : " + b.get().getClass().getName());

    // 제네릭 메소드 Integer
    System.out.println("<T> 반환타입 : " + a.genericMethod(3).getClass().getName());

    // 제네릭 메소드 String
    System.out.println("<T> 반환타입 : " + a.genericMethod("ABCD").getClass().getName());

    // 제네릭 메소드 ClassName b
    System.out.println("<T> 반환타입 : " + a.genericMethod(b).getClass().getName());

  }
```
파라미터 타입에 따라 T 타입이 결정되는 genericMethod()를 추가했다.<br>
반환값은 다음과 같다.<br>
![image](https://user-images.githubusercontent.com/117061586/232075285-2f2c27fe-5548-4dee-b8d9-14f5ba9d92ae.png)<br>
제네릭 메소드는 클래스에서 지정한 제네릭유형과 별도로 메소드에서 독립적으로 제네릭 유형을 선언하여 쓸 수 있다.<br>

그렇다면 제네릭 메소드는 왜 제네릭 클래스와 별도로 독립적인 제네릭이 사용될까?<br>
제네릭은 유형을 외부에서 지정준다. 즉 해당 클래스 객체가 인스턴스화 했을 때, new 생성자로 클래스 객체를 생성하고 <> 괄호 사이에 파라미터로 넘겨준 타입으로 지정이 된다는 뜻이다.<br>
하지만 static메소드는 객체가 생성되기 전에 이미 메모리에 올라가기 때문에 객체에서 타입을 얻어올 수 있는 방법이 없다.<br>
그렇기 때문에 제네릭 메소드는 제네릭 클래스 타입과 별도로 지정해주는 것이다.<br>

<br>

## 제한된 Generic(제네릭)과 와일드 카드<br>
제네릭을 특정 범위 내로 좁혀서 제한하고 싶다면 어떻게 해야할까? <br>
이 때 필요한 것이 바로 extends 와 super, 그리고 ?(물음표)다. ? 는 와일드 카드라고 해서 쉽게 말해 '알 수 없는 타입'이라는 의미다.<br>

```java
<K extends T>	// T와 T의 자손 타입만 가능 (K는 들어오는 타입으로 지정 됨)
<K super T>	// T와 T의 부모(조상) 타입만 가능 (K는 들어오는 타입으로 지정 됨)
 
<? extends T>	// T와 T의 자손 타입만 가능
<? super T>	// T와 T의 부모(조상) 타입만 가능
<?>		// 모든 타입 가능. <? extends Object>랑 같은 의미
```
보통 이해하기 쉽게 다음과 같이 부른다.<br>
 extends T : 상한 경계<br>
? super T : 하한 경계<br>
'<?>' : 와일드 카드(Wild card)<br>

<br>
이 때 주의해야 할 게 있다. K extends T와 ? extends T는 비슷한 구조지만 차이점이 있다.<br>
'유형 경계를 지정'하는 것은 같으나 경계가 지정되고 K는 특정 타입으로 지정이 되지만, ?는 타입이 지정되지 않는다는 의미다.<br>
	
<br>

* ```<K extends T>,<? extends T>``` <br>
이 것은 T 타입을 포함한 자식(자손) 타입만 가능하다는 의미다.<br>
대표적인 예로는 제네릭 클래스에서 수를 표현하는 클래스만 받고 싶은 경우가 있다. 대표적인 Integer, Long, Byte, Double, Float, Short 같은 래퍼 클래스들은 Number 클래스를 상속 받는다.<br>
즉,  Integer, Long, Byte, Double, Float, Short 같은 수를 표현하는 래퍼 클래스만으로 제한하고 싶은 경우 다음과 같이 쓸 수 있다.<br>

```java
public class ClassName <K extends Number> { ... }
```
<br>

* ```<K super T>, <? super T>```<br>
T 타입의 부모(조상) 타입만 가능하다는 의미다. 즉, 다음과 같은 경우들이 있다.<br>

 ```java
<K super B>	// B와 A타입만 올 수 있음
<K super E>	// E, D, A타입만 올 수 있음
<K super A>	// A타입만 올 수 있음
 
<? super B>	// B와 A타입만 올 수 있음
<? super E>	// E, D, A타입만 올 수 있음
<? super A>	// A타입만 올 수 있음
```

하한 한계. 즉 super 뒤에 오는 타입이 최하위 타입으로 한계가 정해진다.<br>
대표적으로는 해당 객체가 업캐스팅(Up Casting)이 될 필요가 있을 때 사용한다.<br>
예로들어 '과일'이라는 클래스가 있고 이 클래스를 각각 상속받는 '사과'클래스와 '딸기'클래스가 있다고 가정해보자.<br>
이 때 각각의 사과와 딸기는 종류가 다르지만, 둘 다 '과일'로 보고 자료를 조작해야 할 수도 있다. (예로들면 과일 목록을 뽑는다거나 등등..) 그럴 때 '사과'를 '과일'로 캐스팅 해야 하는데, 과일이 상위 타입이므로 업캐스팅을 해야한다. 이럴 때 쓸 수 있는 것이 바로 super라는 것이다.<br>

<br>

* ```<?> (와일드 카드 : Wild Card)```<br>
와일드 카드 <?> 은 <? extends Object> 와 마찬가지다. Object는 자바에서의 모든 API 및 사용자 클래스의 최상위 타입이다.<br>

```java
public class ClassName { ... }
public class ClassName extends Object { ... } 
```
보통 데이터가 아닌 '기능'의 사용에만 관심이 있는 경우에 <?>로 사용할 수 있다.

## ▶️ 참조
[참조1](https://st-lab.tistory.com/153) - 제네릭(Generic)의 이해 / Stranger's LAB <br>
[참조2](https://tecoble.techcourse.co.kr/post/2020-11-09-generics-basic/) -  자바 제네릭(Generics) 기초 / Tecoble<br>
[참조3](https://life-with-coding.tistory.com/489) -  자바 제네릭(Generic) 기본 및 활용 / 코딩젤리
