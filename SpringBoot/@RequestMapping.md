### @RequestMapping

@RequestMapping에 대해 알아보자!

편의상 리퀘스트 매핑이라고 부르겠다. 리퀘스트 매핑은 GetMapping(”/board/save”) 이런식으로

url을 설정하게 되는데 예를 들어 /board/save가 글을 작성하는 기능이라 한다면 /board/read는 사용자가

글을 읽는 기능이라고 하자 둘 다 앞에 /board라는 url 붙는다 이걸  매번 코드를 작성할 때마다 붙이기 번거롭다 그래서 이걸 더 편안하게 작성하게 위해 존재하는 어노테이션이 @RequestMapping이다 

더 쉽게 설명하게 위해 코드로 설명을 하겠다

원래라면

```java
@Controller
public class BoardController {

	@GetMapping("/board/save")
	public String saveForm() {
	...
	}
	
	@GetMapping("/board/read")
	public String readForm() {
	...
	}

}
```

이렇게 적었을 것이다

하지만? @RequestMapping을 사용한다면

```java
@Controller
@RequestMapping("/board")
public class BoardController {
	
	@GetMapping("/save")
	public String saveForm() {
	...
	}
	
	@GetMapping("/read")
	public String readForm() {
	...
	}

}
```

이런식으로 /board라는 공통 url 경로를 잡아놓고 쓸 수 있다는 것이다
