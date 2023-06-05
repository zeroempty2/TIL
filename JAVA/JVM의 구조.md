## JVM이란?
> JVM은 Java Virtual Machine의 약자로, 자바 가상 머신이라고 부른다.<br>
자바와 운영체제 사이에서 중개자 역할을 수행하며, 자바가 운영체제에 구애 받지 않고 프로그램을 실행할 수 있도록 도와준다.<br>
 또한, 가비지 컬렉터를 사용한 메모리 관리도 자동으로 수행하며, 다른 하드웨어와 다르게 레지스터 기반이 아닌 스택 기반으로 동작한다.<br>

<br>

## ▶️ JVM의 동작방식
![image](https://github.com/zeroempty2/TIL/assets/117061586/187332f6-5ba5-4bee-acde-173de4054dea)<br>
[출처 - Comparison of garbage collectors in Java programming language/ Hrvoje Grgic,Branko Mihaljevic,Aleksander Radovan](https://www.researchgate.net/figure/Visual-representation-of-the-Java-Virtual-Machine-with-key-memory-components-bolded_fig1_326701102)<br>

1. 자바 프로그램을 실행하면 JVM은 OS로부터 메모리를 할당받는다.<br>
2. 자바 컴파일러(javac)가 자바 소스코드(.java)를 자바 바이트 코드(.class)로 컴파일 한다.<br>
3. Class Loader는 동적 로딩을 통해 필요한 클래스들을 로딩 및 링크 하여 Runtime Data Area(실질적인 메모리를 할당 받아 관리하는 영역)에 올린다.<br>
4. Runtime Data Area에 로딩 된 바이트 코드는 Execution Engine을 통해 해석된다.<br>
5. 해석된 바이트 코드는 Runtime Data Area의 각 영역에 배치되어 수행하며 이 과정에서 Execution Engine에 의해 GC의 작동과 스레드 동기화가 이루어진다.<br>



## ▶️ 클래스 로더(Class Loader)

자바는 동적으로 클래스를 읽어오므로, 프로그램이 실행 중인 런타임에서야 모든 코드가 자바 가상 머신과 연결된다. 이렇게 동적으로 클래스를 로딩해주는 역할을 하는 것이 바로 클래스 로더(class loader)이다. <br>
자바에서 소스를 작성하면 .java파일이 생성되고 .java소스를 컴파일러가 컴파일하면 .class파일이 생성되는데 클래스 로더는 .class 파일을 묶어서 JVM이 운영체제로부터 할당받은 메모리 영역인 Runtime Data Area로 적재한다.<br>
클래스 파일의 로딩 순서는 다음과 같이 3단계로 구성된다. (Loading → Linking → Initialization)<br>
1. Loading(로드) : 클래스 파일을 가져와서 JVM의 메모리에 로드한다.<br>
2. Linking(링크) : 클래스 파일을 사용하기 위해 검증하는 과정이다.<br>
    * Verifying(검증) : 읽어들인 클래스가 JVM 명세에 명시된 대로 구성되어 있는지 검사한다.<br>
    * preparing(준비) : 클래스가 필요로 하는 메모리를 할당한다.<br>
    * Resolving(분석) : 클래스의 상수 풀 내 모든 심볼릭 레퍼런스를 다이렉트 레퍼런스로 변경한다.<br>
3. Initialization(초기화) : 클래스 변수들을 적절한 값으로 초기화한다. ( static 필드들을 설정된 값으로 초기화 등 )<br>

<br>

## ▶️ 실행 엔진(Execution Engine)
실행 엔진은 클래스 로더를 통해 런타임 데이터 영역에 배치된 바이트 코드를 명령어 단위로 읽어서 실행한다<br>
자바 바이트 코드(*.class)는 기계가 바로 수행할 수 있는 언어보다는 가상머신이 이해할 수 있는 중간 레벨로 컴파일 된 코드이다. 그래서 실행 엔진은 이와 같은 바이트 코드를 실제로 JVM 내부에서 기계가 실행할 수 있는 형태로 변경해준다.<br>
이 수행 과정에서 실행 엔진은 인터프리터와 JIT 컴파일러 두 가지 방식을 혼합하여 바이트 코드를 실행한다.<br>

## ▶️ 가비지 컬렉터 (Garbage Collector ,GC)
자바 가상 머신은 가비지 컬렉터(garbage collector)를 이용하여 Heap 메모리 영역에서 더는 사용하지 않는 메모리를 자동으로 회수해 준다.<br>
C언어 같은 경우 직접 개발자가 메모리를 해제해줘야 되지만, JAVA는 이 가비지 컬렉터를 이용해 자동으로 메모리를 실시간 최적화 시켜준다. 따라서 개발자가 따로 메모리를 관리하지 않아도 되므로, 더욱 손쉽게 프로그래밍을 할 수 있도록 해준다.<br>
일반적으로 자동으로 실행되지만, 단 GC(가비지 컬렉터) 가 실행되는 시간은 정해져 있지 않다.<br>
특히 Full GC 가 발생하는 경우, GC 를 제외한 모든 스레드가 중지되기 때문에 장애가 발생할 수 있다.<br>

<br>

## ▶️ 런타임 데이터 영역 (Runtime Data Area) 
![image](https://github.com/zeroempty2/TIL/assets/117061586/5a2ee601-ca43-475e-8fb6-c1a8d40915ff)<br>
[출처 - 자바 JVM 내부 구조와 메모리 구조에 대하여/코딩팩토리](https://coding-factory.tistory.com/828)<br>
런타임 데이터 영역은 JVM의 메모리 영역으로 자바 애플리케이션을 실행할 때 사용되는 데이터들을 적재하는 영역이다.

* 모든 스레드가 공유해서 사용 (GC의 대상)<br>
힙 영역 (Heap Area)<br>
메서드 영역(Method Area)<br>
 
* 스레드(Thread) 마다 하나씩 생성<br>
스택 영역(Stack Area)<br>
PC 레지스터 (PC Register)<br>
네이티브 메서드 스택(Native Method Stack)<br>

<br>

## 메서드 영역 (Method Area)
메서드 영역은 JVM이 시작될 때 생성되는 공간으로 바이트 코드(.class)를 처음 메모리 공간에 올릴 때 초기화되는 대상을 저장하기 위한 메모리 공간이다.<br>
JVM이 동작하고 클래스가 로드될 때 적재되서 프로그램이 종료될 때까지 저장 된다.<br>
모든 쓰레드가 공유하는 영역이라 다음과 같이 초기화 코드 정보들이 저장되게 된다.<br>
* Field Info : 멤버 변수의 이름, 데이터 타입, 접근 제어자의 정보<br>
* Method Info : 메소드 이름, return 타입, 함수 매개변수, 접근 제어자의 정보<br>
* Type Info : Class 인지 Interface 인지 여부 저장, Type의 속성, 이름 Super Class의 이름<br>

## 힙 영역 (Heap Area)
![image](https://github.com/zeroempty2/TIL/assets/117061586/1e8fd6b2-9720-4493-89ee-314de9e4474d)<br>
[출처 - 자바 JVM 내부 구조와 메모리 구조에 대하여/코딩팩토리](https://coding-factory.tistory.com/828)<br>
new 키워드로 생성된 객체와 배열이 생성되는 영역이다. <br>
주기적으로 GC가 제거하는 영역이다. <br>

Young Generation 영역은 자바 객체가 생성되자마자 저장되고, 생긴지 얼마 안되는 객체가 저장되는 공간이다. <br>
Heap 영역에 객체가 생성되면 최초로 Eden 영역에 할당되고, 이 영역에 데이터가 어느정도 쌓이게 되면 참조정도에 따라 Servivor의 빈 공간으로 이동되거나 회수된다. <br>
Young Generation(Eden+Servivor) 영역이 차게 되면 또 참조정도에 따라 Old영역으로 이동되거나, 회수된다. <br>
이렇게 Young Generation과 Tenured Generation 에서의 GC를 Minor GC 라고 한다.<br>
Old영역에 할당된 메모리가 허용치를 넘게 되면, Old 영역에 있는 모든 객체들을 검사하여 참조되지 않는 객체들을 한꺼번에 삭제하는 GC가 실행된다.<br>
시간이 오래 걸리는 작업이고 이 때 GC를 실행하는 쓰레드를 제외한 모든 스레드는 작업을 멈추게 된다. 이를 'Stop-the-World' 라 한다. <br>
그리고 이렇게 'Stop-the-World'가 발생하고 Old영역의 메모리를 회수하는 GC를 Major GC라고 한다.<br> 

 ## 스택 영역 (Stack Area)
스택 영역은 int, long, boolean 등 기본 자료형을 생성할 때 저장하는 공간으로, 임시적으로 사용되는 변수나 정보들이 저장되는 영역이다.<br>
데이터의 타입에 따라 스택(stack) 과 힙(haeap)에 저장되는 방식이 다르다.<br>
* 기본(원시)타입 변수는 스택 영역에 직접 값을 가진다.<br>
* 참조타입 변수는 힙 영역이나 메소드 영역의 객체 주소를 가진다.<br>

예를들어 Person p = new Person(); 와 같이 클래스를 생성할 경우, new 에 의해 생성된 클래스는 Heap Area 에 저장되고, Stack Area 에는 생성된 클래스의 참조인 p 만 저장된다.<br>
스택 영역은 각 스레드마다 하나씩 존재하며, 스레드가 시작될 때 할당된다.<br>
프로세스가 메모리에 로드 될 때 스택 사이즈가 고정되어 있어, 런타임 시에 스택 사이즈를 바꿀 수는 없다.<br>
만일 고정된 크기의 JVM 스택에서 프로그램 실행 중 메모리 크기가 충분하지 않다면 StackOverFlowError가 발생하게 된다.<br>
쓰레드를 종료하면 런타임 스택도 사라진다.<br>

 ## PC 레지스터 (Program Counter Register)
PC 레지스터는 쓰레드가 시작될 때 생성되며, 현재 수행중인 JVM 명령어 주소를 저장하는 공간이다.<br>
JVM 명령의 주소는 쓰레드가 어떤 부분을 무슨 명령으로 실행해야할 지에 대한 기록을 가지고 있다.<br>

 ## 네이티브 메서드 스택 (Native Method Stack)
* 자바 이외의 언어(C, C++, 어셈블리 등)로 작성된 네이티브 코드를 실행할 때 사용되는 메모리 영역으로 일반적인 C 스택을 사용한다.
* 보통 C/C++ 등의 코드를 수행하기 위한 스택을 말하며 (JNI) 자바 컴파일러에 의해 변환된 자바 바이트 코드를 읽고 해석하는 역할을 하는 것이 자바 인터프리터(interpreter)이다.

## ▶️ 출처 및 참조
[참조1](https://coding-factory.tistory.com/828) - 자바 JVM 내부 구조와 메모리 구조에 대하여 / 코딩팩토리 <br>
[참조2](https://inpa.tistory.com/entry/JAVA-%E2%98%95-JVM-%EB%82%B4%EB%B6%80-%EA%B5%AC%EC%A1%B0-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%98%81%EC%97%AD-%EC%8B%AC%ED%99%94%ED%8E%B8) - JVM 내부 구조 & 메모리 영역 💯 총정리 / Inpa Dev<br>
[참조3](https://steady-coding.tistory.com/305) - JVM 메모리 구조란? (JAVA) / 느리더라도 꾸준하게
