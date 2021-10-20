# Spring Framework 

> 자바 웹 애플리케이션 개발을 위한 오픈 소스 프레임워크로, 기능을 미리 
클래스나 인터페이스 등으로 만들어 제공하는 반제품 

(이하 스프링)


## 스프링 특징



1. 경량 컨테이너의 기능을 수행
2. 제어 역행(Ioc) 기술을 이용해 애플리케이션 간의 느슨한 결합을 제어
3. 의존성 주입(Di) 기능
4. 관점 지향 기능(AOP)을 이용해 자원 관리
5. 영속성과 관련된 다양한 서비스를 지원
6. 수많은 라이브러리와 연동 기능 



MVC - DI 

트랜잰션 - AOP

인증과 권한 - Servlet Fiter 



용어정리 

의존성 주입 :  클래스 객체를 개발자가 코드에서 생성하지 않고 프레임워크가 생성하여 사용하는 방법

제어 역행 :  서블릿이나 빈 등 개발자가 코드에서 생성하지 않고 프레임워크가 직접 수행하는 방법

관점 지향 : 핵심 기능 회 부수 기능들을 분리 구현함으로써 모듈성을 증가시키는 방법 



DI  = Dependency Injection  
의존성 주입 

객체의 생성, 소멸, 의존 관계를 개발자가 직접 설정하는 것이 아니고, XML이나 애너테이션 설정을 통해 경량 컨데이너에 해당하는 스프링 프레임 워크가 제어 
코드를 단순화 하고, 유지보수를 쉽게 할수 있음 

Ioc =  





10 / 19  인프런으로 시작한 강의 ( Intell.J 시작 )







## 10 / 20 인프런으로 시작한 강의 

Welcom Page 만들기 

```
<!DOCTYPE HTML>
<html>
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<BODY>
Hello
<a href="/hello">hello</a>
</BODY>

```



> resources > static > index.html 작성 
>
> 올려두면  Welcome page 기능을 제공 



'HelloController'

```
package hello.hellospring.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;


@Controller
public class HelloController {


    @GetMapping("hello")
    public String hello (Model model) {
     model.addAttribute("data", "hello!!");
     return "hello";

    }
}

```



' resources / templates / hello.html '

```
<!DOCTYPE HTML>
<html>
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<BODY>
<p th:text="'안녕하세요.' + ${data}" > 안녕하세요. 손님 </p>
<a href="/hello">hello</a>
</BODY>
</html>
```





*동작 원리*

웹브라우저 > localhost:8080/hello > 내장 톰캣 서버 > helloController (스프링 컨테이너) > return : hello. model(data: hello) > viewResolver > templates/hello.html ( Thymleaf 템플릿 엔진처리 ) > hello.html (변환후)

* 컨트롤러에서 리턴값으로 문자를 반환하면 뷰 리졸버가 화면을 찾아서 처리 
* 스프링 부트 템플릿엔지 기본 viewName매핑 ( 'resources : templates/' +(viewName+'.html'))

스프링부트는 톰캣서버에서 받아서 (hello네? ) get방식으로 넘어오면 url 매칭 되어서 컨트롤러에 있는 메서드가 실행이 되고 model이 넘어오면 키는 data,  리턴의 이름 hello (resources와 같은데 ) 랜더링을 하고 

