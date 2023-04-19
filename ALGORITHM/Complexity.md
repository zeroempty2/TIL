## 복잡도란?
>알고리즘 성능을 평가하기 위해서는 '복잡도(Complexity)'의 척도를 사용한다고 한다.<br>
그중 시간 복잡도와 공간 복잡도의 개념이 나오며, 동일한 기능을 수행하는 알고리즘이 있을 때 복잡도가 낮을 수록 좋은 알고리즘이라 말한다.<br>
복잡도는 각 알고리즘이 주어진 특정 크기의 입력(n)을 기준으로 수행시간(연산) 혹은 사용공간이 얼마나 되는지 객관적으로 비교할 수 있는 기준을 제시한다.<br>
복잡도를 나타내는 방법으로는 점근 표기법으로 O(빅오), Ω(오메가), Θ(세타) 등이 있고, 주로 빅오와 세타 표기법이 많이 사용된다.<br>
다시 말해, 복잡도는 어떤 알고리즘이 효율적인지를 판단하는 척도이다.<br>
<br>

## ▶️ 시간 복잡도
시간 복잡도는 특정 크기의 입력을 기준으로 할 때 필요한 연산의 횟수를 나타낸다.<br>
이름은 시간 복잡도이지만 실행 시간이 아닌 연산 횟수를 세는 이유는 다음과 같다.<br>
    1. 모든 OS, IDE, 플랫폼에서 동일한 결과가 나오지 않는다.<br>
    2. 실행 시간 측정을 위한 또다른 방법이 필요하다.<br>


<br>

## ▶️ 공간 복잡도 (Space Complexity)
공간 복잡도란 프로그램 실행과 완료에 얼마나 많은 공간(메모리)가 필요한지를 나타낸다.<br>
알고리즘을 실행시키기 위해 필요한 공간(space)는 두 가지로 나눌 수 있다.<br>
1. 알고리즘과 무관한 공간, 즉 고정 공간<br>
    * 코드가 저장되는 공간, 알고리즘 실행을 위해 시스템이 필요로 하는 공간 등<br>
2. 알고리즘과 밀접한 공간, 즉 가변 공간<br>
    * 문제를 해결하기 위해 알고리즘이 필요로 하는 공간. 변수를 저장하는 공간, 순환 프로그램일 경우 순환 스택(recursion stack) 등<br>


<br>

## ▶️ 빅-오 표기법
빅오 표기법(Big-O notation)은 복잡도를 나타내는 점근 표기법 중 가장 많이 사용되는 표기법이다.<br>
빅오 표기법이 가장 많이 사용되는 이유는 알고리즘 효율성을 상한선 기준으로 표기하기 때문이다.<br>
다시 말해 최악의 경우를 고려하는 데 가장 좋은 표기법이다 (알고리즘 효율성은 값이 클수록, 즉 그래프가 위로 향할수록 비효율적임을 의미)<br>

<br>

