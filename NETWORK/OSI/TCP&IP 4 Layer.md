## TCP/IP 4 계층
>TCP/IP 4 계층은 실제 사용되는 TCP/IP는 OSI 참조 모델을 기반으로 상업적이고 실무적으로 이용될 수 있도록 단순화된 모형이다.<br>
네트워크 전송 시 데이터 표준을 정리한 것이 OSI 7계층, 이 이론을 실제 사용하는 인터넷 표준이 TCP/IP 4계층이다.<br>
OSI 7계층을 4-5계층으로 분류하여 적용할 수 있다.<br>
![image](https://user-images.githubusercontent.com/117061586/232484446-9500f5f0-71bc-47fe-9841-4f36255a90db.png)<br>
[이미지 출처 - TCP/IP 4계층 / joeyful.log](https://velog.io/@jehjong/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EC%9D%B8%ED%84%B0%EB%B7%B0-TCPIP-4%EA%B3%84%EC%B8%B5)<br>

<br>

## ▶️ IP (인터넷 프로토콜)란?
IP는, 패킷 데이터들을 최대한 빨리 특정 목적지 주소로 보내는 프로토콜이다.<br>
빨리 보내는게 목적이기 때문에, 패킷 전달 여부를 보증하지 않으며, 패킷을 보낸 순서와 받는 순서가 다를 수 있다.<br>


<br>

## ▶️ TCP (전송 제어 프로토콜)란?
패킷 통신은, 데이터를 작은 단위로 나누어 전송하기 때문에, 순서가 뒤섞이거나 내용이 유실될 수 있다는 단점이 있다.<br>
따라서, 이러한 문제를 해결하기 위해 TCP 라는 프로토콜이 존재한다.<br>
TCP는 패킷 데이터를 꼼꼼하게 보내는게 목적이기 때문에, IP 보다 패킷 전송 속도는 느리지만, 패킷 전달 여부를 보증하고, 패킷을 송신 순서대로 받게 해준다.<br>
즉, 목적지에 도착한 패킷들을 순서대로 정렬하고, 손상되거나 손실된 패킷이 있다면, 출발지에 재요청하는 방식으로 진행된다.<br>
TCP는 데이터를 상대방에게 확실하게 보내기 위해서 3 way 핸드쉐이킹이라는 방법을 사용하고 있다.<br>
이 방법은 패킷을 보내고 잘 보내졌는지 여부를 상대에게 확인하러 간다.<br>
여기에서 고유의 'SYN'와 'ACK'라는 TCP 플래그를 사용한다.<br>


<br>

## ▶️ TCP 3 way handshake
TCP는 연결지향형 프로토콜이기 때문에, 송신측과 수신측이 서로 연결되는 작업이 필요하다.<br>
3 way handshake는 본격적으로 상대 클라이언트와 연결되기 전에 가상 연결을 하고 패킷을 보내서 확인하는 동작이다.<br>
3 Way Handshaking 은 SYN(접속요청) 과 ACK(승인) 로 진행된다.<br>

<br>

1. 먼저, 클라이언트는 서버에게, 접속을 요청하는 SYN 패킷을 보낸다.<br>
2. 서버는 SYN 패킷을 받고, 클라이언트에게 요청을 수락한다는 ACK 와 SYN 플래그가 설정된 패킷을 보낸다.<br>
3. 클라이언트는 다시 서버에게 ACK 패킷을 보낸다.<br>
4. 이제 3 Way Handshaking 으로 기기 간 연결이 성립되었으니, 데이터 통신이 가능해진다.<br>


<br>

## ▶️ TCP/IP 4계층의 캡슐화, 역캡슐화
TCP/IP 4계층은,  애플리케이션 계층, 전송 계층, 인터넷 계층, 네트워크 접근 계층으로 이루어져있다.<br>
데이터 전송 시, 데이터는 상위 계층에서 하위 계층으로 이동하고, 계층 이동 마다 필요한 정보(헤더)가 추가된다.<br>
이를, 캡슐화라고 한다.<br>
데이터 수신 시, 데이터는 하위 계층에서 상위 계층으로 이동하고, 계층 이동 마다 추가된 헤더를 읽고 알맞은 행동을 취한 후, 헤더를 제거한다.<br>
이를, 역캡슐화라고 한다.<br>
계층 별로 추가되는 헤더는 아래와 같다.<br>
![image](https://user-images.githubusercontent.com/117061586/232489678-3df3d08c-d411-4daa-857f-f4e985dd9c2a.png)<br>
[이미지 출처 - TCP/IP 와 TCP/IP 4계층이란? / 우노](https://velog.io/@jehjong/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EC%9D%B8%ED%84%B0%EB%B7%B0-TCPIP-4%EA%B3%84%EC%B8%B5)<br>


<br>

## 1계층 : 네트워크 액세스 계층(Network Access Layer or Network Interface Layer)
* 데이터를 전기신호로 변환한 뒤, 물리적 주소인 MAC 주소를 사용해, 알맞은 기기로 데이터를 전달하는 계층이다.<br>
* 프로토콜로는 Ethernet, Wi-Fi, PPP, Token Ring 과 같은 프로토콜이 사용된다.<br>


<br>

## 2계층 : 인터넷 계층(Internet Layer)
* 패킷을 최종 목적지까지 라우팅하는 계층이다.<br>
* 프로토콜로는 IP, ARP, ICMP, RARP, OSPF 가 사용된다.<br>


<br>

## 3계층 : 전송 계층(Transport Layer)
* 통신 노드 간 신뢰성 있는 데이터 전송을 보장하는 계층이다.<br>
    * 역캡슐화 과정에서, 포트 번호를 사용해 데이터를 정확한 애플리케이션에 전달하는 역할도 한다.<br>
    * 네트워크 액세스 계층과 인터넷 계층을 통해, 데이터가 목적지 기기까지 정상적으로 도착했다면, 전송 계층은 포트 번호를 사용해, 데이터를 목적지 기기 내 적절한 에플리케이션으로 전달한다.<br>
* 프로토콜로는 TCP, UDP, RTP, RTCP 가 있다.<br>


<br>

## 4계층 : 애플리케이션 계층(Application Layer)
* 사용자와 가장 가까운 계층으로, 사용자-소프트웨어 간 소통을 담당하는 계층이다.<br>
* 애플리케이션을 실행하기 위한 데이터 형식이 작성된다.<br>
*  프로토콜로는 HTTP, HTTPS, FTP, SSH, Telnet, DNS, SMTP 가 있다.<br>


<br>

## ▶️ 구글 연결 시나리오
* 만약, www.google.com 을 웹 브라우저에 입력한다면, 구글 웹서버에 80번 포트로 HTTP Request 를 보낸다는 의미와 동일하다.<br>

<br>

* 그리고, 구글 구글 웹 서버에 HTTP Request 를 보내기 위해선, 아래와 같이 각 계층에 필요한 정보들을 담은 패킷을 만들어야한다.<br>
![image](https://user-images.githubusercontent.com/117061586/232492460-79ee9efb-cded-4c1b-b4a9-858501588769.png)
[이미지 출처 - TCP/IP 와 TCP/IP 4계층이란? / 우노](https://velog.io/@jehjong/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EC%9D%B8%ED%84%B0%EB%B7%B0-TCPIP-4%EA%B3%84%EC%B8%B5)<br>

<br>

* 먼저, 패킷의 Application Layer 에는 HTTP Request 헤더가 들어간다. <br>

<br>

* 이후,Transport Layer 에는 TCP 헤더가 들어간다. <br>
    * TCP 헤더에서 중요하게 볼 것은 SP(출발지 포트번호)와 DP(목적지 포트번호)이다.<br>
    * 출발지 포트번호는 내 컴퓨터에서 만든 소켓의 포트 번호이므로, 내 컴퓨터는 알고 있으며, 목적지 포트 번호 또한 80으로 알고 있다.<br>

<br>

* 이후, Internet Layer 에는 IP 헤더가 들어간다.<br>
    * IP 헤더에서 중요하게 볼 것은 SA(출발지 IP주소) 와 DA(목적지 IP주소)이다.<br>
    * 현재, www.google.com 이라는 도메인 정보만 알고 있기 때문에 나의 시작 IP 주소는 알고 있지만, 목적지의 IP 주소는 아직 모른다.<br>
    * 따라서, 도메인 정보로 목적지의 IP 주소를 알아내기 위해, 도메인 서버에 DNS 쿼리를 보내고, IP 주소를 응답받는다.<br>

<br>

* 이후, Network Access Layer 에는 Ethernet 헤더가 들어간다.<br>
    * Ethernet 헤더에서 중요하게 볼 것은 SA(출발지 MAC 주소)와 DA(목적지 MAC 주소)이다.<br>
    * 여기서 목적지 MAC 주소는, 구글의 MAC 주소가 아닌, 물리적으로 연결된, 패킷이 전달될 라우터(예를 들어, 공유기) 또는 게이트웨이의 MAC 주소를 의미한다.<br>
    * 따라서, 라우터의 MAC 주소를 알아내기 위해, ARP 프로토콜을 사용한다.<br>

<br>

* 이후 패킷을 전송하기 전, TCP는 연결지향형 프로토콜이기 때문에, 송신측과 수신측이 서로 연결되는 작업인 3 Way Handshaking을 수행한다.<br>

<br>

* 3 Way Handshaking을 통해 연결이 되었으면, 라우팅을 통해 패킷을 목적지 서버에게 전송한다.<br>
    * 패킷은 Network Access Layer의 MAC 주소와 Internet Layer의 IP 주소로 라우팅을 반복해 목적지 구글 서버까지 도착한다.<br>
    * 먼저, 구글 서버가 받은 패킷 내부 Transport Layer의 목적지 포트 번호에는 80번이 적혀져있다.<br>
    * 따라서, Transport Layer는 80번 포트를 사용하고 있는 Application Layer에 데이터를 전송한다.<br>
    * 이후, Application Layer는 HTTP Request 데이터를 받아, “/” 에 매핑된 GET 요청을 처리한다.<br>
    * 이후, 적절한 HTML을 클라이언트에게 응답한다.<br>
    * 따라서, 클라이언트는 라우팅을 통해 전달 받은, “www.google.com” 에 해당하는 HTML 을 브라우저에 띄우게 된다.<br>

<br>

* HTTP 요청 및 응답 과정이 끝났으므로, 연결을 종료한다.<br>
    * 여기서도 TCP의 컨트롤 비트가 사용되며, 해당 단계에서는 ACK, FIN 플래그가 사용된다.<br>
    * 클라이언트와 서버의 연결 종료 작업을 4 Way Handshaking 이라고 부르며, 총 4단계로 진행된다. <br>
    * 먼저, 클라이언트는 서버에게, 연결을 종료하겠다는 의미인 FIN 패킷을 전송한다.<br>
    * 서버는 클라이언트에게 ACK 패킷을 보내고, 클라이언트가 보냈던 요청들에 대해 마저 응답을 보낸다. <br>
    * 이후, 서버의 응답이 끝나면 클라이언트에게 FIN 패킷을 전송한다.<br>
    * 클라이언트는 서버의 통신 종료를 확인한 뒤, 서버에게 ACK 패킷을 전송하고, 연결이 종료된다.<br>
    * 하지만, 서버가 클라이언트에게 FIN 을 보내는 과정에서 한가지 문제가 발생할 수 있다. <br>
    * 서버가 클라이언트에게 FIN 을 보내기 전에, 이전에 서버가 클라이언트에게 응답 했던 패킷이 FIN 보다 늦게 도착할 수도 있고, 그렇게 되면, 클라이언트가 서버의 일부 응답을 받지 못하게 된다.<br>
    * 따라서, 클라이언트는 서버로부터 FIN 패킷을 받고, ACK 패킷을 보낸 뒤에도 일정 시간동안 혹시나 아직 도착하지 않은 잉여 패킷을 기다린다.<br>
    * 이렇게, 4 Way handshaking 이후에도 소켓을 닫지 않고 잉여패킷을 기다리는 상태를, TIME_WAIT 이라고 한다.<br>


<br>

## 구글 연결 시나리오 요약
* www.google.com 을 브라우저 주소창에 입력한다.<br>
* 보낼 패킷의 HTTP 헤더는, HTTP Request 를 통해 채워진 상태이다.<br>
* 보낼 패킷의 IP 헤더를 채우기 위해, DNS 서버를 통해 www.google.com 도메인의 IP 주소를 응답 받는다.<br>
* 보낼 패킷의 TCP 헤더를 채우기 위해, 클라이언트와 구글 웹서버 간 TCP 연결을 한다.(3-Way Handshaking)<br>
* 보낼 패킷이 완성되었으므로, www.google.com 에 패킷을 전송하고, HTML 을 응답받는다.<br>
* 클라이언트는 응답 받은 HTML 을 브라우저에 띄운다.<br>
* 클라이언트와 구글 웹서버간 TCP 연결을 종료합니다.(4-Way Handshaking)<br>


<br>


## ▶️ 출처 및 참조
[참조1](https://velog.io/@jehjong/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EC%9D%B8%ED%84%B0%EB%B7%B0-TCPIP-4%EA%B3%84%EC%B8%B5) - TCP/IP 4계층 / joeyful.log <br>
[참조2](https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-TCP-IP-%EC%A0%95%EB%A6%AC-%F0%9F%91%AB%F0%9F%8F%BD-TCP-IP-4%EA%B3%84%EC%B8%B5) - TCP / IP 4계층 모델 - 핵심 총정리 / Inpa Dev<br>
[참조3](https://wooono.tistory.com/507) - TCP/IP 와 TCP/IP 4계층이란? / 우노
