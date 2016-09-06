name: title
class: middle, center, inverse

# .title_upper[Unity3d에서 테스트하기]

.author[박진언 ([jinunpark@maverickgames.co](mailto:jinunpark@maverickgames.co))]

---
class: middle

# 발표자: 박진언

--

## 관심사
* 재미있는 게임 만들기
* 더 즐겁게 프로그래밍하기
* 가벼운 팀 만들기

--

## 경력
* Maverick Games 프로그래머
* (전) NCSoft B&S 개발실 서버 프로그래머
* (전) 루비콘게임즈 서버 프로그래머

---
class: center, middle

# **TDD**

## Test Driven Development

---
class: center, middle

# 주로 하는 질문

## 왜 하는지 잘 모르겠다
## 어떻게 하는지 잘 모르겠다

---
class: middle

# 왜?

---
class: center, middle

## 테스트 커버리지 100% == 버그 없음

--

### 도망가세요. **사기꾼입니다.**

---
class: center, middle

## Test Code의 기능

--

### 문서화

--

### 회귀 테스트

---
class: middle

## 문서화

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

# 어떻게?

--

* Unity3d의 component들은 모두 MonoBehavior 기반
* 모두 구체 클래스
* Mockup이 불가능하다
