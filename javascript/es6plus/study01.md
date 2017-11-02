# 코드 스피츠 스터디 1일

**[Code Spitz 73 – ES6+ 기초편](http://www.bsidesoft.com/?p=5687)**
이번 코스에서는 ES6+의 기초적인 문법과 의미를 살펴보고 실제 브라우저 상에서의 활용법을 공부하게 됩니다.
하지만 너무 기초적인 설명보다는 대한 보다 깊은 의미와 사용법을 다루는데 치중하기 때문에 프론트엔드 개발자나 백엔드 개발자가 자바스크립트에 대해 보다 깊이 이해하고 싶은데 어려워서 접근하지 못하고 있던 경우가 더 적합할 수도 있습니다.

강의자 : Bsidesoft 대표

[ES6+](https://github.com/wesbos/es6.io)

코드 스피츠 세미나 목표 : 실제 개발자가 되자 -> 복잡성 정복

## 프로그래밍 실행 주기
1) C/ C++ 등
랭귀지 코드(Lint time. 오류가 있는지 체크) -> machine language(Compile time 컴파일)
파일 -> 메모리에 적재 -> 실행(Run time 런타임) -> terminate(종료)
- 되도록이면 앞 시점에서 오류를 잡자. 프로그래밍 전략
- 컴파일시 전체 검사

2) 현대의 패러다임 : 런타임 스크립트 개념 도입 (런타임 언어)
랭귀지 코드(Lint time)
-> 파일 -> 메모리에 적재(load) -> machine language(즉 오토 컴파일)
-> 실행(Run time 런타임) -> terminate(종료)
- 부분적인 컴파일. 따라서 실행되어야 오류를 알 수 있다.
- 런타임 에러가 나는데 오류 잡기 힘들다. 그래서 typescript등이 나왔다. 혹은 스크립트 개발론
- 스크립트 개발론 : 함수, 클래스 등 레이어별로 에러가 나는 시점을 분류해서 코드를 적는다.
 - isolate(격리) : base, extended, use function class...  이렇게 격리할 줄 알아야한다.

## Lexical grammer(어휘적 문법)
: 자바스크립트 엔진이 text를 만나면 이렇게 분류된다.
control chracter 제어문자(한국어쓸땐 안씀), white space 공백문자, line termanators 개행문자,
comments 주석, keyword 예약어, literals 리터럴(더이상 자를 수 없는 값의 표현)

## 자바스크립트의 언어 기본 요소 (language element)
#### statements 문
공문(비어있는 문), 식문(하나의 식은 하나의 문. 예 2 + 3;), 제어문, 선언문
단문(문장 하나), 중문(중괄호로 묶었을 때 문장 하나로 보는 경우)
- 값이 아닌 모든 것이라고 보면된다.
- 자바스크립트 엔진이 어떻게 해석할지 알려주는 힌트. 실행 후 메모리에서 없어진다.

#### expresstion 식
값식, 연산식, 호출식
- 최종적으로 하나의 값으로 떨어진다.
- 그냥 값은 소비되어 없어진다.

#### identifier 식별자
기본형(복사가 일어난다.), 참조형(다른 메모리 주소가 들어있다. 주소만 복사되어 똑같은 데이터를 가리킨다.)
변수, 상수
- 변수 : 메모리 주소의 별명, 데이터 타입 정보
- 상수 : 변하지 않는 데이터

자바스크립트 기본형 : int, string, boolean, null, undefined, NaN
자바의 string은 참조형
그렇게 정한거다.

함수 : 자바스크립트에서는 값이다. 자바에서는 식.. 언어설계자가 그렇게 정한것임

## sync flow 동기화 명령 흐름
- 한번에 적재되어 있는 메모리의 명령어를 쭉 소비한다.
- 중간에 프로그래밍을 멈출 수 없다.
- 위 -> 아래로, 왼 -> 오른쪽으로
- 그런데 할당(=)만 오른쪽에서 왼쪽으로 (수학적 기호에 따라)

## 제어문 (sync flow control)
프로그램은 고정되어 있지만 입력값들에 따라 다른 flow를 타게 하고 싶다. => 효율적
- sub flow : main flow에서 sub flow갔다가 다시 main flow... 함수, 클래스 등 처리

#### if문
- if ( 식 ) { 문(단문, 중문) } => optional 하게 쓴다.
- if ( 식 ) { 문(단문, 중문) } else { 문 } => 둘 중 하나. 굉장히 중요한 것이다 라고 표현한 것이다.
=> 이렇게 섬세하게 쓸 줄 알아야 한다. 

**연산자보다는 함수로 처리하여 누구나 알 수 있게끔 하는 것이 좋다.**
예) 3 + 2 / 4, a = 5; 보다는 함수로 처리하도록 한다. (add, divide... )

- ES6의 generater : 끝까지 flow가 진행되지 않아도 끝내게 할 수 있다. 즉, 복잡한 flow제어를 할 수 있다.
- 현대 언어는 이런 흐름제어를 할 수 있다. 예전 a,b,c언어는 무조건 끝까지 실행되어야 끝났다.

- 코드를 작성할 때 코드를 읽어보면 의도를 알 수 있도록 짜야한다. 그래야 수정, 유지보수가 가능하며 upgrade할 수 있다.
즉, for, while, do while문 들이 왜 있는가, 이런 의도를 알 수 있도록 하기 위함이다.