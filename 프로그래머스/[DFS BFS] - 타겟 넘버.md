# 타겟 넘버
[코딩테스트 연습 \- 타겟 넘버 | 프로그래머스 스쿨 (programmers.co.kr)](https://school.programmers.co.kr/learn/courses/30/lessons/43165?language=java)

```java
class Solution {
    private static int cnt = 0;
    public int solution(int[] numbers, int target) {
               
        dfs(0, numbers, target);	// DFS를 이용해 풀이
        int answer = cnt;
        
        return answer;
    }

    public void dfs(int index, int[] numbers, int target){
        
        if(index == numbers.length){	// 주어진 배열의 마지막 자리일 경우
            int sum = 0;				// sum초기화
            for(int i=0; i<numbers.length; i++){
                sum += numbers[i];		// sum에 주어진 배열의 수를 더한다
            }
            if(sum == target){			// 배열을 모두 더한 값이 target과 같은 경우
                cnt++;					// cnt++
            }
        } else {						// 마지막자리가 아닐 경우 재귀함수를 통해 부호를 바꿔가며 탐색
            numbers[index] *= 1;
            dfs(index+1, numbers, target);
            
            numbers[index] *= -1;
            dfs(index+1, numbers, target);
        }
    }
}
```

# DFS
DFS는 깊이 우선 탐색(Depth-First Search)의 약어로, 그래프나 트리 등의 자료구조에서 모든 노드를 방문하는 탐색 알고리즘이다. DFS는 스택(Stack)이나 재귀 함수를 통해 구현된다.

DFS는 한 경로를 끝까지 탐색한 후, 다음 경로로 넘어가며 탐색을 진행한다. 이 과정에서 더 이상 탐색할 경로가 없으면 되돌아와 다른 경로를 탐색한다. 이러한 방식으로 모든 노드를 탐색하게 된다.

# 풀이
1. 매개변수로 현재까지의 인덱스(`index`), 숫자 배열(`numbers`), 그리고 목표 숫자(`target`)를 받는다
2. 기저 조건인 `index == numbers.length`은 모든 숫자를 탐색한 경우를 의미한다. 
3. 주어진 배열의 모든 수를 더한 값을 `sum` 변수에 저장한다.
4. `sum` 값이 목표 숫자(`target`)와 같다면, `cnt` 변수를 증가시켜 가능한 경우의 수를 세는 역할을 한다
5. `cnt` 변수는 클래스 변수로 선언되어 있으므로, 모든 재귀 호출에서 공유되며 최종적인 경우의 수를 담는다.
6. 기저 조건이 아닌 경우, `numbers[index]`의 부호를 바꾸어 재귀 호출을 수행한다
7. 먼저 `numbers[index]`를 1로 곱하여 재귀 호출을 수행하고, 다음으로 `-1`로 곱하여 재귀 호출을 수행한다. 
8. 이를 통해 모든 가능한 부호 조합을 탐색한다.
9. 최종적으로 `solution` 메서드에서는 `dfs` 메서드를 호출하여 가능한 경우의 수를 찾고, 그 값을 `cnt` 변수에 저장한 후 `answer`로 반환한다.
