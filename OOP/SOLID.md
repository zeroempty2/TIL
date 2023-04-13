## SOLID
>컴퓨터 프로그래밍에서 SOLID란 로버트 마틴이 2000년대 초반에 명명한 객체 지향 프로그래밍 및 설계의 다섯 가지 기본 원칙을 마이클 페더스가 두문자어 기억술로 소개한 것이다. <br>프로그래머가 시간이 지나도 유지 보수와 확장이 쉬운 시스템을 만들고자 할 때 이 원칙들을 함께 적용할 수 있다. <br>SOLID 원칙들은 소프트웨어 작업에서 프로그래머가 소스 코드가 읽기 쉽고 확장하기 쉽게 될 때까지 소프트웨어 소스 코드를 리팩터링하여 코드 냄새를 제거하기 위해 적용할 수 있는 지침이다. <br>이 원칙들은 애자일 소프트웨어 개발과 적응적 소프트웨어 개발의 전반적 전략의 일부다.

<br>

## ▶️ SRP(Single Responsibility Principle) - 단일 책임 원칙
* 한 클래스는 하나의 책임만 가져야 한다.<br>
* 하나의 책임은 클수도 있고, 작을 수도 있다.<br>
* 하나의 책임의 기준은 변경이다.<br>
    * 변경이 발생하였을 때, 변경해야 될 부분이 적으면, 단일 책임 원칙을 잘 따른 것이다.<br>
    * 클래스를 변경해야하는 이유가 오직 하나여야 한다.<br>

<br>
예를 들어 purchase란 클래스가 있으면 그 클래스는 구매의 기능만 담당해야한다. 이 purchase가 구매뿐만 아니라 판매의 기능도 담당하고 있으면, 단일 책임 원칙을 지키지 않은 클래스이다. purchase가 구매의 기능만 담당하고 있으니 만약 이 클래스를 변경해야 한다면 이유는 구매기능의 변경 하나 뿐일 것이다.

<br>

## ▶️ OCP(Open/Closed Principle) - 개방/페쇄 원칙
* 확장에는 열려있으나 변경에는 닫혀있어야한다.<br>
* 변경을 위한 비용은 줄이고, 확장을 위한 비용은 극대화 해야한다.<br>
* 객체지향의 장점을 극대화하는 아주 유용한 원리(feat, 다형성)<br>

<br>
속성을 새로 추가할때 기존 코드에서 최대한 변경없이 추가할수 있도록 설계해야한다.<br>
예를들어 휴대폰의 종류별로 정보를 가져오는 기능을 만든다고 한다.<br>
이때, 첫번째 방법은 휴대폰의 종류별로 클래스를 만들어 휴대폰의 속성을 일일히 넣어주는 것이고,<br>
두번째 방법은 폰이라는 클래스를 만들어 그 안에 핸드폰의 속성들을 넣고 각 휴대폰 종류에서 폰 클래스를 상속받는것이다.<br>
두 방법을 비교했을때 변경없이 확장이 용이한 것은 두번째 방법이다. <br>
다시 말해 같은 코드를 반복해서 쓰는것을 피하고, 기능 확장을 할때 많은 수정이 없는게 이 개방 폐쇄의 원칙을 잘 지키는 것이다.<br>

<br>

## ▶️ LSP(Liskov Substitution Principle) - 리스코프 치환 원칙 
* 상위 타입의 객체를 하위 타입의 객체로 교체해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.<br>
* 정확성을 깨뜨리면 안된다.<br>
* 원칙을 지키지 않으면 , 자식클래스의 인스턴스를 파라미터로 전달 했을 때 메소드가 이상하게 작동 할 수 있다.<br>
* 스피커 기능 중 볼륨 업은 소리를 키우는 기능이다. 하만카돈 스피커의 볼륨업은 소리를 줄이면 안된다. 소리가 작게 커지더라도 소리를 키워야한다. → 그래야 믿고 쓸 수 있다.<br>
* 부모클래스에 대해 작성된 단위테스트가 자식클래스에 대해서는 작동되지 않을 것이다.<br>
* 상속을 잘 활용하고 있다면, 이미 LSP를 하고 있다<br>

<br>

상위 타입에서 정한 명세를 하위 타입에서도 그대로 지킬 수 있을 때 상속을 해야 한다.<br>
 직사각형과 그를 상속받는 정사각형을 예로 들자면,<br>