![image](https://user-images.githubusercontent.com/117061586/232772289-2d94f4d9-8463-4841-b105-1b04970c1e08.png)<br>
[이미지 출처 - 시간 복잡도, 공간 복잡도 / minam.log](https://velog.io/@cha-suyeon/Algorithm-%EC%8B%9C%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84-%EA%B3%B5%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84)<br>

<br>

※ n이란 입력되는 데이터를 의미.<br>

<br>

O(1) (Constant)<br>
입력 데이터의 크기에 상관없이 언제나 일정한 시간이 걸리는 알고리즘을 나타낸다. 데이터가 얼마나 증가하든 성능에 영향을 거의 미치지 않는다.<br>

<br>

O(log₂ n) (Logarithmic)<br>
입력 데이터의 크기가 커질수록 처리 시간이 로그(log: 지수 함수의 역함수) 만큼 짧아지는 알고리즘이다.<br>
예를 들어 데이터가 10배가 되면, 처리 시간은 2배가 된다. 이진 탐색이 대표적이며, 재귀가 순기능으로 이루어지는 경우도 해당된다.<br>

<br>

O(n) (Linear)<br>
입력 데이터의 크기에 비례해 처리 시간이 증가하는 알고리즘이다.<br> 
예를 들어 데이터가 10배가 되면, 처리 시간도 10배가 된다. 1차원 for문이 있다.<br>

<br>

O(n log₂ n) (Linear-Logarithmic)<br>
데이터가 많아질수록 처리시간이 로그(log) 배만큼 더 늘어나는 알고리즘이다.<br>
 예를 들어 데이터가 10배가 되면, 처리 시간은 약 20배가 된다. 정렬 알고리즘 중 병합 정렬, 퀵 정렬이 대표적이다.<br>

<br>

O(n²) (quadratic)<br>
데이터가 많아질수록 처리시간이 급수적으로 늘어나는 알고리즘이다.<br>
예를 들어 데이터가 10배가 되면, 처리 시간은 최대 100배가 된다.<br>
이중 루프(n² matrix)가 대표적이며 단, m이 n보다 작을 때는 반드시 O(nm)로 표시하는 것이 바람직하다.<br>

<br>

O(2ⁿ) (Exponential)<br>
데이터량이 많아질수록 처리시간이 기하급수적으로 늘어나는 알고리즘이다.<br> 
대표적으로 피보나치 수열이 있으며, 재귀가 역기능을 할 경우도 해당된다.<br>

<br>

그래프와 위 설명을 참고하여, 시간 복잡도에 따른 성능을 비교하면 아래와 같다.<br>

```
faster O(1) < O(log n) < O(nlog n) < O(n²) < O(2ⁿ) slower
```

slower로 갈수록(즉, 오른쪽 방향으로 갈수록) 효율성이 떨어진다.

<br>

## ▶️ 시간 복잡도 예제
다음과 같이 숫자로 이루어진 배열이 있을 때, 이 배열 내에서 가장 큰 수를 반환해야한다고 한다.<br>
[3, 5, 6, 1, 2, 4]<br>

이 문제를 두가지 유형으로 풀어보았다.<br>

<br>

```java
 public int findMaxNum(int[] numArray){
   int maxNum = 0;
   for (int i : numArray) {
     if (maxNum < i) {
       maxNum = i;
     }
   }
   return maxNum;
 }
```
첫번째는, 배열의 가장 큰 수를 저장할 변수를 만들고, 배열을 돌면서 그 변수와 비교하는 방식이다. <br>

<br>

```java
  public int findMaxNum(int[] numArray){
    int maxNum = numArray[0];
    for (int i : numArray) {
      maxNum = i;
      for(int j : numArray){
        if(i < j){
         maxNum = j;
        }
      }
    }
  return maxNum;
  }
```

두번째는, 배열의 가장 큰 수를 저장한 변수를 만드나, 변수와 값을 비교하지 않고, 배열의 값끼리 일일히 비교하는 방식이다. <br>
실제로는 이렇게 풀지 않겠지만, 시간 복잡도를 비교하기 위해 이렇게 만들어 보았다. <br>

<br>
그렇다면, 위의 함수가 시간이 얼마나 걸리는지 어떻게 분석할 수 있을까?<br>
각 줄이 실행되는 걸 1번의 연산이 된다고 생각하고 계산하시면 된다.<br>
첫번째 함수는 아래와 같이 계산 해 볼 수 있다.<br>

```java
 public int findMaxNum(int[] numArray){
   int maxNum = numArray[0]; // 대입 연산 1번 실행
   for (int i : numArray) { // array 의 길이만큼 아래 연산이 실행
     if (maxNum < i) { // 비교 연산 1번 실행
       maxNum = i; // 대입 연산 1번 실행
     }
   }
   return maxNum;
 }
```
위에서 연산 된 것들을 더해보면,<br>
1. maxNum 대입연산 1번<br>
2. array의 길이 X (비교 연산 1번 + 대입 연산 1번)<br> 
만큼의 시간이 필요하다.  array 의 길이를 N이라고 하면, 다음과 같이 표현 할 수 있다.<br> 
```
1 + 2 x N = 2N + 1
```
이때, 매번 코드를 매 실행 단위로 이렇게 몇 번의 연산이 발생하는지 확인하는 건 불가능하기때문에. 상수는 신경쓰지않고, 입력값에 비례해서 어느 정도로 증가하는지만 파악하면 된다.<br> 
따라서 첫번째 함수는 N의 시간 복잡도를 가지고 있다. <br> 

두번째 함수는 얼마만큼의 시간 복잡도를 가지고 있을까? <br> 

```java
  public int findMaxNum(int[] numArray){
    int maxNum = numArray[0]; // 대입 연산 1번 실행
    for (int i : numArray) { // array 의 길이만큼 아래 연산이 실행
      maxNum = i; // 대입 연산 1번 실행
      for(int j : numArray){ // array 의 길이만큼 아래 연산이 실행
        if(i < j){ // 비교 연산 1번 실행
         maxNum = j; // 대입 연산 1번 실행
        }
      }
    }
  return maxNum;
  }
```
상수를 신경쓰지 않고, 입력값(array)의 길이만 계산하면,<br>
```
N x N = N^2
```
두번째 함수는 N^2의 시간복잡도를 가지고 있다.



## ▶️ 출처 및 참조
[참조1](https://madplay.github.io/post/time-complexity-space-complexity) - 시간복잡도와 공간복잡도(Time Complexity Space Complexity) / MadPlay! <br>
[참조2](https://velog.io/@cha-suyeon/Algorithm-%EC%8B%9C%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84-%EA%B3%B5%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84) - 시간 복잡도, 공간 복잡도 / minam.log<br>
[참조3](https://velog.io/@welloff_jj/Complexity-and-Big-O-notation) - 복잡도(Complexity): 시간 복잡도와 공간 복잡도, 그리고 빅오(Big-O) 표기법 / hyeojung.log
