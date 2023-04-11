## REST
>REST란, HTTP를 잘사용하기 위한 아키텍쳐 스타일 이다.<br>
REST는 URI와 HTTP 메소드를 사용해서 자원과 행위를 표현한다.<br>
REST의 원칙을 지키면서 API의 의미를 표현하고 쉽고, 파악하기 쉽게 하는것을 Restful 하다고 한다.<br>

<br>

## ▶️ REST 구성 요소
REST는 다음과 같은 3가지로 구성이 되어있다. <br>
자원(Resource) : HTTP URI<br>
자원에 대한 행위(Verb) : HTTP Method<br>
자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load<br>


<br>

## REST API
> REST한 방식으로 데이터를 상호교환하게 설계된 API를 말한다.  이걸 풀어말하면<br>
 HTTP를 잘사용하기위해, URI와 HTTP메소드를 사용해서, URL로 어떤 자원에 접근할 것인지, 메소드로 어떤 행위를 할것인지 표현하여 설계된 API를 말한다.

<br>

## ▶️ REST 제약조건
로이필딩이 말하는 진정한 REST API 는 REST 의 제약조건을 모두 준수하는 것 이다.<br>

1. Client - Server<br>
    * Client-Server 제약조건이란, API를 통해 정보를 교환하는 주체는, 클라이언트와 서버 구조를 가져야한다.<br> 
    * 클라이언트와 서버를 분리함으로써, 서로 의존하지 않는 구조를 가져야한다.<br> 
2. Stateless<br> 
    * 무상태성 (서로의 상태를 기억하지 않는다.)<br> 
    * 클라이언트에서 서버로의 요청에는 그 요청을 이해하는 데 필요한 모든 정보가 포함되어있어야 한다.<br> 
    * 클라이언트와 서버 모두, 통신하는 상대의 상태를 저장하고 있지 않아야 한다.<br> 
    * 요청과 응답이 들어올 때 마다, 상대가 누구인지 파악할 수 있어야한다.<br> 
3. 캐시처리 가능 여부<br> 
    * 요청에 대한 응답 내의 데이터에 캐시 가능여부가 명시되어 있어야함을 의미한다.<br> 
    * 📌 cache-control 헤더를 통해 명시 가능<br> 
4. Uniform Interface<br> 
    * 전체 시스템을 파악할 수 있는 인터페이스를 제공해야한다.<br> 
    * 전체적인 시스템 아키텍처를 간단하고 잘 파악할 수 있도록 약속된 인터페이스를 제공해야한다.<br> 
    * 이 인터페이스를 일반화 시킴으로써, 클라이언트 - 서버간의 결합도를 낮출 수 있다.<br> 
5. Layered System<br> 
    * 계층화 시스템<br> 
    * 클라이언트는 서버에 직접 연결되었는지, 중간 서버를 통해 연결되었는지 알 수 없어야함을 의미한다.<br> 
6.  Code-On-Demand (Optional)<br> 
    * Server 에서 보낸 코드를 Client에서 실행할 수 있어야함을 의미한다. (ex - Java Script)<br> 
    * 선택적인 조건 사항이라 논문에 언급되며 필요에 따라, 지켜도되고, 지키지않아도 REST에는 문제가 없다고 이야기한다.

<br>

## ▶️ REST API의 장점
REST API의 장점은<br>

1. 보기 좋다.<br> 
    * URL만 보고 어떤 자원에 접근할 것인지, 메소드를 보고 어떤 행위를 할지 알 수 있기 때문에, 개발을 할때 용이하다.<br> 
2. 자원을 아낄 수 있다.<br> 
    * 1개의 URI로 4개의 행위(CRUD)를 명시할 수 있기 때문에, 굉장히 효율적이다.<br> 
3. stateless한 상태를 유지할  수 있다.<br> 
    * REST API의 가장 큰 특징으로, 다양한 브라우저와 모바일에서 통신할 수 있도록 한다.<br> 
    * 클라이언트가 서버에 종속적이지 않아도 되기때문에, scale out한 상황에서도 용이하다.<br> 

<br>

## ▶️ 참조
[참조1](https://thalals.tistory.com/284) - Rest API / Restful API 란 무엇인가요 / 힘차게, 열심히 공대생 <br>
[참조2](https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80) -  REST API란? REST, RESTful이란? / 하진쓰의 서버사이드 기술 블로그<br>
[참조3](https://thalals.tistory.com/335) -  진짜 Rest API 란 무엇이고 어떻게 써야하는 걸까? / 힘차게, 열심히 공대생