# 타겟 넘버
[코딩테스트 연습 \- 타겟 넘버 | 프로그래머스 스쿨 (programmers.co.kr)](https://school.programmers.co.kr/learn/courses/30/lessons/43165?language=java)

```java
class Solution {
    public int solution(int[] numbers, int target) {
        int answer = 0;
        answer = dfs(numbers, 0, 0, target);
        return answer;
    }
    int dfs(int[] numbers, int n, int sum, int target) {
        if(n == numbers.length) {
            if(sum == target) {
                return 1;
            }
            return 0;
        }
        return dfs(numbers, n + 1, sum + numbers[n], target) + dfs(numbers, n + 1, sum - numbers[n], target);
    }
}
```

# DFS
DFS는 깊이 우선 탐색(Depth-First Search)의 약어로, 그래프나 트리 등의 자료구조에서 모든 노드를 방문하는 탐색 알고리즘이다. DFS는 스택(Stack)이나 재귀 함수를 통해 구현된다.

DFS는 한 경로를 끝까지 탐색한 후, 다음 경로로 넘어가며 탐색을 진행한다. 이 과정에서 더 이상 탐색할 경로가 없으면 되돌아와 다른 경로를 탐색한다. 이러한 방식으로 모든 노드를 탐색하게 된다.

# 풀이
1. 이 문제는 숫자 배열에서 주어진 숫자(target)를 만들 수 있는 경우의 수를 찾는 문제를 해결하기 위한 솔루션이다.
2. `dfs` 함수는 재귀적으로 호출되며, 매개변수로 현재까지 탐색한 숫자 배열(`numbers`), 현재 탐색 위치(`n`), 현재까지의 합(`sum`), 그리고 목표 숫자(`target`)를 받는다.
3. 기저 조건인 `n == numbers.length`은 모든 숫자를 탐색한 경우를 의미한다.  이때, 현재까지의 합(`sum`)이 목표 숫자(`target`)와 같은지 확인하고, 같다면 1을 반환합니다. 같지 않다면 0을 반환합니다.

재귀적으로 `dfs` 함수를 호출하는 부분은 다음과 같습니다.

1.  `n + 1` 위치의 숫자를 더하여 재귀 호출합니다. 이때, `sum + numbers[n]`은 현재까지의 합에 `numbers[n]`을 더한 값입니다. 탐색 위치를 한 칸 앞으로 이동하고, 합을 갱신하여 재귀적으로 탐색을 진행합니다.
2.  `n + 1` 위치의 숫자를 뺀 후 재귀 호출합니다. 이때, `sum - numbers[n]`은 현재까지의 합에서 `numbers[n]`을 뺀 값입니다. 탐색 위치를 한 칸 앞으로 이동하고, 합을 갱신하여 재귀적으로 탐색을 진행합니다.

재귀 호출된 두 개의 결과를 더한 값이 최종적인 경우의 수입니다. 이는 현재 숫자를 선택하는 경우와 선택하지 않는 경우로 나누어진 모든 가능한 경우의 수를 합한 것입니다.

최종적으로 `solution` 함수는 `dfs` 함수를 호출하고 그 결과를 반환합니다.

이 코드는 주어진 숫자 배열에서 DFS를 활용하여 타겟 숫자를 만들 수 있는 모든 경우의 수를 구하는 예시입니다.