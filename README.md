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

- 컨테이너에서는 객체들을 관리하기 위해 별도의 저장소에 bin을 저장하는데 저장소에 저장되어 있는 개발자들이 컨테이너에서 제공하는 API를 이용하여 사용하고자 하는 bin을 검색하는 방법이다.

**DI(Dependency Injection) - 의존성 주입**

- 의존성 주입이란 객체가 서로 의존하는 관계가 되게 의존성을 주입하는 것이다.
- 객체지향 프로그램에서 의존성 이란 하나의 객체가 어떠한 다른 객체를 사용하고 있음을 의미한다.

**각 클래스 사이에 필요로 하는 의존관계를 bin설정 정보를 바탕으로 컨테이너가 자동으로 연결**해 주는 것이다.

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