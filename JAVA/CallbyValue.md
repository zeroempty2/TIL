## Call by Value? Call by Reference?
>프로그래밍 언어들의 메소드 매개변수 호출 방식에는 여러 가지가 있으며 호출 방식은 언어마다 다르게 되어 있다. 대표적으로 C++은 Call by Reference를 사용한다.<br>
Call by Value는 함수의 인자를 전달할 때 '값을 전달하는 방식'이고 Call by Reference는 '주소를 전달하는 방식'이다.<br>
자바는 Call by Value 방식만 사용한다.<br>

<br>

##  Call by Value
Call by Value 는 메서드를 호출할 때 값을 넘겨주기 때문에 Pass by Value 라고도 부른다.<br>
메서드를 호출하는 호출자 (Caller) 의 변수와 호출 당하는 수신자 (Callee) 의 파라미터는 복사된 서로 다른 변수이다.<br>
값만을 전달하기 때문에 수신자의 파라미터를 수정해도 호출자의 변수에는 아무런 영향이 없다.<br>


<br>

## Call by Reference
Call by Reference 는 참조 (주소) 를 직접 전달하며 Pass By Reference 라고도 부른다.<br>
참조를 직접 넘기기 때문에 호출자의 변수와 수신자의 파라미터는 완전히 동일한 변수이다.<br>
메서드 내에서 파라미터를 수정하면 그대로 원본 변수에도 반영된다.<br>


<br>

## 자바는 Call by Value
Java 는 오직 Call by Value 로만 동작한다.<br>
예시를 들어보자<br>
```java
public void method1(){
    int a = 10;
    int b = 20;
    System.out.println("Before Call Method2 : (a  =" + a + ", b = " + b + ")");
    method2(a,b);
    System.out.println("After Call Method2 : (a  =" + a + ", b = " + b + ")");
  }
  public void method2(int a, int b){
   a = 30;
   b = 40;
   System.out.println("Method2 : (a  =" + a + ", b = " + b + ")");

  }
```
method1과 method2의 두 함수가 존재할 때, method1은 a=10, b=20 이라는 값을 넘겨주고, method2는 이 값을 a=30, b=40이라는 값으로 변경한다.<br>
이 함수의 값은 다음과 같다.<br>
![image](https://user-images.githubusercontent.com/117061586/235157289-6ad96f2b-cb88-4c3c-88da-c343d35ee4d6.png)<br>
자바가 Call by Value 이기 때문에 이와 값이 출력이 되는 것이다.<br>

하지만 다음과 같은 예시에서는 조금 다른 값이 나온다.<br>
```java
class Person{
  int age;
  String name;
  public Person(int age, String name){
    this.age = age;
    this.name = name;
  }
}

  public void method1(){
    Person person = new Person(22,"Kim");
    System.out.println("Before Call Method2 : (a = " + person.age + ", b = " + person.name + ")");
    method2(person);
    System.out.println("After Call Method2 : (a = " + person.age + ", b = " + person.name  + ")");
  }
  public void method2(Person person){
   person.age = 25;
   person.name = "Lee";
   System.out.println("Method2 : (a = " + person.age + ", b = " + person.name + ")");
  }
```
이 예시에서는 다음과 같이 출력된다.<br>
![image](https://user-images.githubusercontent.com/117061586/235158945-d8f304cb-2e44-4812-b2d1-0c13aae92454.png)<br>
자바가 Call by Value 라면 이전 예시와 같이 Merhod2를 호출해도 값이 변해야 하지 않는데 왜 이와 같이 출력되는 것일까? <br>
그 이유는 자바의 Reference Type에 있다.<br>
<br>

## Reference Type의 동작 원리
자바에서는 Call by Value 방식을 수행할 때, 값을 넘겨받은 메소드에서값을 복사하여 새로운 지역 변수에 저장한다. 이 때 Method2는
Method1의 변수를 사용한 것이 아니라, 자신이 새롭게 생성한 지역 변수에 Method1의 변수 이름과 변수 값을 복사하여 사용하는 것이다.<br>
이 때문에 아무리 Method2에서 A와 B의 값을 바꾸어도 Method1의 A, B에게 영향을 끼칠 수 없다.<br>
하지만, 만약 자바가 Call by Value가 아닌 Call by Reference 방식을 사용한다면 A와 B에 영향을 끼칠 수 있다.<br> 왜냐면 이 둘은 다른 변수가 아니라 같은 주소를
공유하는 변수이기 때문이다.<br>
그렇다면 Call by Value인 자바가 왜 예시 2와 같은 결과 값을 내는 것일까?<br>
![1 drawio](https://user-images.githubusercontent.com/117061586/235164855-4123b271-9d01-47c4-8ffa-e898707e57ea.png)<br>
바로 참조 타입은 이러한 방식을 사용하기 때문이다.<br>
참조타입은 Heap Memory 영역에 생성된 객체의 주소값을 참조하기 때문에 '참조 타입' 이라고 불린다.<br>
따라서 Method1에서 Method2로 넘겨준건 Person의 주소값이고, Method1이 가지고 있는 주소값과 동일한 주소값을 가지고 이 객체의 상태를 수정하면 당연히 두 Person의 값은 동일한 주소를 참조하기 때문에, <br>
![image](https://user-images.githubusercontent.com/117061586/235158945-d8f304cb-2e44-4812-b2d1-0c13aae92454.png)<br>
이러한 결과가 나오는 것이다.<br>


<br>


<br>

[참조1](https://bcp0109.tistory.com/360) - Java 의 Call by Value, Call by Reference / 뱀귤 블로그 <br>
[참조2](https://velog.io/@ahnick/Java-Call-by-Value-Call-by-Reference) - Call by Value, Call by Reference / ahnick.log <br>
