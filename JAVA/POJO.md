## POJO(Plain Old Java Object)
> Plain Old Java Object, 간단히 POJO는 말 그대로 해석을 하면 오래된 방식의 간단한 자바 오브젝트라는 말로서 Java EE 등의 중량 프레임워크들을 사용하게 되면서 해당 프레임워크에 종속된 "무거운" 객체를 만들게 된 것에 반발해서 사용되게 된 용어이다. 2000년 9월에 마틴 파울러, 레베카 파슨, 조쉬 맥킨지 등이 사용하기 시작한 용어로서 마틴 파울러는 다음과 같이 그 기원을 밝히고 있다.

“	우리는 사람들이 자기네 시스템에 보통의 객체를 사용하는 것을 왜 그렇게 반대하는지 궁금하였는데, 간단한 객체는 폼 나는 명칭이 없기 때문에 그랬던 것이라고 결론지었다. 그래서 적당한 이름을 하나 만들어 붙였더니, 아 글쎄, 다들 좋아하더라고.	”
 	
— 마틴 파울러
> POJO라는 용어는 이후에 주로 특정 자바 모델이나 기능, 프레임워크 등을 따르지 않은 자바 오브젝트를 지칭하는 말로 사용되었다. 스프링 프레임워크는 POJO 방식의 프레임워크이다.
<br>

## ▶️ 왜 POJO를 지향해야 하는가?
* 스프링 프레임워크 이전에는 원하는 엔터프라이즈 기술이 있다면 그 기술을 직접적으로 사용하는 객체를 설계했었다. <br> 하지만 특정 기술과 환경에 종속되어 의존하게 된 자바 코드는 가독성이 떨어져 유지보수에 어려움이 생겼으며 특정 기술의 클래스를 상속받거나, 직접 의존하게 되어 확장성이 매우 떨어지는 단점이 생겼다. <br> 이 말은 객체지향의 화신인 자바가 객체지향 설계의 장점들을 잃어버리게 된 것이다.<br> 그래서 본래 자바의 장점을 살리는 '오래된' 방식의 '순수한' 자바객체 라는 뜻의 POJO라는 개념이 등장했다.


<br>

## ▶️ POJO의 조건
* 특정 규약에 종속되지 않는다. 
  *  자바언어와 꼭 필요한 API외에는 종속되지 말아야한다.<br> EJB2와 같이 특정 규약을 따라 만들게 하는 경우는 대부분 규약에서 제시하는 특정 클래스를 상속하도록 요구한다.<br> 그럴 경우 자바의 단일 상속 제한 때문에 더이상 해당 클래스에 객체지향적인 설계 기법을 적용하기가 어려워지는 문제가 생긴다.
* 특정 환경에 종속되지 않는다. 
  * 특정 기업의 프레임워크나 서버에서만 동작가능한 코드라면 POJO라 할 수 없다. POJO는 환경에 독립적이여야한다.<br> 특히 비지니스 로직을 담고 있는 POJO 클래스는 웹이라는 환경 정보나 웹 기술을 담고 있는 클래스나 인터페이스를 사용해서는 안된다.<br> 설령 나중에는 웹 컨트롤러와 연결되서 사용될 것이 분명하더라도 직접적으로 웹이라는 환경으로 제한해버리는 오브젝트나 API에 의존해서는 안된다. 그렇게 되면 웹 외의 클라이언트가 사용하지 못하기 때문이다.<br>
  기술적인 내용을 담은 웹 정보가 비즈니스 로직과 얽혀있으니 이해하기도 어렵다. <br>때문에 비지니스 로직을 담은 코드에 HTTPServletRequest, HttpSession, 캐시에 관련된 API가 등장한다면 진정한 POJO라고 할 수 없다.
* 객체 지향적 원리에 충실해야한다.
  * POJO는 객체지향적인 자바언어의 기본에 충실하게 만들어져야한다.<br> 자바 언어 문법을 사용했다고해서 자동적으로 객체지향 프로그래밍과 객체지향 설계가 적용됬다고 볼 수는 없다.<br> 책임과 역할이 각기 다른 코드를 한 클래스에 몰아넣어 덩치큰 만능 클래스를 만들고 상속과 다형성의 적용이 아닌 if/switch문으로 가득 설계된 오브젝트라면 POJO라고 부르기 힘들다.
* POJO의 예시
```java
public class User {
	
	private String userName;
	private String userPassword;
	
	public String getUserName() {
		return userName;
	}
	
	public void setUserName(String userName) {
		this.userName = userName;
	}
		
	public String getUserPassword() {
		return userPassword;
	}
	
	public void setUserPassword(String userPassword) {
		this.userPassword = userPassword;
	}

	
}
``` 
위 객체는 기본적인 자바 기능인 getter, setter 기능만 가지고 있다.<br>
특정 기술에 종속되어 있지 않은 순수 자바 객체이기 때문에 위 객체는 POJO라고 할 수 있다.
* POJO는 다음과 같은 행동을 해서는 안된다

미리 정의된 클래스의 확장. 예:
```java
public class Foo extends javax.servlet.http.HttpServlet { ...
``` 
미리 정의된 인터페이스의 구현. 예:
```java
public class Bar implements javax.ejb.EntityBean { ...
``` 
미리 정의된 애너테이션을 포함. 예:
```java
@javax.persistence.Entity public class Baz { ...
``` 


<br>

[참조1](https://ko.wikipedia.org/wiki/Plain_Old_Java_Object#cite_note-1) - Plain Old Java Object / wikipedia <br>[참조2](https://siyoon210.tistory.com/120) - POJO - (Plain Old Java Object)란 뭘까? / siyoon210  <br>[참조3](https://doing7.tistory.com/81) - POJO란? / DOing