---
title: "시간 복잡도 표기법 알아보기"
date: 2025-04-27 17:00:00 +0900
categories: [CodingTest]
tags: [Code, Test]
layout: post
---

## 시간 복잡도 유형
- 빅-오메가 : 최선일 때(best case)의 연산 횟수를 나타낸 표기법
- 빅-세타 : 보통일 때(average case)의 연산 횟수를 나타낸 표기법
- 빅-오 : 최악일 때(worst case)의 연산 횟수를 나타낸 표기법

다음은  0~99 사이의 무작위값을 찾아 출력하는 코드입니다.  
빅-오메가 표기법의 시간 복잡도는 1번, 빅-세타 표기법의 시간 복잡도는 N/2번, 빅-오 표기법의 시간 복잡도는 N번입니다.

```java
public abstract class timeComplexityExample1 {
    public static void main(String[] args) {
        // 1~100 사이 값 랜덤 선택
        int findNumber = (int) (Math.random() * 100);
        for (int i = 0; i < 100; i++) {
            if (i == findNumber) {
                System.out.println(i);
                break;
            }
        }
    }
}
```
코딩 테스트에서는 빅-오 표기법을 기준으로 수행 시간을 계산하는 것이 좋습니다.

```java
public class timeComplexityExample2 {
    public static void main(String[] args) {
        int N = 100000;
        int cnt = 0;
        for (int i = 0; i < N; i++) {
            System.out.println("연산 횟수 : " + cnt++);
        }
    }
}
```
위의 코드의 결과 값은 다음 이미지와 같습니다.

![위의 코드의 결과 값](assets/img/favicons/timeComplexity/timeComplexityExample2.png)
  
다음은 연산 횟수가 3N인 경우의 코드를 확인 해보겠습니다.
```java
public class timeComplexityExample3 {
    public static void main(String[] args) {
        int N = 100000;
        int cnt = 0;
        for (int i = 0; i < N; i++) {
            System.out.println("연산 횟수 : " + cnt++);
        }
        for (int i = 0; i < N; i++) {
            System.out.println("연산 횟수 : " + cnt++);
        }
        for (int i = 0; i < N; i++) {
            System.out.println("연산 횟수 : " + cnt++);
        }
    }
}
```
위의 코드의 결과 값은 다음 이미지와 같습니다.
  
![위의 코드의 결과 값](assets/img/favicons/timeComplexity/timeComplexityExample3.png)
  
두 예제 코드의 연산 횟수는 3배의 차이가 납니다.  
언뜻 생각하면 큰 차이인 것 같지만 코딩 테스트에서는 일반적으로 상수를
무시하므로 두 코드 모두 시간 복잡도는 O(n)으로 같습니다.  

---  
  
다음은 연산 횟수가 N²인 경우의 코드를 확인 하겠습니다.
```java
public class timeComplexityExample4 {
    public static void main(String[] args) {
        int N = 100000;
        int cnt = 0;
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.println("연산 횟수 : " + cnt++);
            }
        }
    }
}
```
위의 코드의 결과 값은 다음 이미지와 같습니다.  

![위의 코드의 결과 값](assets/img/favicons/timeComplexity/timeComplexityExample4.gif)
  
시간 복잡도는 가장 많이 중첩된 반복문을 기준으로 도출하므로 이 코드에서 이중 for문이 전체 코드의 시간 복잡도 기준이 됩니다. 
만약 일반 for문이 10개 더 있다 하더라도 timeComplexityExample2에 따라 시간 복잡도의 변화 없이 N²으로 유지됩니다.
