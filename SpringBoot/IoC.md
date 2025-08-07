# IoC, 이게 뭐야?

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
이제 `OrderRepository`의 구현을 바꾸고 싶다면 `OrderService`도 수정해야 한다.

이제 OrderRepository의 구현을 바꾸고 싶다면 OrderService도 함께 수정해야 한다.
테스트할 때 가짜 저장소(FakeRepository)로 대체하고 싶어도 OrderRepository를 직접 생성하고 있기 때문에 교체가 어렵다.

이처럼 객체가 객체를 직접 생성해서 사용하는 방식은 코드의 유연성과 재사용성을 떨어뜨린다.

## IoC의 등장
IoC는 이런 문제를 해결하기 위해 등장한 개념이다.
제어의 역전이라는 말처럼, 객체 생성의 책임을 개발자가 아닌 **외부(컨테이너)**가 담당하게 되는 것이다.

```java
복사
편집
public class OrderService {
    private final OrderRepository orderRepository;

    public OrderService(OrderRepository orderRepository) {
        this.orderRepository = orderRepository;
    }
}
```
위 코드처럼 OrderService는 더 이상 OrderRepository를 직접 생성하지 않는다.
대신 외부에서 생성된 OrderRepository 객체를 주입받는다.
이렇게 하면 OrderRepository의 구현을 바꾸더라도 OrderService는 영향을 받지 않는다.

## IoC와 DI의 관계
여기서 자연스럽게 DI(Dependency Injection, 의존성 주입) 개념이 등장한다.
DI는 IoC의 한 구현 방법으로, 외부에서 필요한 의존 객체를 **주입(inject)**해주는 방식이다.

- IoC: 제어의 흐름을 외부로 넘긴다는 큰 개념

- DI: 그 IoC를 구현하는 하나의 방식 (생성자 주입, 필드 주입, 세터 주입 등)

## IoC를 적용하면 뭐가 좋을까?
- 유지보수 용이
객체 간의 결합도가 낮아져서 변경에 유연하게 대응할 수 있다.

- 테스트 쉬움
가짜 객체(Mock, Stub 등)로 주입해서 단위 테스트가 쉬워진다.

- 확장성 향상
다양한 구현체를 유연하게 교체 가능하다.

## 마무리

IoC는 처음 들으면 어렵게 느껴지지만, 결국은 객체 생성과 제어의 책임을 외부로 넘겨서 코드의 유연성과 확장성을 높이기 위한 설계 철학이다.
스프링 프레임워크 같은 자바 기반의 프레임워크는 이 IoC 개념을 바탕으로 동작한다.

ㄳㅎㄴㄷ

