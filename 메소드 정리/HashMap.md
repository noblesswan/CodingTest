# HashMap

- 키와 값을 매핑하는데 사용되는 데이터 구조
- `HashMap`은 `HashTable`의 비동기 버전으로 간주할 수 있으며, 멀티스레드 환경에서 더 효율적

## 특징
1.  **키(Key)와 값(Value)을 저장:** `HashMap`은 키(key)와 값(value)의 쌍을 저장한다. 키는 고유해야 하므로 두 개의 키가 동일한 값을 가질 수 없다. 그러나 두 개의 다른 키는 동일한 값을 가질 수 있다.

2.  **Null 값과 Null 키:** `HashMap`은 하나의 Null 키와 여러 개의 Null 값을 허용한다.
    
3.  **비동기:** `HashMap`은 비동기이며 스레드 안전하지 않다. 따라서 여러 스레드가 동시에 `HashMap`에 접근하면 동시성 문제가 발생할 수 있다. 이 문제를 해결하려면 `Collections.synchronizedMap(hashMap)`을 사용하여 동기화된 `HashMap`을 얻을 수 있다.
    
4.  **순서를 유지하지 않음:** `HashMap`은 키 또는 삽입 순서를 유지하지 않는다. 키 또는 삽입 순서에 따라 항목을 저장하려면 `LinkedHashMap`을 사용한다.

`HashMap`은 `put(key, value)`, `get(key)`, `containsKey(key)`, `remove(key)`, `size()` 등의 메소드를 제공하여 사용자가 키-값 쌍을 쉽게 추가, 제거, 검색할 수 있다.

`HashMap`은 키를 기반으로 값을 빠르게 검색할 수 있다. 그러나 해시 충돌이 발생할 수 있으며, 이 경우 `HashMap`은 연결 목록이나 레드-블랙 트리와 같은 방법을 사용하여 충돌을 처리한다. 이로 인해 성능이 저하될 수 있습니다.

```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        // Create a HashMap object
        HashMap<String, Integer> people = new HashMap<String, Integer>();

        // Add keys and values (Name, Age)
        people.put("John", 32);
        people.put("Steve", 30);
        people.put("Angela", 33);

        // Display content using Iterator
        for (String i : people.keySet()) {
            System.out.println("Name: " + i + " Age: " + people.get(i));
        }
    }
}
```

# .put()
특정 키와 값을 맵에 추가하는데 사용된다. 이 메서드의 기본 형태는 다음과 같다.
```java
V put(K key, V value)
```
여기서, K는 키의 유형이며, V는 값의 유형이다.

이 메서드는 주어진 키가 맵에 이미 존재하는 경우, 그 키에 대응하는 이전 값을 반환한다. 만약 주어진 키가 맵에 존재하지 않는다면, `null`을 반환한다. 즉, 이 메서드는 키-값 쌍을 `HashMap`에 추가하고, 동일한 키에 대한 이전 값을 반환한다.

키에 대응하는 값을 갱신하려면, `put()` 메서드에 동일한 키와 새로운 값을 제공하면 된다. 이렇게 하면 `HashMap`은 자동으로 새로운 값을 이전 값으로 대체한다.

다음은 `put()` 메서드를 사용하는 간단한 예시다:
```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, Integer> map = new HashMap<>();

        // Adding key-value pairs to the HashMap
        map.put("One", 1);
        map.put("Two", 2);
        map.put("Three", 3);

        // Here the old value for the key "Two" was 2 which is replaced by the new value 22
        int oldValue = map.put("Two", 22);

        System.out.println("Old value for the key 'Two': " + oldValue);
        System.out.println("New map: " + map);
    }
}
```
이 코드를 실행하면 다음과 같은 출력을 볼 수 있다.

```java
Old value for the key 'Two': 2
New map: {One=1, Two=22, Three=3}
```
이 예시에서 보다시피, `put()` 메서드는 동일한 키에 대해 새로운 값을 설정하면서 이전 값을 반환하고 있습니다. 이것이 `put()` 메서드의 기본 작동 원리입니다.

# getOrDefault()

`getOrDefault(Object key, V defaultValue)`  메소드는 주어진 키에 대한 값을 반환한다. 만약 맵에 키가 존재하지 않는 경우, 이 메소드는 기본 값을 반환한다.

메소드의 선언은 다음과 같다.
```java
public V getOrDefault(Object key, V defaultValue)
```
여기서, `V`는 값의 타입을 나타낸다.

이 메소드는 키가 맵에 있으면 해당 키의 값을, 그렇지 않으면 기본 값을 반환한다. 이 메소드는 특정 키가 맵에 없는 경우 Null 포인터 예외를 방지하는 데 유용하다.

다음은 `getOrDefault()` 메소드를 사용하는 간단한 예시다:

```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, Integer> map = new HashMap<>();

        // Adding key-value pairs to the HashMap
        map.put("One", 1);
        map.put("Two", 2);
        map.put("Three", 3);

        // The key "Three" exists in the map
        int value1 = map.getOrDefault("Three", 30);
        System.out.println("Value for the key 'Three': " + value1);

        // The key "Four" does not exist in the map
        int value2 = map.getOrDefault("Four", 4);
        System.out.println("Value for the key 'Four': " + value2);
    }
}
```
이 코드를 실행하면 다음과 같은 출력을 볼 수 있다

```java
Value for the key 'Three': 3
Value for the key 'Four': 4
```
이 예시에서, 첫 번째 `getOrDefault()` 호출은 키 "Three"가 맵에 있으므로 해당 값인 3을 반환한다. 두 번째 `getOrDefault()` 호출은 키 "Four"가 맵에 없으므로 기본값인 4를 반환한다