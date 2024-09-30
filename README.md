# 24-09 / Daily-Working-Log

## 이번주 목표
* JPA 프로젝트 강의(by. 김영한) 완강
* JPA 프로젝트 강의(by. 백기선) 추가 진행 (to the deep)
* thymeleaf 사용법 익히기

## Things to think about
* 실무 업무 효율을 높이는 조합 3종(spring boot / JPA / queryDSL) 동작원리 

## Things to do
* ~~JPA 실전1(Web 개발) -- 9/25~~
* 자바의 정석(기본개념I) -- 9/30
* JPA 실전2(API 개발 기본) -- 9/30

## Things I am doing?
* ~~JPA 실전1 - Web 개발 완강 (~9/29)~~~


## Things I learned
* Web Application 데이터 전송  ---  9/25
* @ModelAttribute Vs. Model  ---  9/26

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

---

### @ModelAttribute Vs. Model (9/26)
아래 케이스에 맞게 사용하시면 됩니다.

* Model : 서버에서 뷰로 데이터 전달하고 싶은 경우
```java
@GetMapping("/url")
public String createForm(Model model) {
    model.addAttribute("memberForm", new MemberForm());
    return "memberForm";
}
```

* @ModelAttribute : 클라이언트에서 서버로 데이터 바인딩 처리가 필요한 경우 
  * 주로 폼데이터를 바인딩하고 유효성 검사를 처리할때 유용합니다. ([spring doc](https://docs.spring.io/spring-framework/reference/web/webmvc/mvc-controller/ann-methods/modelattrib-method-args.html))
```java
@PostMapping("/members/new")
public String join(@Valid @ModelAttribute MemberForm memberForm, BindingResult result) { 
    if (result.hasErrors()) {
        // 예외처리
    }
    // 비즈니스 로직 처리
    return "redirect:/";
}
```
**피드백**  
확실히 제대로 짚으면 몰랐던 내용이 많았네요.. 가야할 길이 멀지만 반드시 해내겠습니다. 좋은 동료분들과 함께 성장하는 개발자가 되기 위해 노력하겠습니다!