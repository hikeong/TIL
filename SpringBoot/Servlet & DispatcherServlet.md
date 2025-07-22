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

## 2. DispatcherServlet이란?

DispatcherServlet은 **Spring MVC에서 요청을 처하는 중앙 Servlet**입니다.
HTTP 요청은 DispatcherServlet을 거쳐 알맞은 컨트롤러로 전달되고, <br>처리 결과는 view로 매핑되어 Response로 전송됩니다.

▶DispatcherServlet의 주요 처리 과정

1. 요청 접수
   - 클라이언트로부터 HTTP 요청이 들어오면 DispatcherServlet이 가장 먼저 요청을 받음
   - web.xml or Java Config를 통해 URL 패턴을 지정할 수 있음
   - 일반적으로 "/"로 설정해 모든 요청을 처리함

2. 컨트롤러 매핑
   - HandlerMapping을 통해 요청 URL에 매핑된 핸들러를 조회함
   - RequestMappingHandlerMapping이 가장 많이 사용됨
   - @RequsetMapping 어노테이션을 통해 매핑됨

3. 핸들러 어댑터 조회
   - 해당 핸들러를 실행할 수 있는 HandlerAdapter를 조회함
   - RequestMappingHandlerAdapter가 주로 사용됨
   - @RequestMapping 기반 컨트롤러를 처리함

4. 핸들러 실행
   - HandlerAdapter를 통해 핸들러를 실행함
   - 컨트롤러의 비즈니스 로직이 실행되고 ModelAndView를 반환함

5. 뷰 리졸버
   - ViewResolver를 통해 뷰의 논리 이름을 실제 뷰 객체로 변환함

6. 뷰 렌더링
   - View 객체를 통해 실제 뷰를 렌더링함
   - JSP, Thymeleaf 등 다양한 템플릿 엔진을 지원함
   
 
