# Servlet과 DispatcherServlet 개념 정리

웹 애플리케이션을 개발할 때, 사용자의 요청을 받아 처리하고 응답을 반환하는 과정은 핵심적인 흐름 중 하나입니다.
Java 웹 개발을 할 때, 가장 기본이 되는 **Servlet**과 Spring MVC에서 확장한 형태인 **DispatcherServlet**에 대해 정리하겠습니다.

## 1. Servlet이란?

Servlet은 Java EE에서 제공하는 **웹 요청과 응답을 처리하기 위힌 지비 클래스입니다.**
주로 `HttpServlet` 클래스를 상속받아 구현하고, Request를 받아 서버에서 처리한 후, Response를 반환하는 구조로 동작합니다.

### 예시 코드

```java
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
   Override
   protected void doGet(HttpServletRequest req, HttpServletResponse resp)
          throws ServletException, IOException {
      resp.SetContentType("Text/plain");
      reso.getWriter().write("Hello, Servlet!");
  }
}
```

▶ Servlet의 주요 특징

- 클라이언트 요청에 따라 doGet(), doPost() 등의 메서드가 실행된다.
- 응답을 직접 구성해야 해서 코드가 복잡해질 수 있다.
- 웹.xml 또는 어노테이션으로 URL 매핑 설정이 팔요하다.

