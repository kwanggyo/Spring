# Spring

:bulb: 참고 : 인프런 - 스프링 입문 강의

**자바 플랫폼을 위한 오픈소스 애플리케이션 프레임워크**

엔터프라이즈급 애플리케이션을 개발하기 위한 모든 기능을 종합적으로 제공하는 경량화된 솔루션이다.

🤔 엔터프라이즈급?

- 개발이란 기업을 대상으로 하는 개발이다. 즉, 대규모 데이터 처리와 트랜잭션이 동시에 여러 사용자로부터 행해지는 매우 큰 규모의 환경을 엔터프라이즈 환경이라 말한다.

**Spirng Framework는 경량 컨테이너로 자바 객체를 담고 직접 관리한다.**

객체의 생성 및 소멸 그리고 라이프 사이클을 관리하며 언제든 Spring 컨테이너로부터 필요한 객체를 가져와 사용할 수 있다.

Spring Framework는 IOC기반이다.

## IOC

- IOC는 Inversion of Control의 약자로 말 그대로 제어의 역전이다.
- 일반적으로 지금까지 프로그램은 객체 결정 및 생성 → 의존성 객체 생성 → 객채 내의 메소드 호출 하는 작업을 반복했다. 이는 각 객체들이 프로그램의 흐름을 결정하고 각 객체를 구성하는 작업에 직접적으로 참여한 것을 말한다. **즉, 모든 작업을 사용자가 제어하는 구조!**
- 하지만 IOC에서는 이 흐름의 구조를 바꾼다. IOC에서의 객체는 자기가 사용할 객체를 선택하거나 생성하지 않는다. 또한 자신이 어디서 만들어지고 어떻게 사용되는지 또한 모른다. 자신의 모든 권한을 다른 대상에 위임함으로써 제어 권한을 위임 받은 특별한 객체에 의해 결정되고 만들어진다. **즉, 제어의 흐름을 사용자가 컨트롤 하지 않고 위임한 특별한 객체에 모든 것을 맡기는 것이다.**
- **IOC란 기존 사용자가 모든 작업을 제어하던 것을 특별한 객체에 모든 것을 위임하여 객체의 생성부터 생명주기 등 모든 객체에 대한 제어권이 넘어 간 것을 IOC, 제어의 역전 이라고 한다.**

### **IOC의 구성요소 DI와 DL**

IOC는 DI와 DL의 의해 구현된다.

**DL(Dependency Lookup) - 의존성 검색**

- 컨테이너에서는 객체들을 관리하기 위해 별도의 저장소에 빈을 저장하는데 저장소에 저장되어 있는 개발자들이 컨테이너에서 제공하는 API를 이용하여 사용하고자 하는 빈을 검색하는 방법이다.

**DI(Dependency Injection) - 의존성 주입**

- 의존성 주입이란 객체가 서로 의존하는 관계가 되게 의존성을 주입하는 것이다.
- 객체지향 프로그램에서 의존성 이란 하나의 객체가 어떠한 다른 객체를 사용하고 있음을 의미한다.

**각 클래스 사이에 필요로 하는 의존관계를 빈설정 정보를 바탕으로 컨테이너가 자동으로 연결**해 주는 것이다.

<br>

# 프로젝트 생성

## 스프링 시작

https://start.spring.io/

스프링부트 기반으로 스프링 프로젝트를 만들어주는 사이트

### Maven, Gradle

버전 설정

필요한 라이브러리를 땡겨서 오고 빌드하는 라이프사이클까지 관리해주는 툴

과거에는 메이븐을 많이 썼지만 요즘에는 그래들을 많이 쓴다.

### Spring Boot

버전을 선택

SNAPSHOT : 아직 만들고 있는 버전

M1 : 정식 릴리즈된 버전이 아님

### Project Metadata

Group : 보통 기업명을 적어줌

Artifact : 빌드된 결과물(프로젝트 명)

Dependencies : 어떤 라이브러리를 사용할 것인지

- spring Web
- Thymeleaf : HTML을 만들어주는 템플릿  엔진(회사마다 다름)

## 프로젝트 구조

main과 test 폴더가 나누어져 있다 : test코드가 중요하다는 것

src/main/resource : 자바 코드를 제외한 xml이나 properties 등 설정 파일들이 들어가있다.

build.gradle : 중요! 옛날에는 직접 작성했지만 요즘은 start.spring.io를 통해서 작성한다(개발자 친화적으로 바뀜)

- gradle : 버전설정, 라이브러리를 가져온다(처음 접하는 수준에서는 이정도만)
- mavenCentral이라는 공개된 사이트에서 dependencies에 있는 라이브러리를 다운 받는다. 적혀있는 부분에 url 작성도 가능

## 기본 코드 실행

✅ java는 main 메소드로부터 모든 프로세스가 실행된다.

실행을 시키면 Tomcat started on port(s) : 8080 (http) ~ 가 떠야한다.

- SpringBootApplication이 Tomcat이라는 웹서버를 내장하고 있다.
- Tomcat이라는 웹서버를 자체적으로 띄우면서 스프링부트가 같이 올라온다.
- localhost:8080에 들어갈 수 있으면 성공(지금은 에러가 떠 있어야 정상 → 아무것도 없기 때문에)

## 실행 참고

인테리제이를 쓰면 빌드가 자바를 직접 실행하는 것이 아니라 Gradle을 통해서 실행될 때가 있다.

