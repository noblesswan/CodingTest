# 특정 문자 제거하기
```java
class Solution {
    public String solution(String my_string, String letter) {
        String answer="";
        answer=my_string.replace(String.valueOf(letter),""); 
        return answer;
    }
}
```

## 생각

1. 처음에는  각 글자를 `split()`으로 나눠준 뒤 `for`문과 `if`를 사용해서 letter를 제거하려고 함
2. 하지만 return 값이 배열이 됨
3. 이에 다른 사람 코드를 보니 애초에 `replace()`가 존재했음 

## 풀이

1. `replace()`를 사용하면 해결됨

## Method
### replace()
1. `replace()` 메서드는 문자열에서 지정된 문자 또는 문자열을 다른 문자 또는 문자열로 바꾸는 역할
2. `my_string` 문자열에서 `letter` 문자열을 빈 문자열로 대체
3. 예를 들어, `my_string`이 "Hello"이고 `letter`가 "l"이라면 `replace()` 메서드를 사용하면 "Hello" 문자열에서 "l"을 제거하고 "Heo"를 반환
 
### valueOf()
1. `valueOf()` 메서드는 다른 데이터 유형을 문자열로 변환 
2. `String` 클래스의 정적 메서드로 제공되며, 매개변수로 전달된 값의 문자열 표현을 반환
3. 해당 코드에서는 `letter` 변수를 `String.valueOf(letter)`를 사용하여 문자열로 변환
4. 예를 들어, `letter` 변수가 문자 'a'라면 `valueOf()` 메서드를 사용하면 "a"라는 문자열을 반환합니다.