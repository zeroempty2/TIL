## DI
* 각 계층 사이, 각 클래스 사이에 필요로하는 의존 관계를 컨테이너가 자동으로 연결해주는것
* 각 클래스의 사이의 의존 관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는 것

### @Autowired Injection    

```java
@Service
@Transactional
public class AccountService {
    @Autowired
    private AccountRepository accountRepository;
}
```

* `@Autowired` 어노테이션을 사용해서 의존성 주입을 한다.
* **순환 참조 의존성을 방지 할 수 있다.**
* POJO 스럽지 않고 테스트 코드 작성시 의존성 주입을 변경해서 진행하기 힘들다

#### 동작 원리
@Autowried를 의존성에 사용하면, 애플리케이션 콘텍스트는 일치하는 의존성을 검색한다. 기본적으로 오토와이어되는 모든 의존성이 필요하다 

* 일치하는 항목이 1개 있다: 찾고 있는 의존성 주입
* 일치하는 항목이 2개 이상 발견됐다 : 오토와이어링 실패
* 일치하는 항목이 없다 : 오토와이어링 실패
  
둘 이상의 후보가 발견된 경우에는 두 가지 방법으로 해결 할 수 있다.
* 후보 중 하나만 사용하려면 @Primary 어노테이션을 사용하라
  * 후보가 둘 이상 있을 때 @Primary 어노테이션을 사용한 빈이 호출 된다.
* 오토와이어링을 더욱 강화하려면 @Qualifier를 사용하라
  * @Primary 반대로 내가 주입 받고싶은 객체에 @Autowired 어노테이션과 함께 @Qualifier("xxx")을 사용하면 한정자를 가진 xxx가 주입된다.
  * 빈으로 등록시킬 @Component 어노테이션과 함께 @Qualifier("xxx")를 함께 작성해야한다.


### Setter Injection
```java
@Service
@Transactional
public class AccountService {
    private AccountRepository accountRepository;

    @Autowired
    public void setAccountRepository(AccountRepository accountRepository) {
        this.accountRepository = accountRepository;
    }
}
```

* 인자가 없는 생성자나 인자가 없는 static factory 메서드가 bean을 인스턴스화 하기 위하여 호출된 bean 의 setter 메서드를 호출하여 실체화하는 방법
* 세터를 생성 후 의존성 삽입 방식이기에 구현시에 조금더 유연할 수 있다.
* 순환 참조 의존성을 발생할 수 있다.
* **immutable 객체가 아니기 때문에 실수할 수 있는 확률이 높다.**

### Constructor Injection

```java
@Service
@Transactional
public class AccountService {
    private final AccountRepository accountRepository;

    public AccountService(AccountRepository accountRepository) {
        this.accountRepository = accountRepository;
    }
}
```
* 생성자를 이용하여 클래스 사이의 의존 관계를 연결
* 생성자 파라미터를 지정함으로써 생성하고자하는 객체가 불필요 하는 것을 명확하게 알 수 있다.
* **Setter 메서드를 제공하지 않음으로 간단하게 필드를 불변 값으로 지정할 수 있다.**
* **가장 POJO 스럽다**
  * `final` 키워드로 해당 객체가 반드시 외부에서 주입 받는다는 것을 잘표시해준다
* 코드량이 많다
  * Lombok의 `@RequiredArgsConstructor`등을 활용하면 해결 가능