Gradle을 통해서 Run을 하면 느릴 때가 있는데 아래의 설정을 통해 Gradle을 통하지 않고 Intellij에서 자바를 바로 띄워서 돌린다.

- settings or preference에 들어가서 Gradle 검색 → Bulid and run 부분의 Bulid and run using, Run tests using 두 부분을 Intellij로 바꾼다.

<br>

# 라이브러리

External Libraries : 가져온 라이브러리들

- 우리가 설정한 것은 3개지만 확인해보면 엄청 많다.
- Gradle이나 Maven 같은 빌드 툴들은 의존관계를 관리해준다(함께 다운로드)
- ex) spring-boot-starter-web을 가져오게 되면 tomcat, spring-webmvc 등 의존관계가 있는 것들을 다 가져오게 된다.
- 오른쪽의 gradle 버튼 → dependencies : 라이브러리들의 의존 관계
  - spring 개발 초기에는 웹서버라는 것을 직접 서버에 설치(tomcat 같은 것)하고 자바 코드를 밀어넣는 식으로 개발
    - 웹서버와 개발라이브러리가 분리가 되어있었다.
    - 그래서 tomcat 서버에 들어가서 설치했었다.
  - 요즘에는 소스 라이브러리에서 이런 웹서비스를 들고 있다(임베디드 : 내장하고 있다, tomcat-embed ~ 확인 가능)
    - 실행만 해도 웹서버가 뜨고 8080으로 들어갈 수 있다.
    - 라이브러리를 빌드해서 웹서버에 올리면 끝

### SpringBoot Library

spring-boot-starter-web

- spring-boot-starter-tomcat : 톰캣(웹서버)
- spring-webmvc : 스프링 웹 MVC

spring-boot-start-thymeleaf : 타임리프 템플릿 엔진(View)

spring-boot-starter(공통) : 스프링부트 + 스프링코어 + 로깅

- spring-boot
  - spring-core
- spring-boot-starter-logging
  - 로그에 관해서 궁금한 점이 있으면 아래 두개 검색!(이 두가지 조합으로 많이 사용)
  - logback : 실제 로그를 어떤 구현체로 출력할지
  - slf4j : 인터페이스

✅ **log(spring-boot-starter-logging)**

현업에서 일하는 사람들은 system.out.println으로 출력하면 안된다. → log로 출력해야한다.

로그로 남겨야 심각한 에러를 모아볼 수 있고 로그 파일들을 관리할 수 있다.

### Test Library

spring-boot-starter-test

- junit : 테스트 프레임워크(핵심)
- mockito : 목 라이브러리
- assertj : 테스트 코드를 좀 더 편하게 작성하게 도와주는 라이브러리
- spring-test : 스프링 통합 테스트 지원

<br>

# View 환경설정

자료를 찾을 때는 https://spring.io/projects/spring-boot#learn 여기서 맞는 버전의 Doc에서 찾기 !

템플릿엔진을 사용하면 정적인 페이지를 원하는 대로 바꿀 수 있다. → Thymeleaf 사용 예정

Cotroller : 웹 어플리케이션에서 첫 진입점

```java
@Controller
public class HelloController {

    @GetMapping("hello")    // 웹 어플리케이션에서 /hello라고 들어오면 이 메소드를 호출한다.
    public String hello(Model model) {  // 스프링이 모델을 만들어서 넣어준다. model(data:hello!!)
        model.addAttribute("data", "hello!!");
        return "hello"; 
    }
}
```

- return의 이름이 hello -> resource에 있는 hello로 가서 렌더링 하라는 것 data는 model을 넘김
- 기본적으로 templates 밑에 있는 것을 찾음 : 스프링 기본 동작으로 세팅 되어있음
- 컨트롤러에서 리턴 값으로 문자를 반환하면 뷰 리졸버(viewResolver)가 화면을 찾아서 처리한다.
  - 스프링 부트 템플릿엔진은 기본적으로 viewName을 매핑 -> 여기서 viewName은 'hello'
  - `resources:templates/` + {viewName} + `.html`이 열리게 된다.

### 참고

spring-boot-devtools 라이브러리를 추가하면, html 파일을 컴파일만 해주면 서버 재시작 없이 View 파일 변경이 가능하다.

Intellij 컴파일 방법 : 메뉴 build → Recompile

<br>

# 빌드하고 실행하기

### 빌드

현재 프로젝트가 있는 폴더에서 window : gradlew.bat build

💣 자바 11 버전이 아니라고 빌드가 안되는 에러 발생

→ gradlew.bat 안에 JAVA_HOME 부분이 문제였다!

- Intellij 에서는 11로 연결해놨기 때문에 빌드가 된 것이고 로컬에서 JAVA_HOME은 8로 등록되어 있어서 생긴 문제!

- ZULU_HOME을 11로 설정하여 환경변수에 넣어주고 해결되나 싶었으나 인식을 못해서 경로를 넣어서 해결했다!

  - gradlew.bat 파일 수정

  ```java
  :findJavaFromJavaHome
  set JAVA_HOME=C:/program files/zulu/zulu-11
  set JAVA_EXE=%JAVA_HOME%/bin/java.exe
  ```

빌드가 안될 경우 gradlew.bat clean build 사용

- build 폴더를 지우고 다시 빌드

