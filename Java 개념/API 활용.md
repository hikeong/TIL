# 자바에서 꼭 알아야 할 API 클래스 3가지

자바를 배우면서 가장 먼저 만나게 되는 클래스들 중 하나는 `String`, `ArrayList`, `HashMap`입니다.
이 세 가지는 자바를 활용해서 실제 프로그램을 만들 때 거의 항상 등장하는 기본적인 API입니다.

이 글에서는 각각이 어떤 역할을 하는지, 어떻게 사용하는지를 간단한 예제와 함께 정리해봅니다.

---

## 1. String 클래스 – 문자열을 다루는 기본

`String`은 문자열 데이터를 처리할 때 사용하는 클래스입니다.  
우리가 `"Hello"`처럼 따옴표로 적는 값은 모두 `String` 객체로 처리됩니다.

자바에서 `String`은 불변(immutable) 객체이기 때문에, 문자열을 수정할 때마다 새로운 문자열이 생성된다. 이 점은 문자열을 다룰 때 반드시 기억해야 합니다.

### 주요 메서드 예시
```java
String text = "Java Programming";

System.out.println(text.length());           // 16
System.out.println(text.charAt(0));          // 'J'
System.out.println(text.substring(5));       // "Programming"
System.out.println(text.toLowerCase());      // "java programming"
System.out.println(text.contains("Java"));   // true

```

## ArrayList 클래스 – 크기가 자유로운 배열

자바의 배열(`Array`)은 크기가 고정되어 있다는 단점이 있습니다.
반면 `ArrayList`는 크기가 자동으로 늘어나기 때문에, 데이터를 동적으로 추가하거나 삭제할 수 있는 유연한 자료구조입니다.

`ArrayList`는 순서를 유지하며, 인덱스를 통해 값에 접근할 수 있다는 점에서 배열과 비슷하게 동작합니다.

### 사용 예시
```java
import java.util.ArrayList;

ArrayList<String> fruits = new ArrayList<>();
fruits.add("사과");
fruits.add("바나나");
fruits.add("딸기");

System.out.println(fruits.get(1));     // 바나나
fruits.remove("사과");
System.out.println(fruits.contains("사과"));  // false
System.out.println(fruits.size());     // 2

```

## HashMap 클래스 – 키와 값을 쌍으로 저장

`HashMap`은 데이터를 **키(Key)** 와 **값(Value)** 형태로 저장하는 자료구조입니다.
예를 들어 학생 이름과 점수를 함께 저장하거나, 사용자 ID와 정보를 연결할 때 자주 사용됩니다.

이 구조의 가장 큰 장점은 **키를 통해 값을 빠르게 검색**할 수 있다는 점입니다.
단, **저장된 순서는 보장되지 않는다**는 점에 주의해야 합니다.

### 사용 예시
```java
import java.util.HashMap;

HashMap<String, Integer> scores = new HashMap<>();
scores.put("하경", 90);
scores.put("하이경", 85);

System.out.println(scores.get("하경"));         // 90
scores.remove("하이경");
System.out.println(scores.containsKey("하이경")); // false

```

피드백 적극 받습니다
