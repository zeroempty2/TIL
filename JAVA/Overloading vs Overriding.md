## 오버로딩(Overloading)
> 이름은 같지만 시그니처(파라미터 수, 타입)는 다른 메소드를 중복으로 선언하는 것

<br>

## ▶️ 오버로딩(Overloading)의 특징
* 메소드 이름이 같아야 한다. <br>
* 리턴형이 같아도 되고 달라도 된다. <br>
* 파라미터 개수가 달라야 한다. <br>
* 파라미터 개수가 같을경우, 데이터의 타입이 달라야 한다. <br>


<br>

## ▶️ 오버로딩 예제
다음과 같은 오버로딩 테스트라는 객체와 테스트라는 메서드가 있다.
```java
public class OverloadingTest {
  void test(){
    System.out.println("매개변수 없음");
  } //이름이 test인 메서드

  void test(int a, int b){
    System.out.println("매개변수 :"+a+", "+b);
  } //매개변수가 int형 2개인 test 메서드

  void test(String c){
    System.out.println("매개변수 : "+ c);
  } //매개변수가 String인 test 메서드
}

  public static void main(String[] args) {
    OverloadingTest ot = new OverloadingTest();
    ot.test();
    ot.test(1,2);
    ot.test("Overloading Test");
  }
``` 
이 코드를 실행시키면 다음과 같은 결과가 나온다.

![image](https://user-images.githubusercontent.com/117061586/230066610-3553e18f-effd-4d20-b671-a96ceedae71a.png)

오버로딩의 특징과 같이 같은 이름의 메서드를 여러개 정의하고, 매개변수만 변경하여 선언했을때, 호출 매개변수에 따라 다르게 매칭되어 해당 함수를 실행시킨다.<br>


<br>

## 오버라이딩(Overriding)
> 상속 관계에 있는 클래스 간에 같은 이름의 메소드를 정의하는 기술이다.<br>
만약 자식클래스가 부모클래스에서 선언된 것과 같은 메소드를 가질때, 메소드 오버라이딩이라고 한다.<br>


<br>

##  ▶️ 오버라이딩(Overriding)의 특징
* 오버라이드 하고자 하는 메소드가 상위 클래스에 존재해야한다.<br>
* 메소드 이름이 같아야 한다.<br>
* 메소드 파라미터 개수, 파라미터의 자료형이 같아야 한다.<br>
* 메소드 리턴타입이 같아햐 한다.<br>
* 상위 메서드와 동일하거나, 내용이 추가되어야 한다.<br>


<br>

## 오버라이딩(Overriding)예제
추상클래스 Car와 그를 상속받는 Audi가 있다고 하자.
```java
public abstract class Car {
  public void Start(String key){
    System.out.println("Car Start");
  }
 public void TurnOff(String key){
    System.out.println("Car TurnOff");
 }

public class Audi extends Car{
  @Override
  public void Start(String key){
    System.out.println(key + " Start");
  } // Car의 Start메소드 오버라이딩
}
``` 
Audi클래스에서 Car의 Start를 오버라이딩 했으므로 Audi의 Start 메소드를 실행시켰을때 Car의 Start와 다른 결과가 나오게 된다.
```java
  public static void main(String[] args) {
    Car audi = new Audi();

    audi.Start("Audi");
    audi.TurnOff("Audi");
  }
``` 

![image](https://user-images.githubusercontent.com/117061586/230071199-ae193f3e-e072-4fa5-ad82-2f6d7d21ec84.png)


<br>
   
## 정리
* 오버로딩은 한 클래스 내에 같은 이름의 메소드를 여러개 선언하여 사용하는 것을 말한다. 이렇게 메소드의 이름을 동일하게 만들어 프로그램의 가독성을 높일 수 있다.
* 오버라이딩은 부모로부터 받은 메소드의 내부로직을 필요에 따라 변경하는 것이다. 객체지향 언어의 특징인 다형성 중 하나이다.


<br>
[참조1](https://brunch.co.kr/@kimkm4726/2) - overloading vs. overriding / 대학생을 위한 IT <br>[참조2](https://private.tistory.com/25) 오버로딩과 오버라이딩 차이와 예제 / 오토봇팩토리 