### 실행

실행 폴더로 이동 : hello-spring > build > libs

명령어 : java -jar hello-spring-0.0.1-SNAPSHOT.jar

<br>

# 스프링 웹 개발 기초

**정적 컨텐츠**

: 서버에서 하는 것 없이 파일을 웹 브라우저에 그대로 내려주는 것

**MVC와 템플릿 엔진**

: 가장 많이 하는 방식으로 과거의 JSP, PHP가 템플릿 엔진(서버에서 프로그래밍을 통해 동적으로 바꿔서 내려주는 것)

→ 그것을 하기 위해서 Model, View, Controller

정적 컨텐츠와 차이는 정적 컨텐츠는 파일을 그대로 전달해주지만 MVC는 서버에서 변형을 통해 바꿔서 html을 주는 것이다.

**API**

: 안드로이드나 IOS와 개발을 해야한다면 html이 아닌 JSON이라는 데이터 구조 포맷으로 클라이언트한테 전달하는 방식, Vue나 React에도 많이 사용, 서버끼리 통신하는 경우 사용

## 정적 컨텐츠(Static Content)

static 밑에 hello-static.html을 만들고 서버를 켜서 http://localhost:8080/hello-static.html로 접속하면 나온다.

- 대신 프로그래밍을 할 수는 없고 그대로 반환한다.
- 요청(localhost:8080/hello-static.html)을 하면 컨트롤러에서 Mapping된 컨트롤러(**컨트롤러에서 우선순위를 가짐**)를 찾는다 → 없으면 resources에 있는 hello-static.html을 찾는다. → 있으면 반환

## MVC와 템플릿 엔진

MVC : Model, View, Controller

- Model : 화면에 필요한 것을 담아서 넘겨줌
- View : 화면과 관련된 일, 관심사를 분리(역할과 책임)
- Controller : 비지니스 로직과 관련, 내부적인 것을 처리

### Controller

```java
@Controller
public class HelloController {

    @GetMapping("hello-mvc")
    public String helloMvc(@RequestParam("name") String name, Model model) {
        model.addAttribute("name", name);
        return "hello-template";
    }
}
```

### View

- resoures/template/hello-template.html

```java
<!DOCTYPE HTML>
<html>
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
    <p th:text="'안녕하세요. ' + ${data}">Hello! empty</p>
</body>
</html>
```

## API

정적 컨텐츠 방식을 제외하면 `HTML로 주는 것`과 `API 방식으로 데이터를 바로 주는 것`이 있다.

객체를 반환한다.

🥕 `Art + insert` : Getter와 Setter를 자동 완성으로 만들어줄 수 있다.

- HTML 형식으로 반환

```java
@GetMapping("hello-string")
@ResponseBody   // HTTP분에 의 body부데이터를 직접 넣어주겠다는 뜻(응답 body 부분에 넣어줌)
public String helloString(@RequestParam("name") String name) {
    return "hello " + name; // 데이터를 그대로 넘겨준다.
    // 이전의 템플릿 엔진은 화면을 가지고(View Template) 조작
}
```

- JSON 형식으로 반환

```java
@GetMapping("hello-api")
@ResponseBody
public Hello helloApi(@RequestParam("name") String name) {
    Hello hello = new Hello();
    hello.setName(name);
    return hello;   // 객체를 반환
}

static class Hello {    // 클래스 안에서 클래스를 사용할 수 있음, HelloController.Hello 이런식으로
    private String name;

    public String getName() {   // 꺼낼 때
        return name;
    }

    public void setName(String name) {  // 넣을 때
        this.name = name;
    }
}
```

**xml**

- 무겁고 태그를 써야 한다.
- "<HTML></HTML>"

**JSON**

- 심플하다.
- 최근에 많이 사용(거의 통일)
- spring에서 객체로 반환 + ResponseBody를 사용하면 기본으로 JSON을 반환한다.

`**@ResponseBody`를 사용하면**

- HTTP의 Body에 문자 내용을 직접 반환한다.
- viewResolver 대신HttpMessageConverter가 동작한다.
  - 기본 문자 처리 : StringHttpMessageConverter
  - 기본 객체 처리 : MappingJackson2HttpMessageConverter
  - byte 처리 등 기타 여러 HttpMessageConverter가 기본으로 등록되어 있다.
- 참고 : 클라이언트의 HTTP Accept 헤더(어떤 form으로 받을지)와 서버의 컨트롤러 반환 타입 정보를 조합해서 HttpMessageConverter가 선택된다.

<br>

# 회원 관리 예제

## 비지니스 요구사항 정리

데이터 : 회원 ID, 이름

기능 : 회원 등록, 조회

아직 DB가 정해지지 않음(가상의 시나리오)

### 일반적인 웹 애플리케이션 계층 구조

**컨트롤러** : 웹 MVC의 컨트롤러 역할, Api 만들기

**서비스** : 핵심 비즈니스 로직 구현, 예) 회원은 중복 가입이 안됨

**리포지토리** : 데이터베이스에 접근, 도메인 객체를 DB에 저장하고 관리

**도메인** : 비즈니스 도메인 객체, 예) 회원, 주문, 쿠폰 등 주로 데이터베이스에 저장하고 관리

### 클래스 의존 관계

MemberService → MemberRepository(interface)

Memory MemberRepository → MemberRepository(interface)

