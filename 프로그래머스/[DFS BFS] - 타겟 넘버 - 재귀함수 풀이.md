# 타겟 넘버 - 재귀함수 풀이
[코딩테스트 연습 \- 타겟 넘버 | 프로그래머스 스쿨 (programmers.co.kr)](https://school.programmers.co.kr/learn/courses/30/lessons/43165?language=java)

``` java
class Solution {
    int count = 0;
    public int solution(int[] numbers, int target) {
        int answer = 0;
        dfs(numbers, 0, target, 0);
        answer = count;
        
        return answer;
    }
    public void dfs(int[] numbers, int depth, int target, int result){
        if (depth == numbers.length){ //마지막 노드까지 진행했을 때
            if (target == result){ //target값과 합계가 같다면
                count++;
            }
            return;
        }
        
        int plus = result + numbers[depth]; //양수를 더한 값
        int minus = result - numbers[depth]; //음수를 더한 값
        
        dfs(numbers, depth+1, target, plus);
        dfs(numbers, depth+1, target, minus);
    }
}

```

# 생각
![다운로드.png](..\..\..\Users\kosa\Desktop\다운로드.png)

1. `answer++`를 해준다
2. `numbers[i]` +/-를 해준다
3. `result += numbers[i]`
      `result -= numbers[i]`
4. `for`문을 돌린다
```java
class Solution {
    public int solution(int[] numbers, int target) {
        int answer = 0;
        int result = 0;
        
        
        for(int i=0; i<numbers.length; i++){
            result += numbers[i];
            result -= numbers[i];
        }
        return answer;
    }
}
```
- 이렇게 하면 문제인 게, `numbers[i]` 값을 계속해서 더하고 빼서 더하기 때문에 -8과 +8만 나올뿐이다. 
- 그렇다면 `numbers` 별로 값을 더하고 빼는 코딩을 해보자

```java
class Solution {
    public int solution(int[] numbers, int target) {
        int answer = 0;
        int result = 0;
        
        
        for(int i=0; i<numbers.length; i++){
            result += numbers[i];
            result -= numbers[i];
        }
        return answer;
    }
}
```
`numbers[4]`일 경우 0에 4를 더하고 빼야한다 
`index[i] = result+numbers[i]`
`index[0]`의 경우, `numbers[4]`가 들어간다. 
`index[1]`의 경우 `numbers[1]` 들어가서 더한다. 
index[0] - 4
index[1] - 5
index[2] - 7
index[3] - 8

이제 이해됐다.
depth를 통해서 푼다
알았어 이제 !

```java
class Solution {
    int count = 0;
    public int solution(int[] numbers, int target) {
        int answer = 0;
        dfs(numbers, 0, target, 0);
        answer = count;
        
        return answer;
    }
    public void dfs(int[] numbers, int depth, int target, int result){
        if (depth == numbers.length){ //마지막 노드까지 진행했을 때
            if (target == result){ //target값과 합계가 같다면
                count++;
            }
            return;
        }
        
        int plus = result + numbers[depth]; //양수를 더한 값
        int minus = result - numbers[depth]; //음수를 더한 값
        
        dfs(numbers, depth+1, target, plus);
        dfs(numbers, depth+1, target, minus);
    }
}
```