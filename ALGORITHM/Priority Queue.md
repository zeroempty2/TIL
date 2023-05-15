## 우선순위 큐(PriorityQueue)
>일반적인 큐는 > FIFO (First In First Out),처음으로 들어온 데이터가 가장 먼저 나가는 형태이다.<br>
PriorityQueue는 먼저 들어온 순서대로 데이터가 나가는 것이 아닌 우선순위를 먼저 결정하고 그 우선순위가 높은 엘리먼트가 먼저 나가는 자료구조이다.<br>
우선순위 큐는 힙을 이용하여 구현하는 것이 일반적이다.<br>
<br>

## ▶️ Priority Queue의 특징
* 높은 우선순위의 요소를 먼저 꺼내서 처리하는 구조 (큐에 들어가는 원소는 비교가 가능한 기준이 있어야함) <br>
* 내부 요소는 힙으로 구성되어 이진트리 구조로 이루어져 있다.<br>
* 내부구조가 힙으로 구성되어 있기에 시간 복잡도는 O(NLogN)이다.<br>
* 데이터 삽입 시 우선순위 기준으로 최대 힙, 최소 힙을 구성한다.<br>
* 데이터 추출 시, 루트 노드를 얻어 루트 노드를 삭제할 때는 빈 루트 노드 위치에 맨 마지막 노드를 삽입 후 아래 노드로 내려가면서 정렬하는 방식으로 진행된다.<br>
* 최대 힙 = 최대 값이 우선순위인 큐<br>
* 최소 힙 = 최소 값이 우선순위인 큐<br>


## ▶️ Priority Queue의 사용법

* Priority Queue 선언<br>

```java
import java.util.PriorityQueue; //import

//int형 priorityQueue 선언 (우선순위가 낮은 숫자 순)
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();

//int형 priorityQueue 선언 (우선순위가 높은 숫자 순)
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());

//String형 priorityQueue 선언 (우선순위가 낮은 숫자 순)
PriorityQueue<String> priorityQueue = new PriorityQueue<>(); 

//String형 priorityQueue 선언 (우선순위가 높은 숫자 순)
PriorityQueue<String> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());
```

<br>

* Priority Queue 값 추가<br>

```java
priorityQueue.add(1);     // priorityQueue 값 1 추가
priorityQueue.add(2);     // priorityQueue 값 2 추가
priorityQueue.offer(3);   // priorityQueue 값 3 추가
```
add(value) 메서드의 경우  삽입에 성공하면 true를 반환하고, 큐에 여유 공간이 없어 삽입에 실패하면 IllegalStateException을 발생시킨다.<br>
우선순위 큐에 값을 추가한다면 다음의 과정을 거쳐 값이 추가된다.<br>
![image](https://github.com/zeroempty2/TIL/assets/117061586/8dda47fe-3f23-4fa3-839a-93634d9b4a24)<br>
[출처 - PriorityQueue(우선순위 큐) 클래스 사용법 & 예제 총정리/ 코딩팩토리](https://coding-factory.tistory.com/603)<br>

* Priority Queue 값 삭제<br>
```java
priorityQueue.poll();       // priorityQueue에 첫번째 값을 반환하고 제거 비어있다면 null
priorityQueue.remove();     // priorityQueue에 첫번째 값 제거
priorityQueue.clear();      // priorityQueue에 초기화
```
.poll()을 하면 다음과 같은 과정을 거쳐 삭제된다.<br>
![image](https://github.com/zeroempty2/TIL/assets/117061586/10c312fe-83ff-4ef8-b1a1-c9b4c577692e)<br>
[출처 - PriorityQueue(우선순위 큐) 클래스 사용법 & 예제 총정리/ 코딩팩토리](https://coding-factory.tistory.com/603)<br>

<br>

* Priority Queue에서 우선순위가 가장 높은 값 출력<br>
```java
priorityQueue.peek();       // priorityQueue에 첫번째 값 참조 = 1
```
Priority Queue에서 우선순위가 가장 높은 값을 참조하고 싶다면 peek()라는 메서드를 사용하면 된다. 

<br>


## ▶️ 출처 및 참조
[참조1](https://coding-factory.tistory.com/603) - PriorityQueue(우선순위 큐) 클래스 사용법 & 예제 총정리/ 코딩팩토리 <br>
[참조2](https://satisfactoryplace.tistory.com/39) - 이분 탐색(Binaray Search) / 만족<br>
[참조3](https://m42-orion.tistory.com/69) - 이분 탐색(Binary Search) / while(true) { continue; }