- 아직 데이터저장소가 선정되지 않았기 때문에 인터페이스로 구현 클래스를 변경할 수 있도록 설계
- 데이터 저장소는 RDB, NoSQL 등 다양한 저장소를 고민 중인 상황으로 가정
- 개발을 진행하기 위해서 초기 개발 단계에서는 구현체로 가벼운 메모리 기반의 데이터저장소를 사용

## 회원 도메인과 레포지토리 만들기(domain)

private 변수와 Getter, Setter를 만든다.

static은 인스턴스와 상관없이 클래스 레벨에 붙는다.

## 회원 리포지토리 테스트 케이스 작성(repository)

개발한 기능을 실행해서 테스트 할 때 자바의 main 메서드를 통해서 실행하거나, 웹 어플리케이션의 컨트롤러를 통해서 해당 기능을 실행한다. 이러한 방법은 준비하고 실행하는데 오래 걸리고, 반복 실행하기 어렵고 여러 테스트를 한번에 실행하기 어렵다는 단점이 있다.자바는 JUnit이라는 프레임워크로 테스트를 실행해서 이러한 문제를 해결한다.

### 테스트 실행

클래스 단위로도 테스트 실행이 가능하다.

테스트 순서는 보장이 되지 않는다

- 모든 테스트는 순서와 상관없이 테스트 별로 따로 동작하게 설계 해야한다.(의존적으로 설계하면 안된다.)

- 하나의 Test가 끝날 때마다 저장소나 공용 데이터를 지워줘야 한다.

  - MemoryMemberRepository에 클리어 하는 함수 추가

  ```java
  public void clearStore() {
      store.clear();
  }
  ```

  - MemoryMemberRepositoryTest에서 호출

  ```java
  @AfterEach  // Test가 끝나고 호출 되는 메서드
  public void afterEach() {
      repository.clearStore();
  }
  ```

개발 → 테스트 케이스

테스트 케이스 → 개발 : 테스트 주도 개발 TDD(Test Driven Development)

테스트가 수십, 수백개면 빌드를 하거나 Gradlew.bat으로 테스트

많은 사람들이 함께 개발하는 경우, 테스트 코드가 없이 개발하는 것이 거의 불가능하다.

## 회원 서비스 개발(service)

비지니스에 가까운 용어를 써야한다.(join, findMembers 등)

서비스 : 비지니스에 의존적으로 설계

리포지토리 : 단순히 개발적으로 용어를 선택

🥕 `Ctrl + Art + V` : Extract Variable

🥕 `Ctrl + Art + M` : Extract Method

## 회원 서비스 테스트

🥕 `Art + Enter` → create test

- Testing library : JUnit5
- 만들고 싶은 테스트 함수 선택

Test 함수의 변수명은 한글을 사용해도 된다.

실제 동작하는 코드들은 한글 x

빌드할 때 테스트 코드는 실제 코드에 포함되지 않는다.

Test는 정상 flow도 중요하지만 예외 flow가 더 중요하다!

given(무언가 주어지고), when(실행), then(결과)으로 나누어서 작성하는 것이 좋다.(주석 이용)

각각의 인스턴스 객체를 생성해서 테스트 하는 것이 아니라 외부에서 넣어주도록 service의 코드를 바꾼다!

→ `Dependency Injection(의존성 주입)` : 표준을 정의할 수 있고 정의된 표준을 바탕으로 같은 설계를 하게 해준다.

- 재사용성 증가, 테스트 용이, 코드 단순화, 종속적이던 코드 감소(변경에 민감하지 않음), 가독성 증가 등

<br>

# 스프링 빈과 의존 관계

### 스프링 빈?

**Spring IoC 컨테이너가 관리하는 자바 객체를 빈(Bean)**이라는 용어로 부른다.

`Spring IoC 컨테이너가 관리하는 자바 객체를 빈(Bean)`이라는 용어로 부른다.

우리가 new 연산자로 어떤 객체를 생성했을 때 그 객체는 빈이 아니다.

ApplicationContext.getBean()으로 얻어질 수 있는 객체는 빈이다.

즉 Spring에서의 빈은 ApplicationContext가 알고있는 객체, 즉 **ApplicationContext가 만들어서 그 안에 담고 있는 객체**를 의미한다.

웬만한 것들은 다 스프링 빈으로 등록해서 사용해야 한다.(장점이 많음)

main이 들어가 있는 package에서 뒤져서 스프링 빈으로 등록한다.

- 현재 예제에서는 hello.hellospring package
- 하위 패키지가 아니거나 동일한 것은 컴포넌트 스캔하지 않는다.

스프링은 스프링 컨테이너에 스프링 빈을 등록할 때, 기본으로 싱글톤으로 등록한다(유일하게 하나만 등록해서 공유한다)

→ 따라서 같은 스프링 빈이면 모두 같은 인스턴스이다.(물건 주문을 할 때 다시 등록하는 것이 아닌 등록 되어 있는 것을 가져온다)

설정으로 싱글톤이 아니게 설정할 수 있지만 특별한 경우를 제외하면 대부분 싱글톤을 사용한다.

## 컴포넌트 스캔과 자동 의존관계 설정

회원 컨트롤러가 회원서비스와 회원 리포지토리를 사용할 수 있게

