name: title
class: middle, center, inverse

# .title_upper[Unity3d에서 테스트하기]

.author[박진언 ([jinunpark@maverickgames.co](mailto:jinunpark@maverickgames.co))]

---
class: middle

## 발표자: 박진언

### 관심사
* 재미있는 게임 만들기
* 더 즐겁게 프로그래밍하기
* 가벼운 팀 만들기

### 경력
* Maverick Games 프로그래머
* (전) NCSoft B&S 개발실 서버 프로그래머
* (전) 루비콘게임즈 서버 프로그래머

---
class: center, middle

# Unit test

--

### TDD(Test Driven Development)의 기법 중 하나

--
### 특정 기능만 테스트하는 코드

---
class: center, middle

# 주로 하는 질문

.footnote[Unit Test]
--

## 왜 하는지 잘 모르겠다


--

## 어떻게 하는지 잘 모르겠다

---
class: middle

# 왜?

.footnote[Unit Test]
---
class: center, middle

## 테스트 커버리지 100% == 버그 없음

.footnote[Unit Test]
--

### 도망가세요. **사기꾼입니다.**

---
class: center, middle

## Test Code의 기능

.footnote[Unit Test]
--

### 문서화

--

### 회귀 테스트

---
class: middle

## 문서화

.footnote[Unit Test]
--

* 코드를 사용하는 방법
* 코드를 실행했을 때 나타나는 결과

--

## 장점

--

* 실패하는 문서
* 문서가 코드

---
class: middle

## 회귀 테스트

.footnote[Unit Test]
--

* 코드를 변경해도 기능이 잘 동작하는지 지속적으로 테스트
* 회귀 테스트가 많으면 리팩토링을 가볍게 할 수 있다
* 버그가 발생하면 발생 가능 지점을 줄일 수 있다


---
class: middle

## 팀 상황

.footnote[Unit Test]
--

* QA 전담 인력 없음

--

* 개발하는 게임의 복잡성 높음
    * 스킬 10개 이상
    * 사용 가능한 행동 20개 이상
    * 지역 1개 이상
    * 의뢰 100개 이상
    * 사건 2000개 이상
--

## -> ** 사람은 처음 나타나는 버그만 발견해야 한다 **

---
class: middle

# 어떻게?

.footnote[Unit Test]
--

* Unity3d의 component들은 모두 MonoBehavior 기반
* 모두 구체 클래스
* Mockup이 불가능하다

--

## 정석

.footnote[Unit Test]
--

* 모든 component의 상속 규칙
  * MonoBehavior 상속
  * 다른 클래스에 대한 인터페이스(들)을 구현
* 클래스끼리는 인터페이스만 사용해서 통신
* 테스트 코드에서는 Mockup instance 사용

---
class: middle

## 팀 상황

.footnote[Unit Test]
--

* MonoBehavior 기반
* 인터페이스로 소통하는 코드 적음
* 클래스간 의존성 강함

---
class: middle

## 해결 방법

.footnote[Unit Test]
--

* Quick'n Dirty
* 구체 클래스의 모든 public method들을 단일 interface로 만든다
* 클래스 의존을 interface로 교체

---
class: middle

## 코드에 redundancy가 늘어나지 않나?

.footnote[Unit Test]
--

* 클래스에 method가 100개가 넘어요!
* 너무 큰 interface가 생겼어요!

--

* 일단 interface로 빼면 나중에 쪼개기 쉽다
* Unit test를 만들어 두었다면 없을 때보다 refactoring하기 쉽다


---
class: middle

## 버그가 생기면

.footnote[Unit Test]
--

* 버그 재현 방법을 찾는다 **<- 제일 어려움**
* 버그 케이스에 대한 유닛 테스트를 추가한다
* 테스트가 통과할 때까지 수정한다
* Profit!

---

class: center, middle

# 기기 테스트

--

## 실제 기기에서 테스트하기

---
class: middle

# 정석

.footnote[기기 테스트]
--

* [Appium](http://appium.io/)
* 구조
  * 앱은 기기의 UI Automator에 연결
  * Appium은 USB를 통해 UI Automator를 조정
* Cucumber를 사용해서 테스트
  * Unit test code를 쓰는 것과 같은 방식으로 돌아감

---
class: middle

# 문제

.footnote[기기 테스트]
--

* 프로그래머가 아닌 사람이 보기 힘들다
* 함수 재사용이 어렵다

---
class: middle

# 해결책

.footnote[기기 테스트]
--

* [SpecFlow](http://www.specflow.org/)
* BDD 툴
* Feature를 문장으로 만들면 cs 파일을 생성해준다

---
class: middle

# Appium 문제

.footnote[기기 테스트]
--

* Unity3d는 UI 구조를 UI automator에게 전달해 주지 않는다
* 게임 오브젝트도 전달해 주지 않는다

---
class: middle

# 해결 방법들

.footnote[기기 테스트]
--

* [Image Recognition](http://testdroid.com/tech/appium-tip-22-how-to-deploy-image-recognition-in-your-appium-tests)
    * 2D 게임이라면 추천
    * 판타지 레이더스는 3D 게임이어서 기각
--

* [Appium에 전용 모듈을 만들어서 해결](http://ndcreplay.nexon.com/NDC2016/sessions/NDC2016_0053.html)
    * Unity3d 전용 해결법
    * 테스트 클라우드에서는 적용할 수 없는 방법

--

* 테스트 코드와 소켓통신
    * 유니티에서 GameObject 정보를 모두 socket으로 전달
    * 빠르고 플랫폼 가리지 않음
    * 테스트 클라우드에서는 적용할 수 없음

---
class: middle

# 실험중인 방법

.footnote[기기 테스트]
--

* Image Recognition을 이용해서 화면에 정보를 띄우자!
  * GameObject 정보를 byte로 변환
  * byte로 변환한 정보를 24bit rgb로 변환
    * 1 pixel == 3bit
  * 테스트 코드에서는 스크린샷을 찍어 색 -> bit -> 정보 로 변환

--

* 장점
  * 플랫폼 독립적임
  * 테스트 클라우드 사용 가능

* 단점
  * 구현하기 어렵다
  * 스크린샷 찍는데 2초 걸림

---
class: middle

# 결론

--

1. 테스트는 쌓을수록 자산이 됩니다.

--

1. 한 번에 깔끔하게 떨어지지 않습니다. Quick'n Dirty.

--

1. 테스트를 시작하기 가장 좋은 시점은 지금

---
class: center, middle

# Q & A

---
class: center, middle

# 감사합니다.
