# 문자열 내 P와 Y의 갯수
```java
class Solution {
    boolean solution(String s) {
        boolean answer = true;
        int pP = 0;
        int yY = 0;
        String[] arr = String.valueOf(s).split("");
        for(int i=0; i<arr.length; i++){
            if(arr[i].equals("p") || arr[i].equals("P")){
                pP++; 
            }
            else if(arr[i].equals("y") || arr[i].equals("Y")){
                yY++;
            }
        }
        
        if(pP != yY){
            answer = false;
        }
        
        return answer;
    }
}
```

# 생각 
1. p와 y의 갯수가 같으면 true 틀리면 false를 반환해야 함
2. string으로 된 글자들을 전부 split으로 나눠준 뒤 if문을 통해서 특정 변수에 담아서 ++를 해준다

# 답안지 작성
```java
class Solution {
    boolean solution(String s) {
        boolean answer = true;
        int pP = 0;
        int yY = 0;
        String[] arr = String.valueOf(s).split("");
        for(int i=0; i<arr.length; i++){
            if(arr[i]=="p" || arr[i]=="P"){
                pP++; 
            }
            else if(arr[i]=="p" || arr[i]="P"){
                yY++;
            }
        }
        
        if(yY == pP){
            answer = true;
        }
        else{
            answer = false;
        }
        
        return answer;
    }
}
```
1. 오류가 발생함 
2. 오류 발생 이유는 `arr[i]=="P"`가 잘못됐다.
3. 문자열 비교는 `==` 대신 `equals()` 메서드를 사용해야 한다. `==` 연산자는 두 문자열의 참조를 비교하기 때문에 의도한 대로 문자열 값을 비교할 수 없다
4. `==` 연산자는 기본적으로 두 개체의 참조(메모리 주소)를 비교. 즉, 두 개체가 동일한 메모리 위치를 가리키는지 확인 
- 두 개체의 값이 동일하더라도 다른 메모리 위치에 저장되어 있다면 `==` 연산자는 false를 반환
5. `equals()` 메서드는 두 개체의 내용(값)을 비교한다

# 결론
1. `equals()`와 `==`의 차이를 몰라서 문제를 틀렸다. 이 둘의 차이점을 알고 써야한다