화면을 붙이려면 Controller와 View template 필요 → MemberController 필요 → MemberService를 통해 회원가입 및 조회가 가능해야한다 ⇒ 이것을 의존관계가 있다고 표현

MemberService의 인스턴스를 계속 생성할 필요 없이 하나로 쓰면 된다.

```java
private final MemberService memberService = new MemberService(); 
```

위와 같이 쓸 필요 없이 Spring Container에 등록하면 하나만 등록된다. + 부가적인 효과

### Controller Annotation

스프링을 실행하면 스프링 컨테이너라는 통이 생김 -> MemberController 객체를 생성해서 넣어둔다.

이것을 스프링 빈이 관리된다고 표현

🥕 `Ctrl + Inssert` → Constructor : 생성자

### **스프링의 정형화된 패턴**

외부 요청을 받고(**Controller**) 비지니스 로직을 만들고(**Service**) 데이터를 저장(**Repository**)

**@Autowired**

스프링이 관리하는 객체에서만 동작한다. 스프링 빈으로 등록하지 않고 내가 직접 생성한 객체에서는 동작하지 않는다.

생성자가 하나 일 경우 생략 가능하다.

ex) MemberController가 생성 될 때 스프링 빈에 등록되어 있는 memberService 객체를 가져다 넣어준다.(Dependency Injection)

```java
@Controller // 스프링을 실행하면 스프링 컨테이너라는 통이 생김 -> MemberController 객체를 생성해서 넣어둔다.
// 이것을 스프링 빈이 관리된다고 표현
// 컨트롤러와 서비스를 연결
public class MemberController {

    private final MemberService memberService;

    @Autowired  // 생성자에 적혀있으면 memberService에 스프링이 스프링 컨테이너에 있는 memberService를 가져다가 연결해준다.
    public MemberController(MemberService memberService) {  // MemberController가 생성 될 때 스프링 빈에 등록되어 있는 memberService 객체를 가져다 넣어준다(DI)
        this.memberService = memberService;
    }
}
```

### 스프링 빈을 등록하는 2가지 방법

1. **컴포넌트 스캔과 자동 의존관계 설정**

   @Component가 있으면 스프링 빈으로 자동 등록된다(스프링 객체를 생성해서 스프링 컨테이너에 등록을 해준다.)

   @Controller, @Service, @Repository 들어가서 보면 @Component가 있다.(자동 등록)

   @AutoWired는 연결해주는 것

2. **자바 코드로 직접 스프링 빈 등록하기**

## 자바 코드로 직접 스프링 빈 등록하기

과거에는 xml로 작성했지만 지금은 거의 자바 코드로 작성

@Service와 @Repository Annotation을 지우고 Service에 ServiceConfig를 만든다.

```java
@Configuration
public class SpringConfig {

    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }

    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }
}
```

### 참고

DI에는 필드 주입, setter 주입, 생성자 주입 이렇게 3가지 방법이 있다.(Controller 코드에서 확인) 의존관계가 실행 중에 동적으로 변하는 경우(Runtime이 떠있는데 변경하는 경우)는 거의 없으므로 **생성자 주입을 권장**한다. → 변경이 있을 경우 Config를 수정해서 다시 올린다.

- 필드 주입 : 별로 좋지 않다. → 중간에 바꿀 수 있는 방법이 없다.
- setter 주입 : 누군가가 MemberController를 호출했을 때 Public으로 열려있어야한다. 서비스를 중간에 바꿀 이유가 없는데 Public하게 노출 되어 있다. → 잘못 바꾸게 되면 문제(애플리케이션 로딩 때 바꾸고 한번 세팅이 되면 바꾸지 않음), 아무개발자나 호출할 수 있게 열려있는 것(호출하지 않아야 할 메서드는 호출되면 안됨)
- **생성자 주입** : 권장하는 방법(생성 후 변경하지 못하도록 막는다.)

실무에서는 주로 정형화된 컨트롤러, 서비스, 리포지토리(일반적으로 작성하는 것) 같은 코드는 컴포넌트 스캔을 사용한다. 그리고 정형화되지 않거나, 상황에 따라 구현 클래스를 변경해야 하면 설정을 통해 스프링 빈으로 등록한다.

<br>

# 회원 관리 예제 - 웹 MVC 개발

## 회원 웹 기능 - 홈 화면 추가

요청이 오면 스프링 컨테이너에서 관련 컨트롤러가 있는지 찾은 후에 없으면 static 파일(index.html)을 찾는다.

## 회원 웹 기능 - 등록

template의 input tag - name : 서버로 넘어갔을 때의 Key 값

## 회원 웹 기능 - 조회

🥕 `Ctrl + E` : Recent files

현재까지는 DB가 아니라 Memory에 저장하기 때문에 서버를 껐다가 키면 데이터가 날아간다.

<br>

# 스프링 DB 접근 기술

JPA를 사용하면 객체를 바로 DB에 쿼리 없이 저장, 관리가 가능하다.

스프링 데이터 JPA : JPA를 편리하게 쓸 수 있도록 감싼 기술

## H2 데이터베이스 설치

