# DI (Dependency Injection)

## 1. DI란 뭘까?
DI는 의존성 주입이라고 불리고,<br>객체가 필요로 하는 의존 객체를 직접 생성하지 않고, 외부에서 주입받는 방식이다.

이 방식을 사용하게 되면 객체들 간의 결합도를 낮추고 코드의 유지보수성과 테스트 용이성을 높일 수 있다.
예를 들어 어떤 클래스가 특정 서비스를 사용한다고 가정해보자
직접 new 키워드로 객체를 생성하게 되면 해당 클래스는 그 서비스에 강하게 묶이게 된다.
하지만 외부에서 주입을 받는다면 다른 구현체로 바꾸기도 쉬워지고 테스트 시에는 가짜 객체를 넣을 수 있다.

```java
public class Car {
   private Engine engine;

   public Car() {
      this .engine  = new GasEngine();
  }
}
```
이 코드는 Car가 GasEngine에 강하게 의존하고 있다.
하지만 DI를 사용하면 이렇게 바꿀 수 있다.

```java
public class Car {
   private Engine engine;

   public Car (Engine engine) {
      this.engine = engine;
   }
}
```
이렇게 하면 Car는 Engine 인터페이에만 의존하게 되고 
주입받는 방식에 따라 다양한 구현체를 유연하게 사용할 수 있다.

## 2. Spring에서의 DI

스프링 프레임워크에서는 DI를 아주 자연스럽게 구현할 수 있다 
대표적으로 **생성자 주입, 필드 주입, Setter 주입** 방식이 있다. 그중에서도 생성자 주입이 가장 권장하는 방식이다.

### 생성자 주입 예시 

```java
@Component
public class OrderService {
   private final PaymentService patmentService;

   @Autowired
   public OrderService(PaymentService paymentService) {
      this.paymentService = paymentService;
   }
}
```
스프링이 `PaymentService`타입의 빈을 자동으로 찾아서 `OrderService`에 주입해준다.
@Autowired는 생략도 가능하고 생성자가 하나뿐일 경우 자동으로 주입된다.

## 왜 DI를 써야하는데?

- 유지보수가 쉬움
- 테스트하기 쉬움
- 유연성이 생김

## 마무리

DI는 스프링의 핵심 개념 중 하나이다.
나도 처음엔 DI가 뭔가 싶고 낯설었다 하지만 프로젝트 구조가 커질 수록 DI의 소중함이 느껴진다.
결함도를 낮추고 유연한 코드를 만들고 싶다면 DI를 자연스럽게 익혀놓도록 하자!