```java
class Rectangle {
    private int width;
    private int height;

    public void setHeight(int height) {
        this.height = height;
    }

    public int getHeight() {
        return this.height;
    }

    public void setWidth(int width) {
        this.width = width;
    }

    public int getWidth() {
        return this.width;
    }

    public int getArea() {
        return this.width * this.height;
    }
}

class Square extends Rectangle {
    @Override
    public void setHeight(int value) {
        this.width = value;
        this.height = value;
    }

    @Override
    public void setWidth(int value) {
        this.width = value;
        this.height = value;
    }
}

public class Test {
   static void testLSP(Rectangle rectangle) {
         rectangle.setWidth(5);
         rectangle.setHeight(3);
         System.out.println(rectangle.getArea());
   }
}

public static void main(String[] args){
      Rectangle rectangle = new Rectangle();
      rectangle.setWidth(5);
      rectangle.setHeight(2);
      rectangle.getArea(); // 10

      Rectangle square = new Square();
      square.setWidth(5);
      square.setHeight(2);
      square.getArea(); // 25
      
      Test.testLSP(new Rectangle());
      Test.testLSP(new Square());
}
``` 
직사각형은 정사각형이 아니지만 정사각형은 직사각형이다.<br>
Rectangle은 세로와 가로의 길이를 다르게 받게 되어있고, Square은 세로와 길이를 같게 받는다.<br>
두 클래스 모두 넓이는 가로x세로로 구할 수 있다.<br>
이때, 가로와 세로의 길이를 두 클래스 모두 동일하게 넣어주어도 넓이의 결과값은 다르게 나온다.<br>
그렇다면 Square을 Rectangle로 교체했을때 해당 객체를 사용하는 프로그램은 정상적으로, 이전과 같이 작동할까?<br>
물론 아니다. 리스코프 치환 원칙이 이뤄지지 않는 경우를 이런 것이라고 이해했다.<br>
우리는 '직사각형은 정사각형이 아니지만 정사각형은 직사각형이다'라는 것을 이해하고 코드를 이렇게 썼겠지만, 이렇게 쓰면 자바는 둘의 차이를 이해하지 못하는 것이다.<br>

<br>

## ▶️ ISP(Interface segregation Principle) - 인터페이스 분리 원칙
* 클라이언트가 자신이 사용하지 않는 메서드에 의존하지 않아야 한다.<br>
* 특정 클라이언트를 위하여, 하나의 범용 인터페이스를 제공하는 것 보다 여러 개의 인터페이스를 제공하는 것이 낫다.<br>
예를들어 phone이라는 인터페이스를 만들고, 거기에 call이라는 기능과 wirelesscharge라는 메서드를 넣는다고 하자.<br>
그런데 phone 인터페이스를 상속받는 휴대폰 클래스를 만들다 문제가 생겼다.<br>
wirelesscharge가 없는 휴대폰 클래스를 만들어야 하는 것이다.<br>
그대로 만들면 나중에 wirelesscharge 메서드를 호출했을때 에러가 날 것이다.<br>
이는 인터페이스 분리 원칙을 위반한 것이다. <br>
그렇다면 어떻게 만들어야 할까?<br>
인터페이스를 세분화 하면 된다.<br>
phone인터페이스에는 call이라는 메서드만 넣고 따로  wirelesscharge 메서드가 들어가는 인터페이스를 생성한다. <br>
그리고 그 인터페이스를 wirelesscharge를 사용하는 휴대폰 클래스에만 상속해주면 될 것이다.<br>

<br>

## ▶️ DIP(Dependency Inversion Principle) - 의존관계 역전 원칙
* 객체들 간의 협력 하는 과정에서 의존 관계가 형성 된다.<br>
* 의존관계 역전 원칙은 이러한 의존 관계를 맺을 때, 어떻게 하면 변화에 용이하게 대응할 수 있을 것인가에 대한 가이드 라인이다.<br>
* 변하기 쉬운 것과 어려운 것을 구분해야한다.<br>
* 변하기 쉬운 것<br>
    * 구체적인 행동<br>
    * 스마트폰으로 전화를 건다.<br>
    * 공중전화로 전화를 건다.<br>
    * 이메일을 발송한다.<br>
    * 카카오톡 메시지를 전달한다.<br>
* 변하기 어려운 것<br>
    * 흐름이나 개념과 같은 추상적인 것<br>
    * 전화를 건다<br>
    * 메시지를 전달한다.<br>

```java
public interface Phone {
   void call(String phoneNumber);
}

public class SmartPhone implements Phone {
    @Override
    public void call(String phoneNumber) {
        System.out.println("스마트폰 : " + phoneNumber);
    }
}

public class PublicPhone implements Phone {
    @Override
    public void call(String phoneNumber) {
        System.out.println("공중 전화 : " + phoneNumber);
    }
}

public class InternetPhone implements Phone {
    @Override
    public void call(String phoneNumber) {
        System.out.println("인터넷 전화 : " + phoneNumber);
    }
}


public class Person {
  private Phone phone;
  
  public void setPhone(Phone phone) {
      this.phone = phone; // 폰이 계속 바뀜.
  }

  public void call(String phoneNumber) {
      phone.call(phoneNumber);
  }
}

public class Main {
	public static void main(String[] args) {
				Person person = new Person();
        person.setPhone(new SmartPhone());
        person.setPhone(new InternetPhone());



        // 코드 수정 X
        person.call("01012341234"); // 스마트폰 전화,
  }
}
```

<br>

## ▶️ 참조
[참조1](https://bit.ly/3mukLIq) - SOLID (객체 지향 설계) / 위키백과 <br>