설치 사이트 : [H2 Database Engine](https://www.h2database.com/html/main.html)

실행 : window : h2.bat 실행 → 페이지가 계속 로딩 중인 경우에는 IP 주소 부분을 localhost로 바꿔준다.

최초에는 데이터베이스 파일을 만들어야 한다.

- JDBC URL : ~test 부분은 파일 경로를 의미

연결을 눌러서 실행 → cmd에서 사용자 > dir 했을 때 test.mv.db가 있어야 한다.

이후에는 파일로 접근하는 것이 아니라 jdbc:h2:tcp://localhost/~/test(소켓을 통해 접근)

- 웹 어플리케이션과 웹 콘솔이 같이 접근이 안되고 오류가 날 수 있기 때문에
- 꼬여서 안될 경우에 test.mv.db 파일을 삭제 후 서버도 껐다 키면서 처음부터

### SQL

```sql
create table member
(
 id bigint generated by default as identity,
 name varchar(255),
 primary key (id)
)
```

- bigint : Java의 Long
- generated by default as identity : id 값이 안들어 왔을 때 자동으로 생성해주는 것

## 순수 JDBC

20년 전 DB 방식, 예전에는 이렇게 했구나 정도만!

개방-폐쇄 원칙(OCP, Open-Closed Principle)

- 확장에는 열려있고 수정, 변경에는 닫혀 있다.

스프링의 DI를 사용하면 **기존 코드를 전혀 손대지 않고, 설정만으로 구현 클래스를 변경**할 수 있다.(객체 지향)

## 스프링 통합 테스트

이전에 만든 것은 단위 테스트(이렇게 만드는 테스트가 좋은 테스트일 확률이 높다.)

DB에는 기본적으로 트랜잭션이라는 개념이 있다. : inssert Query 후에 commit을 해야 반영이 된다(autocommit or commit)

- commit을 하기 전에는 반영되지 않는다.
- Test 끝난 후 롤백을 하면? → DB에 데이터 반영이 안되고 없어짐 → @Transactional 사용

@SpringBootTest : 스프링 컨테이너와 테스트를 함께 실행한다.

@Transactional : 테스트 케이스에 이 annotation이 있으면 테스트 시작 전에 트랜잭션을 시작하고 테스트 완료 후에 항상 롤백한다. 이렇게 하면 DB에 데이터가 남지 않으므로 다음 테스트에 영향을 주지 않는다.

## 스프링 JdbcTemplate

Build.gradle에 `implementation 'org.springframework.boot:spring-boot-starter-jdbc'` **추가**

스프링 JdbcTemplate과 MyBatis 같은 라이브러리는 JDBC API에서 본 반복 코드를 대부분 제거해준다. 하지만 SQL은 직접 작성

해야 한다.

실무에서도 많이 사용한다.

Test Code를 잘 짜는 것이 중요!!

<br>

## JPA

기존 반복 코드는 물론이고 기본적인 SQL도 JPA가 직접 만들어서 실행해준다.

SQL과 데이터 중심의 설계에서 객체 중심의 설계로 패러다임을 전환할 수 있다.

개발 생산성을 크게 높일 수 있다.

객체 + ORM(Object Relational Mapping)

Mapping은 Annotation 사용 → @Entitiy

**주의 해야할 점!**

항상 Transactional이 있어야 한다.

- 데이터를 저장하거나 변경할 경우 필요!

### 환경 설정

build.gradle에 `implementation 'org.springframewok.boot:spring-boot-starter-data-jpa'`을 넣어준다.

- jpa와 starter-jdbc를 포함한다.
- 스프링 부트가 EntityManager를 자동으로 생성해준다.

application.properties에 `spring.jpa.show-sql=true`을 추가한다.

- jpa가 날리는 sql을 볼 수 있다.

application.properties에 `spring.jpa.hibernate.ddl-auto=none`을 추가한다.

- jpa를 사용하면 객체를 보고 테이블을 만들어준다.
- 우리는 만들어져 있는 것을 쓸 것이기 때문에 none으로 설정한다.(자동 생성 기능을 끔)
  - create로 설정하면 자동으로 만들어진다.

JPA는 인터페이스만 제공 구현체는 hibernate, eclipse 등이 있다.

- 보통 JPA에 hibernate를 쓴다.

## Entity

💡 참고 : https://doorbw.tistory.com/227

💡 참고 : https://brunch.co.kr/@ambler/55

: 실제, 객체라는 의미로 실무적으로 엔터티라고 부른다.

즉, 업무에 필요하고 유용한 정보를 저장, 관리하기 위한 집합적인 것

ex) 학생이라는 엔터티는 학번, 이름, 학점, 생일, 등록 날짜 등의 속성으로 특정지어질 수 있다.

- 엔터티는 사람, 장소, 물건, 사건, 개념 등과 같은 명사에 해당된다.
- 엔터티는 업무상 관리가 필요한 것에 해당된다.
- 엔터티는 저장 되기 위한 어떤 것(Thing)에 해당된다.

엔터티는 인스턴스의 집합으로 나타나게 된다.

ex) 과목이라는 엔터티가 있다면, 수학, 영어, 국어와 같은 인스턴스가 과목이라는 엔터티에 포함되는 것이다.

### **특징**

일반적으로 아래의 특징을 지니지 않으면 적절하지 않은 엔터티일 확률이 높다.

- 반드시 엔터티가 사용되는 곳의 업무에서 필요하며 관리하고자 하는 정보
- 엔터티가 포함하는 인스턴스에 대해 유일한 식별자로 식별이 가능해야 한다.
- 엔터티는 지속적으로 존재하는 두 개 이상의 인스턴스들의 조합이어야 한다.
- 엔터티는 반드시 속성을 지녀야 한다.
- 엔터티는 업무 프로세스에 의해서 이용되어야 한다.
- 엔터티는 다른 엔터티와 최소 한 개 이상의 관계가 있어야 한다.

