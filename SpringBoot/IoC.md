# IoC란 뭘까?

일단 IoC가 무엇의 약자인지부터 살펴보자.<br> IoC란 Inversion of Controller의 약자로 한국말로 해석해보면 제어의 역전이란 뜻이다.

그런데 '제어의 역전'이란 말만 들으면 뭔가 모호하고 어렵게 느껴질 수 있다.  
그래서 예시와 함께 개념을 차근차근 풀어보려 한다.

---

## IoC, 왜 필요할까?

우리가 Java 프로그램을 만들 때, 하나의 객체는 다른 필요한 객체를 직접 생성해서 사용한다. <br>이런 방식은 단순할 수 있지만 시간이 지날수록 코드가 서로 얽히고 결함도가 높아져서 유지보수에 어려움을 겪게 된다.

예를 들어, `OverService `란 클래스가 `OverRepository`를 직접 생성해서 사용한다면 두 클래스는 강하게 연결되 있는 셈이다.

```java
public class OverService {
    private final OrderRepository orderRepository = new OrderRepository();
}
```
이제 `OrderRepository`의 구현을 바꾸고 싶다면 `OrderService`도 수정해야 한다. 테스트할 때 가

