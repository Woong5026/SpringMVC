### @RequestParam과 @PathVariable의 쓰임과 차이

<br/>

위 2개의 어노테이션은 http의 비연결성을 극복하고 데이터를 전달하기 위한 방법들 중 하나로, <br/> 
uri를 통해 전달된 값을 파라미터로 받아오는 역할

* uri를 통해 값을 전달하는 방식은 2가지

1. http://localhost:8000/board?page=1&listSize=10 <br/>
2. http://localhost:8000/board/1

1과 같은 방식은 쿼리 스트링이라 부르며 Get 방식의 통신을 할 때 주로 쓰인다.(파라미터의 값과 이름을 함께 전달하는 방식)

2와 같은 방식은 RESTful 방식이며 Rest 통신할 때 쓰인다.

<br/>

이 예시에서 쉽게 생각하면, 쿼리스트링을 사용하여 여러개의 값을 전달하는 <br/>
첫번째 방식은 @RequestParam을 통해 받아오고, 두번째 방식은 @PathVariable을 사용하여 받아올 수 있다

<br/>

### @RequestParam

RequestParam은 url에서는 파라미터로 값을 넘기고 Controller에서 RequestParam으로 값을 받는다

defaultValue - 값이 설정되지 않을 때 기본으로 설정할 값 <br/>
name - 바인딩할 요청 파라미터의 이름 <br/>
value -  name의 별칭 <br/>
required  - 필수 값인지 설정하는 값

```java

@RestController
public class TestController (){

  @GetMapping("/")
  public String test(@RequestParam("userId") String userId, 
                     @RequestParam("memo")   String memo){

    //아래와 같이 해당 변수에 파라미터값이 할당된다.
    //userId = "test"
    //memo   = "테스트"

    return "TEST 성공"
  }
  
}

```
<br/>

### @PathVariable

```java

@RestController
public class TestController (){

  @GetMapping("/{userId}/{memo}")
  public String test(@PathVariable("userId") String userId,
                     @PathVariable("memo")   String memo){

    //아래와 같이 해당 변수에 파라미터값이 할당된다.
    //userId = "test"
    //memo   = "테스트"

    return "TEST 성공"
  }
  
}

```


### 정리 요약

<br/>

@RequestParam 과 @PathVariable은 둘 다 데이터를 받아오는 데에 사용한다! <br/>
@RequestParam은 uri를 통해 전달된 값이 아니더라도, ajax 요청을 통해 body에 담아온 데이터를 여러 타입으로 받을 수 있다.


<br/><br/>

@PathVariable은 아무래도 RESTful 방식에 맞게 좀 더 직관적이다. <br/>
@RequestParam는 null 값 허용이나 키:밸류 값으로 보낼 수 있다는 점 정도로 들 수 있다. <br/>
꼭 정답은 없으니 상황에 맞게 사용하면 좋을 거 같다. <br/>