### **분류**

엔터티는 각각의 성격에 의해, 실체유형(유무형)에 따라 구분하거나, 엔터티의 발생시점에 의해 분류될 수 있다.

1. **실체유형(유무형)에 따른 분류**

- **유형 엔터티(Tangible Entity)**

  물리적인 형태가 존재하는 엔터티이며 안정적이고 지속적으로 활용되는 엔터티이다.

- **개념 엔터티(Conceptual Entity)**

  물리적인 형태는 존재하지 않고 관리해야 할 개념적인 정보로 구분이 되는 엔터티이다.

- **사건 엔터티(Event Entity)**

  업무를 수행함에 따라 발생되는 엔터티이다.

1. **발생시점에 따른 분류**

- **기본/키 엔터티(Fundamental/Key Entity)**

  해당 업무에 원래 존재하는 정보로 다른 엔터티와의 관계에 의해 발생 또는 생성되지 않고 독립적으로 존재하는 엔터티이다. 이는 독립적으로 생성이 가능하며 다른 엔터티의 부모역할을 한다.

- **중심 엔터티(Main Entity)**

  기본 엔터티로 부터 발생되며 업무에 있어서 중심적인 역할을 한다. 일반적으로 데이터 양이 많으며 다른 엔터티와의 관계를 통해 행위 엔터티를 생성한다.

- **행위 엔터티(Active Entity)**

  두 개 이상의 부모엔터티로 부터 주로 발생되고, 자주 엔터티의 내용이 바뀌거나 데이터양이 증감한다. 분석초기 단계보다는 상세 설계 단계나 프로세스와 상관 모델링을 진행하면서 도출될 수 있다.

### **엔터티의 명명(Naming)**

엔터티의 이름을 정하는 데에 있어서는 다음과 같은 원칙을 지켜야 한다.

- 가능하면 현업업무에서 사용하는 용어를 사용한다.
- 가능하면 약어를 사용하지 않는다.
- 단수 명사를 사용한다.
- 모든 엔터티를 통틀어서 유일한 이름을 가져야 한다.
- 엔터티의 생성의미대로 이름을 부여한다.

### Code

DB에서 id를 자동으로 생성해 주는 것을 Identity 전략이라고 한다.

- `@Id @GeneratedValue(strategy = GenerationType.*IDENTITY*)`

DB 컬럼명이 username일 때 매핑

- `@Column(name = "username")`

JPA는 EntityManager로 모든 것이 동작한다.(JPA를 쓰려면 EntityManager를 Injection 받아야 한다.)

Pk가 아닌 findByName이나 findAll 같은 경우에는 JPQL을 작성해줘야 한다.

- 조회, 저장, 업데이트는 sql이 없어도 된다.

✅ stream()

💡 참고 : https://dpdpwl.tistory.com/81

람다함수형식으로 간결하고 깔끔하게 요소들을 처리 가능

map : 특정 조건에 해당하는 값으로 변환

- 요소들을 대,소문자 변형 등 의 작업을 하고 싶을 때 사용 가능

filter : 조건에 따라 걸러내는 작업

- 길이의 제한, 특정 문자 포함 등 의 작업을 하고 싶을 때 사용 가능

sorted : 정렬해주는 작업

- 요소들의 가공이 끝났다면 리턴해 줄 결과를 collect를 통해 만들어 준다.

**예시**

```java
ArrayList<string> list = new ArrayList<>(Arrays.asList("Apple","Banana","Melon","Grape","Strawberry"));
System.out.println(list);
//[Apple, Banana, Melon, Grape, Strawberry]

System.out.println(list.stream().map(s->s.toUpperCase()).collect(Collectors.joining(" "))); //APPLE BANANA MELON GRAPE STRAWBERRY
System.out.println(list.stream().map(s->s.toUpperCase()).collect(Collectors.toList())); //[APPLE, BANANA, MELON, GRAPE, STRAWBERRY]
System.out.println(list.stream().map(String::toUpperCase).collect(Collectors.toList())); //[APPLE, BANANA, MELON, GRAPE, STRAWBERRY]
list.stream().map(String::toUpperCase).forEach(s -> System.out.println(s));
//APPLE
//BANANA
//MELON
//GRAPE
//STRAWBERRY

System.out.println(list.stream().filter(t->t.length()>5).collect(Collectors.joining(" "))); //Banana Strawberry
System.out.println(list.stream().filter(t->t.length()>5).collect(Collectors.toList())); //[Banana, Strawberry]

System.out.println(list.stream().sorted().collect(Collectors.toList())); //[Apple, Banana, Grape, Melon, Strawberry]
```

## 스프링 데이터 JPA

스프링 부트와 JPA만 사용해도 개발 생산성이 매우 증가하고 개발해야할 코드도 줄어든다.

여기에 스프링 데이터 JPA를 사용하면 리포지토리에 구현 클래스 없이 인터페이스 만으로 개발을 완료할 수 있다.

반복 개발해온 기본 CRUD 기능도 스프링 데이터 JPA가 모두 제공한다.

