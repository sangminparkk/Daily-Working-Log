# 24-09 / Daily-Working-Log

## 이번주 목표
* JPA 프로젝트 강의(by. 김영한) 완강
* JPA 프로젝트 강의(by. 백기선) 추가 진행 (to the deep)
* thymeleaf 사용법 익히기

## Things to think about
* 실무 업무 효율을 높이는 조합 3종(spring boot / JPA / queryDSL) 동작원리 

## Things to do
* JPA 실전1(Web 개발) -- 9/25

## Things I am doing?
* JPA 실전1 - Web 개발 완강

## Things I learned
* Web Application 데이터 전송  ---  9/25

---

### Web Application 데이터 전송 (9/25)
클라이언트(사용자)로부터 정보를 입력받아 DB에 데이터 저장하기 위해서는 다음과 같은 과정이 필요합니다.  
1. 사용자 정보에 대한 form 객체를 생성해야 합니다. (=DTO, Data Transform Object로 비지니스 로직이 아닌 오직 데이터 담고 전달하는 역할만 합니다)
2. Controller를 통해서 사용자 정보를 입력 받기 위해서 뷰 랜더링을 통해 화면을 보여줍니다. (Controller → view)
3. 사용자는 랜더링된 입력폼에 정보를 입력하고 제출합니다. 이때가 클라이언트가 서버에 `POST` 요청을 보내는 시점입니다.
4. 다만 데이터가 Controller에 전달되기 전, `@Valid`가 붙은 DTO 객체에 대하여 데이터 유효성 검증을 수행합니다. (Bean Validation에 의해 자동으로 수행됨)
5. `@PostMapping` 처리된 Controller가 클라이언트로부터 받은 데이터를 서버에 보내고, 내부 로직에 의해 처리되며, DB에 데이터를 저장합니다.
6. DB는 서버가 요청한 데이터를 제공하고, 서버는 데이터를 클라이언트로 다시 전송합니다.

**피드백**  
당연하게 알고 있다고 착각했던, 오만한 제 자신을 반성하게 됩니다.  
위의 데이터 전달 흐름을 명확하게 인지하지 못한 상황에서 무작정 개발을 진행하다보니 막히는 부분이 많았습니다.  
역시 무식하면 용감합니다..