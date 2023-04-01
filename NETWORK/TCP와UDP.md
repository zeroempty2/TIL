## TCP(Transmission Control Protocol)
> TCP는 신뢰성 있는 데이터 전송을 지원하는 연결 지향형 프로토콜이다. 일반적으로 TCP와 IP가 함께 사용되는데, IP가 데이터의 전송을 처리한다면 TCP는 패킷 추적 및 관리를 하게 된다. <br> 연결 지향형인 TCP는 3-way handshaking이라는 과정을 통해 연결 후 통신을 시작하는데, 흐름 제어와 혼잡 제어를 지원하며 **데이터의 순서를 보장한다**.

* 흐름 제어: 보내는 측과 받는 측의 데이터 처리속도 차이를 조절해주는 것
* 혼잡 제어: 네트워크 내의 패킷 수가 넘치게 증가하지 않도록 방지하는 것
<br>

## ▶️ TCP의 특징
* 연결 지향 방식이다.<br>
* 3-way handshaking과정을 통해 연결을 설정하고 4-way handshaking을 통해 해제한다.<br>
* 흐름 제어 및 혼잡 제어.<br>
* 높은 신뢰성을 보장한다.<br>
* UDP보다 속도가 느리다.<br>
* 전이중(Full-Duplex), 점대점(Point to Point) 방식.<br>
    * 전이중(Full-Duplex) : 전송이 양방향으로 동시에 일어날 수 있다.
    * 점대점(Point to Point) : 각 연결이 정확히 2개의 종단점을 가지고 있다.
* **TCP는 연속성보다 신뢰성있는 전송이 중요할 때에 사용하는 프로토콜**


<br>

## UDP(User Datagram Protocol)
> UDP는 비연결형 프로토콜로써, 인터넷상에서 서로 정보를 주고받을 때 정보를 보낸다는 신호나 받는다는 신호 절차를 거치지 않고 보내는 쪽에서 일방적으로 데이터를 전달하는 통신 프로토콜이다. TCP와는 다르게 연결 설정이 없으며, 혼잡 제어를 하지 않기 때문에 TCP보다 전송 속도가 빠르다. 그러나 **데이터 전송에 대한 보장을 하지 않기 때문에 패킷 손실이 발생할 수 있다**.

## ▶️ UDP의 특징
* 비연결형 서비스로 데이터그램 방식을 제공한다.<br>
* 정보를 주고 받을 때 정보를 보내거나 받는다는 신호절차를 거치지 않는다.<br>
* UDP헤더의 CheckSum 필드를 통해 최소한의 오류만 검출한다.<br>
* 신뢰성이 낮다.<br>
* TCP보다 속도가 빠르다.<br>
* **UDP는 신뢰성보다는 연속성 있는 전송이 필요할 때 사용하는 프로토콜**<br>


<br>

## TCP(Transmission Control Protocol)와 UDP(User Datagram Protocol)의 차이
|TCP(Transfer Control Protocol)|UDP(User Datagram Protocol)|
|:---:|:---:|
|연결형 프로토콜|비연결형 프로토콜|
|데이터의 경계를 구분하지 않음|데이터의 경계를 구분함|
|신뢰성있는 데이터 전송 (데이터 재전송 존재O)|비신뢰성 데이터 전송 (데이터 재전송 존재X)|
|일 대 일(Unicast) 통신|일 대 일, 일 대 다(Broadcast), 다 대 다(Multicast) 통신|


<br>

[참조1](https://mangkyu.tistory.com/15) - TCP와 UDP의 특징과 차이 / 망나니개발자 <br>[참조2](https://cocoon1787.tistory.com/757) - TCP와 UDP의 특징과 차이점 / 코딩 공부 일지 <br>[참조3](https://dev-coco.tistory.com/144) - TCP와 UDP의 특징 및 차이점 알아보기 / coco3o
