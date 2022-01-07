# Orientation

* [스프링 프로젝트 생성](/testPjt01)
* [처음 해보는 스프링 프로젝트](/testPjt02)

# 의존 객체

DI(Dependency injection): 객체를 만들어 외부에서 주입하는 방식.

예시) 배터리 일체형 vs 배터리 분리형

### 다양한 의존 객체 주입

* 생성자를 이용한 의존 객체 주입
* setter를 이용한 의존 객체 주입: name속성을 사용하며, 이름은 set을 제외한 글자로 + 소문자로 시작
* List타입 의존 객체 주입
* Map타입 객체 주입

# 설정 및 구현

### 웹 프로그래밍 설계 모델

* 웹 프로그래밍을 구축하기 위한 설계 모델

**Model1**

![](./img/img/1.PNG)

모델 1의 경우: 브라우저로부터 받은 요청을 수행하는 모든 기능을 모듈화하지 않고 하나로 만듬.

* 장점 : 개발속도 빠름
* 단점 : 유지보수 어려움

Model2: 

![](./img/img/2.PNG)

Controller, Service, DAO 모듈화. 
* 서비스: 기능
* DAO: DB와 연결
* View: 사용자에게 보여줌

DAO는 Model객체를 통해 DB와 통신. Controller는 View객체를 통해 브라우저에 response

이 모델을 MVC라함. Model, View, Controller

장점: 유지보수가 쉽다.


### 스프링 MVC 프레임워크 설계 구조

![](./img/img/3.PNG)

1. 브라우저의 request -> DispatcherServlet이 받음

2. DispatcherServlet이 HandlerMapping과 연결

3. 핸들러 맵핑은 많은 컨트롤러 중, 적합한 컨트롤러 선택

4. 다시 핸들러 맵핑이 디스패쳐 서블릿으로

5. 디스패쳐 서블릿은 핸들러 어답터에 요청

6. 핸들러 어답터는 컨트롤러에 있는 많은 메소드 중 적합한 메소드를 찾는다. 그 결과는 model이다.

7. 다시 디스패쳐 서블릿은 ViewResolver를 선택

8. 뷰리졸버는 가장 적합한 JSP페이지 View를 선택해준다

9. 마지막으로 View에서 응답이 브라우저에게 전달

### DispatcherServlet 설정

web.xml에 서블릿을 맵핑.

url패턴을 루트로



---
* 스프링 MVC 프레임워크 설계 구조
* DispatcherServelet 설정
* Controller객체 - @Controller
* Controller객체 - @Requestmapping
* Controller객체 - Model 타입의 파라미터
* View 객체
* 전체적인 웹프로그래밍 구조