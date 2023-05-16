# x만큼 간격이 있는 n개의 숫자

# 생각 
1. `for`문을 돌려 x값을 받아서 y만큼 돌리면 될 것 같다

# 오답
```java
class Solution {
    public long[] solution(int x, int n) {
        long[] answer = new long[n];
        
        for(int i=1; i<=n; i++){
            answer[i-1] = x*i;
        }
        
        return answer;
    }
}
```

# 오답 작성 이유
1. `long[] answer = new long[n]`을 통해서 `long[] answer`의 배열의 크기를 정해줬다
2. `for`문을 돌렸다. i는 0으로 시작하면 오류가 발생하기 때문에 1부터 돌렸다
3. 하지만 `answer`에서 배열이 0부터 시작하기 때문에 `i=1`부터 시작하는 게 배열 순서가 맞지 않았다.
4. 그렇기 때문에 i-1을 하여 배열을 맞춰주었다. 

# 오답 이유
1. `answer[i-1]`이 문제
2. 이번 문제에서는 배열의 인덱스는 0부터 시작하기 때문에, 첫 번째 요소에 접근할 때는 인덱스 0을 사용해야 한다

# 수정
```java
class Solution {
    public long[] solution(int x, int n) {
        long[] answer = new long[n];
        
        for(int i=0; i<n; i++){
            answer[i] = x*2;
        }
        
        return answer;
    }
}
```

# 해결이 안 된다 !
1. test case 13, 14에서 계속 오류가 난다
2. 이유는 모르겠다 !

# 정답 분석
```java
class Solution {
    public long[] solution(int x, int n) {
        long[] answer = new long[n];
        long num = x;
        
        for(int i=0; i<answer.length; i++){
            answer[i]=num;
            num+=x;
        }
        return answer;
    }
}
```
1. `long[] answer = new long[n];`를 통해 answer 배열값 지정
2. `long num = x;`num값을 x의 값으로 넣는다 가령 x값이 2라면 num값은 2가 된다
3. `for`문을 통해서 `answer[i]` 값에 x를 넣어준다 
4. num+=x를 통해서 곱하기처럼 구현한다
5. 즉, 초기값에 `answer[0]`에 2를 넣고 num을 두 배로 만들어준다