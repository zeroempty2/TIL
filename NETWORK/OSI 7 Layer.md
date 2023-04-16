## OSI 7 계층
>OSI 7 계층은 네트워크에서 통신이 일어나는 과정을 7단계로 나눈 것을 말한다.<br>
계층을 나눈 이유는 통신이 일어나는 과정이 단계별로 파악할 수 있기 때문이다.<br>
흐름을 한눈에 알아보기 쉽고, 사람들이 이해하기 쉽고,
7단계 중 특정한 곳에 이상이 생기면 다른 단계의 장비 및 소프트웨어를 건들이지 않고도 이상이 생긴 단계만 고칠 수 있기 때문이다.<br>

<br>

## ▶️ OSI 7 계층(Layer) 이란?
1984년 국제표준화기구(ISO)에서 개발한 모델로써, 네트워크 프로토콜 디자인과 통신 과정을 7개의 계층으로
구분하여 만든 "표준 규격"이다.<br> 초창기의 네트워크는 각 컴퓨터마다 시스템이 달랐기 때문에 하드웨어와
소프트웨어의 논리적인 변경 없이 통신할 수 있는 표준 모델이 나타나게 되었다.<br>
통신이 일어나는 과정을 7단계로 크게 구분하여, 단계별로 파악이 가능하다.<br>
컴퓨팅 장치나 네트워킹 장치를 만들 때 이 모델을 참조해서 모든 통신 장치를 만든다.<br>
각 계층은 독립적인 모듈로 구성되어 있다.<br>
각 계층은 상하 계급 구조를 가지고 있다.<br>
상위 계층의 프로토콜이 제대로 동작하기 위해서는 하위의 모든 계층에 문제가 없어야 한다.<br>
물리 계층 : 하드웨어 /  데이터링크 계층 : 하드웨어 + 소프트웨어 / 3 계층부터는 소프트웨어로 구성<br>
![image](https://user-images.githubusercontent.com/117061586/232315122-9dba849a-3ed0-425e-993a-87387d405115.png)<br>
[이미지 출처] - '데이터 통신', 오창환 저, 한국 학술정보(주)


<br>

## 1 계층 : 물리 계층(Physical Layer)
![image](https://user-images.githubusercontent.com/117061586/232315233-5608be0f-6540-452d-ab0f-ef00cc114d8a.png)<br>
[이미지 출처 - OSI 7 계층 (OSI 7 Layer) / 무작정 개발](https://backendcode.tistory.com/167)<br>
* 주로 전기적, 기계적, 기능적인 특성을 이용해서 통신 케이블로 데이터를 전송하는 물리적인 장비<br>
* 단지 데이터 전기적인 신호(0,1)로 변환해서 주고받는 기능만 할 뿐<br>
* 이 계층에서 사용되는 통신 단위 : 비트(Bit)이며 이것은 1과 0으로 나타내어지는, 즉 전기적으로 On, Off 상태<br>
* 장비 : 통신 케이블, 리피터, 허브 등<br>


<br>

## 2 계층 : 데이터 링크 계층(DataLink Layer)
![image](https://user-images.githubusercontent.com/117061586/232315353-1fa0dbf6-c462-4d08-8d3c-56e19c8d4e12.png)<br>
[이미지 출처 - OSI 7 계층 (OSI 7 Layer) / 무작정 개발](https://backendcode.tistory.com/167)<br>
* 물리계층을 통해 송수신되는 정보의 오류와 흐름을 관리하여 안전한통신의 흐름을 관리<br>
* 프레임에 물리적 주소(MAC address)를 부여하고 에러검출, 재전송, 흐름제어를 수행<br>
* 이 계층에서 전송되는 단위 : 프레임(Frame)<br>
* 장비 : 브리지, 스위치, 이더넷 등(여기서 MAC주소를 사용)<br>
-> 브릿지나 스위치를 통해 맥주소를 가지고 물리계층에서 받은 정보를 전달함.<br>


<br>

## 3 계층 : 네트워크 계층(Network Layer)
![image](https://user-images.githubusercontent.com/117061586/232315540-02edb32a-98d5-47f0-bd1d-bf894f29d06f.png)<br>
[이미지 출처 - OSI 7 계층 (OSI 7 Layer) / 무작정 개발](https://backendcode.tistory.com/167)<br>
* 데이터를 목적지까지 가장 안전하고 빠르게 전달<br>
* 라우터(Router)를 통해 경로를 선택하고 주소를 정하고(IP) 경로(Route)에 따라 패킷을 전달 > IP 헤더 붙음<br>
* 이 계층에서 전송되는 단위 : 패킷(Packet)<br>
* 장비 : 라우터<br>


<br>

## 4 계층 : 전송 계층(Transport Layer)
![image](https://user-images.githubusercontent.com/117061586/232315660-43f5fd4c-dd92-4ad6-a26b-971f85693043.png)<br>
[이미지 출처 - OSI 7 계층 (OSI 7 Layer) / 무작정 개발](https://backendcode.tistory.com/167)<br>
* port 번호, 전송방식(TCP/UDP) 결정 > TCP 헤더 붙음<br>
    * TCP : 신뢰성, 연결지향적<br>
    * UDP : 비신뢰성, 비연결성, 실시간<br>
* 두 지점간의 신뢰성 있는 데이터를 주고 받게 해주는 역할<br>
* 신호를 분산하고 다시 합치는 과정을 통해서 에러와 경로를 제어<br>


<br>

## 5 계층 : 세션 계층(Session Layer)
![image](https://user-images.githubusercontent.com/117061586/232315716-410d18a5-39cf-4789-8894-26bc0fb987e8.png)<br>
[이미지 출처 - OSI 7 계층 (OSI 7 Layer) / 무작정 개발](https://backendcode.tistory.com/167)<br>
* 주 지점간의 프로세스 및 통신하는 호스트 간의 연결 유지<br>
* TCP/IP 세션 체결, 포트번호를 기반으로 통신 세션 구성<br>
* 세션 생성, 유지, 종료, 전송 중단 시 복구 기능 수행 (OS가 세션 계층으로 이 역할 수행)<br>
* 프로토콜(Protocol) : NetBIOS, SSH, TLS<br>
* API, Socket<br>

<br>

## 6 계층 : 표현 계층(Presentation Layer)
![image](https://user-images.githubusercontent.com/117061586/232315850-30bdb161-cd50-4356-8992-d7692262bee2.png)<br>
[이미지 출처 - OSI 7 계층 (OSI 7 Layer) / 무작정 개발](https://backendcode.tistory.com/167)<br>
* 전송하는 데이터의 표현방식을 결정(ex. 데이터변환, 압축, 암호화 등)<br>
* 파일인코딩, 명령어를 포장, 압축, 암호화<br>
* JPEF, MPEG, GIF, ASCII 등<br>


<br>

## 7 계층 : 응용 계층(Application Layer)
![image](https://user-images.githubusercontent.com/117061586/232315905-b9d69f34-0e51-4d3f-a043-11044fb7f250.png)<br>
[이미지 출처 - OSI 7 계층 (OSI 7 Layer) / 무작정 개발](https://backendcode.tistory.com/167)<br>
* 최종 목적지로, 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행(ex. explore, chrome 등)<br>
* HTTP, FTP, SMTP, POP3, IMAP, Telnet 등과 같은 프로토콜이 있다<br>
* 사용자와 직접 접하는 유일한 계층<br>
    * 사용자로부터 정보를 입력받아 하위 계층으로 전달하고, 하위 계층에서 전송한 데이터를 사용자에게 전달<br>
    * UI 부분, I/O부분<br>

<br>

## ▶️ 출처 및 참조
[참조1](https://shlee0882.tistory.com/110) - OSI 7 계층이란?, OSI 7 계층을 나눈 이유 / effortDev <br>
[참조2](https://lxxyeon.tistory.com/155) -  OSI 7계층이란? - OSI 계층별 특징, TCP/IP 4계층 / 테크연<br>
[참조3](https://backendcode.tistory.com/167) - OSI 7 계층 (OSI 7 Layer) / 무작정 개발