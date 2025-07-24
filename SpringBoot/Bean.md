# Bean에 대하여

## 1. Bean의 정의

스프링 프레임워크에서 **Bean**이란, **스프링 컨테이너가 관리하는 객체**를 의미한다. 일반적으로 개발자가 직접 생성하는 객체가 아니라, 스프링이 객체의 생성과 생명주기를 관리한다.

즉, `@Component`, `@Service`, `@Repository`, `@Controller`, `@Bean` 등의 어노테이션이나 XML 설정을 통해 등록된 객체들이 Bean이다.

---

## 2. Bean을 사용하는 이유

스프링이 Bean을 관리하게 함으로써 얻는 이점은 다음과 같다:

- **의존성 주입(DI, Dependency Injection)**  
  객체 간의 의존성을 스프링이 대신 주입해 줌으로써, 결합도를 낮추고 코드의 유연성과 테스트 용이성이 증가한다.

- **객체 생명주기 관리**  
  스프링 컨테이너가 객체의 생성, 초기화, 소멸까지의 과정을 관리한다.

- **재사용성과 효율성**  
  기본적으로 싱글톤(Singleton) 스코프로 관리되기 때문에 하나의 인스턴스를 여러 곳에서 재사용할 수 있다.

---

## 3. Bean 등록 방법

### (1) 어노테이션 기반 등록

```java
@Component // 일반 컴포넌트
@Service   // 서비스 계층
@Repository // DAO 계층
@Controller // 컨트롤러 계층
```

이런 어노테이션을 클래스에 붙으면 자동으로 Bean이 등록된다 단, `@ComponentScan` 범위 내에 있어야 한다.

### (2) 자바 설정 파일에서 수동 등록 

```java
@Configuration
public class AppConfig {

    @Bean
    public UserService userService() {
        return new UserServiceImpl();
    }
}
```
직접 Bean 객체를 생성해 등록할 수 있으며, 복잡한 설정이 필요한 경우 유용하다.

### (3) XML 기반 설정 (구버전 방식)

```xml
<bean id="userService" class="com.example.UserServiceImpl" />
```
과거에는 XML 파일에 직접 Bean을 등록하는 방식이 일반적이었다.

## 4. Bean의 생명주기
스프링 Bean은 다음과 같은 생명주기를 가진다.

1. 스프링 컨테이너가 객체 생성
2. 의존성 주입 수행
3. 초기화 메서드 호출 (예: `@PostConstruct`)
4. 애플리케이션에서 사용
5. 소멸 직전 콜백 호출 (예: `@PreDestroy`)

이러한 라이프사이클은 필요에 따라 커스터마이징할 수 있다
