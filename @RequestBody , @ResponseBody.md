비동기통신을 하기위해서는 클라이언트에서 서버로 요청 메세지를 보낼 때, 본문에 데이터를 담아서 보내야 하고, <br/>
서버에서 클라이언트로 응답을 보낼때에도 본문에 데이터를 담아서 보내야 한다. 

이 **본문**이 바로 body 이다. <br/>
즉, 요청본문 requestBody, 응답본문 responseBody 을 담아서 보내야 한다. 

<br/>

@RequestBody 어노테이션과 @ResponseBody 어노테이션이 각각 HTTP요청 바디를 자바객체로 변환하고 자바객체를 다시 HTTP 응답 바디로 변환해준다. 

<br/>

#### @RequestBody 

<br/>

이 어노테이션이 붙은 파라미터에는 **http요청의 본문(body)이 그대로 전달**된다.  <br/>
일반적인 GET/POST의 요청 파라미터라면 @RequestBody를 사용할 일이 없을 것이다. <br/> 
반면에 xml이나 json기반의 메시지를 사용하는 요청의 경우에 이 방법이 매우 유용하다. <br/>
HTTP 요청의 바디내용을 통째로 자바객체로 변환해서 매핑된 메소드 파라미터로 전달해준다.  <br/>

<br/>


#### @ResponseBody 

<br/>

자바객체를 HTTP요청의 바디내용으로 매핑하여 클라이언트로 전송한다.
@ResponseBody 가 붙은 파라미터가 있으면 HTTP요청의 미디어타입과 파라미터의 타입을 먼저 확인한다.

즉, **@Responsebody 어노테이션을 사용하면 http요청 body를 자바 객체로 전달받을 수 있다**.

<br/>

#### @RestController

<br/>

@Controller와는 다르게 @RestController는 리턴값에 자동으로 @ResponseBody가 붙게되어 별도 어노테이션을 명시해주지 않아도 <br/>
HTTP 응답데이터(body)에 자바 객체가 매핑되어 전달 된다.

@Controller인 경우에 바디를 자바객체로 받기 위해서는 @ResponseBody 어노테이션을 반드시 명시해주어야한다. 

<br/>

+) @Controller와 @RestController의 차이점

@Controller의 역할은 Model 객체를 만들어 데이터를 담고 View를 반환하는 것이고, <br/>
@RestController는 단순히 객체만을 반환하고 객체 데이터는 JSON 또는 XML 형식으로 HTTP 응답에 담아 전송 <br/>
물론 @Controller도 @ResponseBody를 사용해서 만들 수 있지만 이런 방식은 RESTful 웹 서비스의 기본 동작이기 때문에 <br/>
Spring은 @Controller와 @ResponseBody의 동작을 조합한 @RestController를 도입

@Controller와 @RestController의 주요 차이점 중 하나는 @RestController를 표시하면 모든 메소드가 뷰 대신 객체로 작성

<br/>

#### @RequestBody / @ResponseBody 정리. 

<br/>

@RequestBody  
* HTTP 요청 몸체를 자바 객체로 전달받음
* HTTP 요청의 body 내용을 자바 객체로 매핑하는 역할

@ResponseBody 
* 자바 객체를 HTTP 응답 몸체로 전송함
* 자바 객체를 HTTP 요청의 body 내용으로 매핑하는 역할

<br/>

클라이언트에서 서버로 필요한 데이터를 요청하기 위해 JSON 데이터를 요청 본문에 담아서 서버로 보내면, <br/>
서버에서는 @RequestBody 어노테이션을 사용하여 HTTP 요청 본문에 담긴 값들을 자바객체로 변환시켜, 객체에 저장한다.
 
서버에서 클라이언트로 응답 데이터를 전송하기 위해 @ResponseBody 어노테이션을 사용하여 <br/>
자바 객체를 HTTP 응답 본문의 객체로 변환하여 클라이언트로 전송한다. 




