## DI
* 각 계층 사이, 각 클래스 사이에 필요로하는 의존 관계를 컨테이너가 자동으로 연결해주는것
* 각 클래스의 사이의 의존 관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는 것
<br>

## ▶️ DI의 세가지 방법

### 1.생성자 주입(Constructor Injection)    
생성자 주입은 생성자를 통해 의존 관계를 주입하는 방법이다.
```java
  @Component
  public class Cup{
    private Water water;
    @Autowired
    public Cup(Water water) {
      this.water = water;
    }
  }
```
final로 선언된 필드의 생성자를 자동으로 생성해주는 Lombok의 @RequiredArgsConstructor를 사용하면 다음과 같이 생략이 가능하다.<br>
```java
  @Component
  @RequiredArgsConstructor
  public class Cup{
    private final Water water;
  }
```
생성자 주입은 생성자의 호출 시점에 1회 호출 되는 것이 보장된다. 그렇기 때문에 주입받은 객체가 변하지 않거나, 반드시 객체의 주입이 필요한 경우에 강제하기 위해 사용할 수 있다.

<br>

### 2.수정자 주입(Setter Injection)    
수정자 주입은 필드 값을 변경하는 Setter를 통해서 의존 관계를 주입하는 방법이다. 
```java
  @Component
  public class Cup{
    private Water water;
    @Autowired
    public void setWater(Water water){
      this.water = water;
    }
  }
```

<br>

### 3.필드 주입(Field Injection)  
필드 주입은 필드에 바로 의존 관계를 주입하는 방법이다.
```java
  @Component
  public class Cup{
    @Autowired
    private Water water;
    }
```
가장 편리한 방법 같으나, 외부에서 접근이 불가능하다는 단점이 존재한다.


<br>

## ▶️ 세가지 방법중 생성자 주입(Constructor Injection)을 이용해야하는 이유
필드 주입 방식을 사용하면 인테리제이에서는 필드 주입방식은 권장하지 않고, 생성자 주입을 권장한다고 경고를 띄운다.<br>
그렇다면 왜 생성자 주입 방식을 권장하는 것일까?

* 객체의 불변성확보가 가능하다<br>
생성자로 의존성을 주입하면 final로 선언할 수 있고, 이로인해 런타임에서 의존성을 주입받는 객체가 변할 일이 없어지게 된다.<br>
하지만 수정자 주입이나 일반 메소드 주입을 이용하면 불필요하게 수정의 가능성을 열어두어 유지보수성을 떨어뜨린다. 그러므로 생성자 주입을 통해 변경의 가능성을 배제하고 불변성을 보장하는 것이 좋다.<br>
또한, 필드 주입 방식은 null이 만들어질 가능성이 있는데, final로 선언한 생성자 주입 방식은 null이 불가능하기 때문에 NPE방지를 할 수 있다.

<br>

* 순환 참조 방지<br>
다음과 같은 순환참조가 일어날 수 밖에 없는 코드가 있다고 해보자.
```java
 @Component
  public class Cup {
    @Autowired
    private Water water;
    public void cup() {
      water.water();
    }
  }

  @Component
  public class Water {
    @Autowired
    private Cup cup;
    public void water() {
      cup.cup();
    }
  }
``` 
어플리케이션을 구동시켰을때, 순환참조가 일어날수 밖에 없는 메서드가 있음에도 불구하고 구동이 잘 된다.<br>
그리고 문제가 있는 메서드를 실행시켰을때, 순환참조가 일어나게 된다.<br>
즉, 메서드가 실행되기 전까지는 순환참조가 있었더라도 알 수 없다.<br>
하지만 생성자 주입 방식을 사용하면 어플리케이션을 구동시켰을때 순환 참조에러가 일어나기 때문에 서버가 실행되지 않기 때문에 어플리케이션 구동 시점에서 순환참조 에러가 있는지 확인 할 수 있다.<br>

<br>
두 방식의 순환 참조의 오류를 발견하는 시점의 차이는 빈 생성 시기의 차이 때문에 발생한다.<br>
필드 주입(Field Injection) 방식은 빈을 먼저 생성한 후에 어노테이션이 붙은 필드에 해당하는 빈을 찾아서 주입하는 방식이다. <br>
즉, 빈을 먼저 생성한 후에 필드에 대해서 주입하기 때문에 빈 객체를 생성한 시점에는 순환 참조의 발생 여부를 알 수가 없다. (생성 -> 주입)<br>

<br>
반면 생성자 주입(Constructor Injection) 같은 경우에는 생성자로 객체를 생성하는 시점에 필요한 빈을 주입한다.<br>
다시 말하면 빈 객체를 생성하는 시점에 생성자의 파라미터 빈 객체를 찾아서 먼저 주입한 뒤에 주입받은 빈 객체를 이용하여 생성하게 된다. (주입 -> 생성)<br>
때문에 런타임 시점이 아니라 애플리케이션 구동 시점에서 순환 참조 오류를 발견할 수 있게 된다.<br>


<br>
❗❗스프링부트 2.6부터는 순환 참조가 기본적으로 허용되지 않도록 변경되었다. 필드 주입을 받아도 순환 참조가 발생한다면 애플리케이션 구동 시점에 에러가 발생한다.