→ 개발자는 핵심 비즈니스 로직을 개발하는데 집중할 수 있다.

스프링 데이터 JPA가 SpringDataJpaMemberRepository를 스프링 빈으로 자동 등록해준다

인터페이스를 통한 기본적인 CRUD 기능 제공 findByName() , findByEmail() 처럼 메서드 이름 만으로 조회 기능 제공 페이징 기능 자동 제공

### **참고**

실무에서는 JPA와 스프링 데이터 JPA를 기본으로 사용하고, 복잡한 동적 쿼리는 Querydsl이라는 라이브러리를 사용하면 된다.

Querydsl을 사용하면 쿼리도 자바 코드로 안전하게 작성할 수 있고, 동적 쿼리도 편리하게 작성할 수 있다.

이 조합으로 해결하기 어려운 쿼리는 JPA가 제공하는 네이티브 쿼리를 사용하거나, JdbcTemplate를 사용하면 된다.

<br>

# AOP

관점 지향 프로그래밍(**Aspect Oriented Programming)**

공통 관심 사항(cross-cutting concern)과 핵심 관심 사항을 분리(core concern)

## AOP가 필요한 상황

모든 메서드의 호출 시간을 측정하고 싶다면?

공통 관심 사항(cross-cutting concern) vs 핵심 관심 사항(core concern)

회원 가입 시간, 회원 조회 시간을 측정하고 싶다면?

- 예시

  시간을 측정하는 것은 핵심 로직이 아니라 공통 로직(공통 관심 사항)

  try 안에 있는 것이 핵심 로직(핵심 관심 사항)

  ```java
  public class MemberService {
   /**
   * 회원가입
   */
   public Long join(Member member) {
  	 long start = System.currentTimeMillis();
  	 try {
  		 validateDuplicateMember(member); //중복 회원 검증
  		 memberRepository.save(member);
  		 return member.getId();
  		 } finally {
  		 long finish = System.currentTimeMillis();
  		 long timeMs = finish - start;
  		 System.out.println("join " + timeMs + "ms");
  	 }
   }
   /**
   * 전체 회원 조회
   */
  	 public List<Member> findMembers() {
  	 long start = System.currentTimeMillis();
  		 try {
  		 return memberRepository.findAll();
  		 } finally {
  		 long finish = System.currentTimeMillis();
  		 long timeMs = finish - start;
  		 System.out.println("findMembers " + timeMs + "ms");
  		 }
  	 }
  }
  ```

  **문제**

  예시처럼 하게 되면 유지보수가 어렵다.

  별도의 공통 로직으로 만들기 어렵다.

  시간을 측정하는 로직을 바꾸려고 하면 모든 로직을 찾아가며 바꿔야 한다.

## AOP 적용

시간 측정 로직을 한 곳에 모으고 원하는 곳에 적용한다.

- 예시

  - hello.hellospring > aop > TimeTraceAop

  ```java
  package hello.hellospring.aop;
  
  import org.aspectj.lang.ProceedingJoinPoint;
  import org.aspectj.lang.annotation.Around;
  import org.aspectj.lang.annotation.Aspect;
  import org.springframework.stereotype.Component;
  
  @Aspect
  @Component
  public class TimeTraceAop {
  
      @Around("execution(* hello.hellospring..*(..))")
  //    @Around("execution(* hello.hellospring.service..*(..))") // 서비스만 측정하고 싶을 때
      public Object execute(ProceedingJoinPoint joinPoint) throws Throwable {
          long start = System.currentTimeMillis();
          System.out.println("START: " + joinPoint.toString());
          try {
              Object result = joinPoint.proceed();    // 다음 메서드 진행
              return result;
          } finally {
              long finish = System.currentTimeMillis();
              long timeMs = finish - start;
              System.out.println("END: " + joinPoint.toString() + " " + timeMs + "ms");
          }
  
      }
  }
  ```

  **해결**

  - 회원가입, 회원 조회 등 핵심 관심 사항과 공통 관심 사항을 분리한다.
  - 시간을 측정하는 로직을 별도의 공통 로직으로 만들었다.
  - 핵심 관심 사항을 깔끔하게 유지할 수 있다.
  - 변경이 필요하면 이 로직만 변경하면 된다.
  - 원하는 적용 대상을 선택할 수 있다. → @Around

<br>

# 프로젝트 적용

## 문법

💡 참고 : https://mainia.tistory.com/5574

자바에는 변수와 함수, 클래스에 대한 접근을 제어하는 문법이 있다.

접근을 제어하는 이유는 객체가 가진 고유의 멤버 변수 값들이 외부에서 잘못 변경되는 것을 막기 위해서 이다.

4가지

- **public** : 접근 제한이 없음
- **protected** : 동일한 패키지 내에 존재하거나 파생클래스에서만 접근 가능
- **default** : 아무런 접근 제한자를 명시하지 않으면 dafault 값이 되며, 동일한 패키지 내에서만 접근 가능
- **private** : 자기 자신의 클래스 내에서만 접근이 가능

### Column

**insertable** : 엔티티 저장시 이 필드도 같이 저장한다. false로 설정하면 데이터베이스에 저장하지 않는다. 읽기 전용일 때 사용한다.

**updatable** : 위와 동일한 하지만 수정일 때 해당 된다.

insertable=false는 insert 시점에 막는 것이고, updatable는 update 시점에 막는 기능이다.