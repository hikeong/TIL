# 자바에서 Getter와 Setter는 왜 필요할까?

Java에서는 클래스를 설계할 때 `getter`와 `setter` 메서드를 자주 사용하게 됩니다.
처음에는 IDE가 자동으로 만들어주는 형식적인 코드처럼 보일 수 있지만, 이 메서드들의 존재 이유는 꽤 중요합니다.

이 글에서는 Getter와 Setter가 어떤 역할을 하는지, 그리고 실제로 사용할 때 주의할 점은 무엇인지 정리해보려고 합니다.

---

## Getter와 Setter란?

- **Getter**: private 필드 값을 외부에서 읽을 수 있도록 제공하는 메서드  
- **Setter**: private 필드 값을 외부에서 변경할 수 있도록 제공하는 메서드

```java
public class User {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

자바는 기본적으로 **캡슐화(encapsulation)**를 지향하기 때문에, 필드를 private으로 선언하고 getter/setter를 통해 접근하는 구조를 권장합니다.

---

# 그럼 그냥 public 필드를 쓰면 되는 거 아닌가?

예를 들어 아래처럼 코드를 작성할 수도 있습니다.

```
public class User {
    public String name;
}
```
겉보기엔 문제가 없어 보이지만, 이렇게 하면 **객체 내부의 상태를 외부가 직접 조작**할 수 있게 됩니다. <br>
이렇게 되면 유지보수나 확장성 측면에서 위험할 수 있습니다.

