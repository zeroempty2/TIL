## 이분 탐색(Binary search)이란?
>이분탐색이란 정렬되어 있는(이분 탐색의 주요 조건) 배열에서 데이터를 찾으려 시도할 때, 순차탐색처럼 처음부터 끝까지 하나씩 모든 데이터를 체크하여 값을 찾는 것이 아니라
탐색 범위를 절반씩 줄여가며 찾아가는 Search 방법이다.<br>
이분탐색은 반드시 리스트(배열)를 정렬해서 사용해야 한다는 단점이 있으며, 탐색할 때마다 검사 범위가 절반으로 줄어든다.<br>
재귀적인 방법, 반복문, STL를 이용하여 이분 탐색(Binary Search)을 실행할 수 있다.<br>
![binary-and-linear-search-animations (1)](https://github.com/zeroempty2/TIL/assets/117061586/76917fbb-0dbf-447e-8e7a-1b942eb84389)<br>
이분탐색의 시간 복잡도는 O(log N)이다.<br>


<br>

## ▶️ 이분 탐색 알고리즘 코드(JAVA)
이분탐색은 변수 3개(start, end, mid)를 사용하여 탐색한다. 찾으려는 데이터와 중간점 위치에 있는 데이터를 반복적으로 비교해서 원하는 데이터를 찾는 것이 이진 탐색의 과정이다. <br>

* 반복문

```java
 public int binarySearch(int[] array, int target){
      int start = 0;
      int end = array.length - 1;
      int mid = (start+end)/2;
      int count = 0;
      while(start <= end){
        if(array[mid] == target){
          System.out.println("탐색을 위해 " + count + "번 더 반복했습니다!"); 
          return array[mid];
        } 
        else if(array[mid] <= target) start = mid + 1;
        else end = mid - 1;
        mid = (start+end)/2;
        count++;
      }
      return -1;
    }
```
위와 같은 함수에 배열 {1,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59}, 타겟 37을 대입하면 다음과 같은 값을 볼 수 있다.<br>
![image](https://github.com/zeroempty2/TIL/assets/117061586/df846fae-e06d-4fab-ad8e-3e4334f040fe)<br>

<br>

재귀함수로도 구현이 가능하다.<br>

* 재귀함수

```java
 public int solution(int[] array, int target) {
      int start = 0;
      int end = array.length - 1;
      int mid = (start+end)/2;
      int count = 0;
      return binarySearch(array, start, end, mid, target, count);
    }
    
    public int binarySearch(int[] array,int start, int end, int mid, int target, int count){
      if(array[mid] == target){
        System.out.println("탐색을 위해 " + count + "번 더 탐색했습니다!"); 
        return array[mid];
      }
      else if(array[mid] <= target) {
        count++;
        binarySearch(array, mid+1, end, (mid+1 + end)/2, target, count);
      }
      else{
        count++;
        binarySearch(array, start, mid-1, (start + mid-1)/2, target, count);
      }
      return -1; 
    }
```


<br>




## ▶️ 출처 및 참조
[참조1](https://velog.io/@kimdukbae/%EC%9D%B4%EB%B6%84-%ED%83%90%EC%83%89-%EC%9D%B4%EC%A7%84-%ED%83%90%EC%83%89-Binary-Search) - 이분 탐색 / 이진 탐색 (Binary Search) / kdb.velog <br>
[참조2](https://satisfactoryplace.tistory.com/39) - 이분 탐색(Binaray Search) / 만족<br>
[참조3](https://m42-orion.tistory.com/69) - 이분 탐색(Binary Search) / while(true) { continue; }
