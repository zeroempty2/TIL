## MSA(MicroService Architecture)
> MicroService Architecture는 이름에서부터 알수있듯이, 작은 서비스 여러개가 모여서 하나의 시스템을 제공하는 아키텍처를 뜻한다. <br> 
MicroService Architecture에서 각 서비스는 작고 독립적이며 느슨하게 결합되어 있기 때문에 서비스들을 독립적으로 배포할 수 있고, 전체 프로그램을 빌드한 뒤에 재배치하지 않고도 기존 서비스들을 업데이트 할 수 있다.

<br>

## ▶️ MSA(MicroService Architecture)란?
* 단일 실행이 가능한 작은 서비스들(각각의 서비스는 모놀리틱 아키텍쳐와 유사한 구조)의 모음
* 각각의 서비스는 독립적으로 배포가 가능해야함
<br>

## ▶️ MSA의 장단점
* 장점 
  * 서비스 별 개별 배포 가능(전체프로그램을 다시 배포하지 않고도 업데이트가 가능)
  * 장애가 전체 서비스로 확장될 가능성이 적음(서비스 하나가 다운되더라도 전체 서비스에 영향을 끼치지 않음)
  * 서비스의 확장이 용이하다(서비스들이 독립적이기 때문에)
  * 서비스들이 독립적이라는 특징덕에 클라우드, 컨테이너와 잘 어울리는 아키텍처이다.

* 단점 
  * 서비스 간 호출 시 API를 사용하기 때문에, 통신 비용이 증가함
  * 서비스가 분리되어 있기 때문에 서비스끼리의 테스트나 트랜잭션이 복잡함
  * 데이터가 여러 서비스에 걸쳐 분산되기 때문에 한번에 조회하기 어렵고, 데이터의 정합성 또한 관리하기 어려윰
  * 독립된 구조로 인해 통합적인 유지관리가 어려워질 수 있음
<br>

[참조1](https://velog.io/@tedigom/MSA-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-1-MSA%EC%9D%98-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90-3sk28yrv0e),[참조2](https://martinfowler.com/articles/microservices.html),[참조3](https://gruuuuu.github.io/cloud/architecture-microservice/)