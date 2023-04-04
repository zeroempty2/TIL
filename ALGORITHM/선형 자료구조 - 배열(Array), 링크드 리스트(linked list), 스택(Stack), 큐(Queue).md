## 선형 자료구조
![image](https://user-images.githubusercontent.com/117061586/229787476-665c6b76-0484-4ad3-a6c7-2e4fab08ef66.png)
[이미지 출처 - 선형 자료구조 : 배열(Array), 연결리스트(linked list), 스택(Stack), 큐(Queue)](https://questionet.tistory.com/36)

<br>

## Stack 
> LIFO (Last In First Out) <br>
마지막으로 들어온 데이터가 가장 먼저 나가는 형태. 예를 들어, 책을 쌓는 것과 같이 가장 마지막에 넣은 책이 가장 먼저 나오는 것을 의미한다.

<br>

## Stack 사용 사례
* 웹 브라우저 방문기록 (뒤로 가기) : 가장 나중에 열린 페이지부터 다시 보여준다.<br>
* 역순 문자열 만들기 : 가장 나중에 입력된 문자부터 출력한다.<br>
* 실행 취소 (undo) : 가장 나중에 실행된 것부터 실행을 취소한다.<br>
* 후위 표기법 계산<br>
* 수식의 괄호 검사 (연산자 우선순위 표현을 위한 괄호 검사)<br>


<br>

## Queue 
> FIFO (First In First Out) <br>
처음으로 들어온 데이터가 가장 먼저 나가는 형태. 예를 들어, 대기열과 같이 먼저 들어온 요소가 먼저 처리되는 것을 의미한다.

<br>

## Queue 사용 사례 
* 프로세스 관리<br>
* 너비 우선 탐색(BFS, Breadth-First Search) 구현<br>
* 캐시(Cache) 구현<br>


<br>

## Array
> Array는 동일한 데이터 형식의 원소들이 메모리 상에 연속적으로 저장되는 자료구조이다. 

<br>

## Array의 특징
* 연속된 메모리 공간에 순차적으로 저장한다.<br>
  연속되어 배열된 각 값(value)에는 인덱스(index)가 있고
  인덱스는 메모리의 주소를 가리킨다.<br>
  값과 인덱스를 합쳐 원소(element)라고 부른다.
* 배열을 선언할 때 크기를 정하는데
   이렇게 정해진 배열의 크기는 변경할 수 없다.<br>
   다시 말해, 배열의 크기는 고정돼 있다.


<br>

## Array를 사용하기 좋은 경우
* 다차원 데이터를 다룰 때<br>
* 어떠한 특정 요소를 빠르게 읽어야 할 때 (index로 바로 접근)<br>
* 데이터의 사이즈가 자주 변하지 않을 때<br>
* 요소가 자주 추가, 삭제가 되지 않을 때<br>


<br>

## Array의 단점
* 메모리 상에 맨 앞 또는 중간에
  저장된 데이터를 삭제하거나, 삽입하는 경우
  작업속도가 시간복잡도 O(n)만큼 걸린다.<br>


  메모리 공간에 연속적으로 할당했기 때문에
  해당 원소 이후의 모든 원소를 한칸씩 당기거나
  밀어야 하기 때문이다.


<br>

## Linked List
> 배열(Array)처럼
데이터를 순차적으로 저장하는 선형 자료구조이지만
메모리 공간에 불연속적으로 저장된다.<br>
다시 말해, 컴퓨터의 메모리 어딘가에 여기저기 흩뿌려져 할당된다.<br>
배열처럼 index가 있는것이 아니고 pointer를 통해 다음 노드들을 가리키는 형식으로 
되어 있기 때문에 배열처럼 원하는 index에 접근해 바로 값을 가지고오는 것이 불가능하다.


<br>

## Linked List의 특징
* 연결리스트의 각 노드(원소)들은
   포인터를 기반으로 연결되어 리스트를 구성한다.<br>
   첫번째 노드는 헤드(Head),<br>
   마지막 노드를 테일(Tail).<br>

* 각 노드는
   데이터와
   다음 노드를 가리키는 포인터로 이루어진다.<br>
   바꿔 말하면
   인덱스 접근이 불가능하다.<br>
   Random Access가 불가능하다.

* 반드시 연결된 노드를 통해서만 접근이 가능하다.<br>
   따라서 n번째 저장된 데이터에 접근하려면
   n-1번까지 순차적으로 접근해야 한다
   (Sequential Access)

* 따라서 리스트의 맨 앞 또는 뒤에
   데이터를 삽입, 삭제하는 경우 O(1)<br>
   반면
   리스트의 중간에 삽입, 삭제하는 경우 O(n)<br>


<br>

## Linked List의 장점
* 데이터의 삽입과 삭제가 용이<br>
   (포인터가 가리키는 노드만 변경해주면 된다)<br>
* 크기가 고정되어 있지 않아 크기 제한에서 자유롭다.<br>


<br>

## Linked List의 단점
* 검색 성능이 좋지 않다.
* 포인터로 인하여 저장 공간의 낭비가 발생


<br>

## Linked List를 사용하는 경우
* 크기가 정해져 있지 않을 때
* 삽입과 삭제가 자주 일어날 때
* 검색을 자주 하지 않을 때


<br>

## Array와 Linked List의 차이
![image](https://user-images.githubusercontent.com/117061586/229806685-9cd867d9-d548-4d69-a1c7-93505de101df.png)
[이미지 출처 - 자료구조 - Array(List), Tuple, Stack, Queue, LinkedList](https://questionet.tistory.com/36)


<br>

[참조1](https://questionet.tistory.com/36) - 선형 자료구조 : 배열(Array), 연결리스트(linked list), 스택(Stack), 큐(Queue) / questionet <br>[참조2](https://velog.io/@jinukix/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0#stack) - 자료구조 - Array(List), Tuple, Stack, Queue, LinkedList / jinukix 