##  Dynamic Programming - chapter 1
### 링크 : [:link:](https://www.inflearn.com/course/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B0%95%EC%A2%8C/)

---

## 내용 정리

* 중복연산을 제거한다.
  * 대표적 예 : 피보나치 수열에서 n번째 항을 구하는 방식을 재귀로 구할때
  * 해결 방법
    * Memoization : 연산기록을 메모리에 저장하여, 연산전 메모리를 확인 해서 나가는 방법
    * Bottom-up : 밑 혹은 시작(작은) 부분 부터 목표까지 연산과정을 순차적으로 진행함으로써 중복 연산을 피함

## 추가 내용 정리

* Dynami Programiing 이란 ? 
  * 특정 범위까지의 값을 구하기 위해서 그것과 다른 범위까지의 값을 이용하여 효율적으로 ㄱ밧을 구하는 알고리즘 설계 기법. ( 출처 : [나무 위키](https://namu.wiki/w/%EB%8F%99%EC%A0%81%20%EA%B3%84%ED%9A%8D%EB%B2%95) )

* 백트래킹이란(Backtracking)?
  * 모든 경우의 수를 전부 고려하는 알고리즘.  상태공간을 트리로 나타낼 수 있을 때 적합한 방식임
    *  방식
      * DFS : 한 쪽 방향으로 마지막길 까지 내려가서 해를 찾고, 없으면 복귀 ( ex : 심플한 미로 찾기 )
      * BFS (Breadth FIrst Search) :  모든 분기점을 다 검사하면서 진행함 ( ex : 가위바위 승리시 계단 올라가기 게임에서 최소 승리 횟수 구하기)
      * Best First Serach : 위 BFS에서 조금 더 발전항 방식, 가망이 없는 경우로의 탐색을 줄임으로써 효율적인 방식, DM으로 할 수 있는건 다 구현이 가능 하다고 봐도 무방 함

## 다른 그룹원에게 질문

1. bottom-up방식과 memoization방식에 대해 각각 2줄 이내로 설명해주세요. (면접 답변용처럼)
2. 이항계수를 각각 bottom-up방식과 memoization 방식으로 구현하세요.

## 질문의 답

* 이호진

  * bottom-up 방식은 밑 혹은 작은 것부터 목적까지 의 연산을 순차적으로 하는 것을 의미 합니다.  탄생 배경은 재귀로 인한 중복연산이나 메모리제이션보다 메모리를 덜 쓰기 위하여 탄생했으며, 복잡도는 기본적으로 O(n)입니다.

  * 메모리제이션은 연산 결과를 다른 메모리에 저장하는것을 의미합니다. 탄생배경은 중복계산을 방지로 연산 속도를 높이기 위하여 사용됩니다. (edited)

  * ~~~java
    int binomialOfBottom(int n, int k) {
            for(int i=0 ; i<=n ;i++) {
                for(int j=0; j<=k && j<=1; j++) {
                    if(k==0 || n==k) {
                        binom[i][j] = 1;
                    }else {
                        binom[i][j] = binom[i-1][j-1] +
                            binom[i-1][j];
                    }
    
                }
            }
            return binom[n][k];
        }
    int binomialOfMemory(int n, int k) {
            if(n == k || k == 0) {
                return 1;
            }else if (binom[n][k] != -1) {
                return binom[n][k];
            }else {
                binom[n][k] = binomialOfMemory(n-1, k) + 
                           binomialOfMemory(n-1, k-1);
                return binom[n][k];
            }
    
        }
    ~~~

