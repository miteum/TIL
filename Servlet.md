# Servlet 

> 서버쪽에서 실행되면서 클라이언트의 요청에 따라 동적으로 서비스를 제공하는 자바 클래스, 자바의 일반적인 특징을 모두 가진다.
>
> 자바 코드안에 HTML을 포함하고 있다.



< 특징 > 

* 서버 쪽에서 실행되면서 기능을 수행

* 기존의 정적인 웹 프로그램의 문제점을 보환하여 동적인 여러가지 기능을 제공

* 스레드 방식으로 실행

* 자바로 만들어져 자바의 특징을 가짐

* 컨터이너에서 실행

* 컨테이너 종류에 상관없이 실행

* 보안 기능을 적용하기 쉽다

* 웹 브라우저에서 요청시 기능을 수행 

  

## 서블릿 동작 방식



![](C:/Users/%EC%9D%B4%EB%AF%BF%EC%9D%8C/Desktop/image.png)



클라이언트가 URL을 클릭 > Http Request를 Container 전송 > Container는 HttpServletRequest, HttpServletResponse 두객체를 생성 > URL을 분석 어느 서블릿에 대해 요청을 한 것인지 찾고 > 해당 서블릿에 메소드를 호출 > 클라이언트의 POST,GET여부에 따라 doGet, doPost를 호출 > doGet, doPost 메소드는 동적페이지를 생성한 후 HttpServletResponse 객체에 응답을 보냄 >  응답이 끝나면 HttpServletRequest, HttpServletResponse  두객체 소멸





## Request, Response 

* Request : 클라이언트에서 넘어오는 데이터를 전달 받기 위한 객체 ( 서버에 어떤 정보를 요청하는 것 )
* Response: 서버에서 클라이언트 데이터를 전달하기 위한 객체  ( 웹 브라우저의 요청에 응답하는 것 )







## 서블릿 API 기능



**Servlet 인터페이스** : 

* javax.servlet 패키지에 선언*
* Servlet 관련 추상 메서드를 선언
* init(), service(), getServletInfo(), getSer
* vletConfig()를 선언

**ServletConfig 인터페이스** :

* javax.servlet 패키지에 선언
* Servlet 기능 관련 추상 메서드가 선언
* getInitParameter(), getInitParameterNames(), getServletContext(), getServletName()이 선언

**GenericServlet (추상)클래스** :

* javax.servlet 패키지에 선언
* 상위 두 인터페이스를 구현하여 일반적인 서블릿 기능을 구현한 클래스
* GenericServlet을 상속받아 구현한 사용자 서블릿은 프로토콜에 따라 각각 Service()를 오버라이딩해서 구현

**HttpServlet 클래스**

* javax.servlet.http 패키지에 선언
* GenericServlet을 상속받아 HTTP 프로토콜을 사용하는 웹 브라우저에서 서블릿 기능을 수행
* 웹 브라우저 기반 서비스를 제공하는 서블릿을 만들 때 상속받아 사용
* 요청시 service()가 호출되면서 요청 방식에 따라 doGet()이나 doPost()가 차례대로 호출됨

---



# HttpServlet 

* GenericServlet을 상속
* HTTP 프로토콜을 사용하는 서블릿 기능을 구현하는 클래스
* HttpServlet을 상속받아 HTTP 프로토콜로 동작하는 웹 브라우저의 요청을 처리하는 서블릿을 만들어 볼 것
* 그 외 다른 서블릿 구성요소들의 기능은 API 문서를 참고 
* 주요 메서드와 기능

>
>
>**메서드 기능** 
>
>| protected doDelete(HttpServletRequest req, <br/>HttpServletResponse resp) | 서블릿이 DELETE request를 수행하기 위해 service()를 통해서 호출 |
>| :----------------------------------------------------------: | :----------------------------------------------------------: |
>| protected doGet(HttpServletRequest req,<br/>HttpServletResponse resp) | 서블릿이 GET request를 수행하기 위해 service()를 통해서 호출 |
>| protected doHead(HttpServletRequest req,<br/>HttpServletResponse resp) | 서블릿이 HEAD request를 수행하기 위해 service()를 통해서 호출 |
>| protected doPost(HttpServletRequest req,<br/> HttpServletResponse resp) | 서블릿이 POST request를 수행하기 위해 service()를 통해서 호출 |
>| protected service(HttpServletRequest req,<br/> HttpServletResponse resp) | 표준 HTTP request를 public service()에서 전달받아 doXXX() 메서드를 호출 |
>| public service(HttpServletRequest req, <br/>HttpServletRequest resp) |     클라이언트의 request를 protected service()에게 전달      |

   

* **HttpServletRequest :** **Client --> Server**에게 보낸 요청을 추상화한 객체 

> http 프로토콜의 request 정보를 서블릿에게 전달하기위해 사용 헤더정보, 파라미터, 쿠키, URL등의 정보를 읽어 들이는 메소드를 가지고 있음 body의 stream을 읽어오는 메소드를 가지고 있음



* **HttpServletResponse :** **Server --> Client**에게 응답하기 위한 정보를 추상화한 객체

  > WAS는 어떤 클라이언트가 어떤 요청을 보냈는지 알고 있고, 해당 클라이언트에게 응답을 보내기 위한 HttpServletResponse 객체를 생성해 서블릿에게 전달 서블릿은 해당 객체를 이용해 content type, 응답코드, 응답 메시지등을 전송







