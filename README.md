# 👨‍👩‍👧‍👦Crew station

# 함께 여행하고, 기록하고, 나누며, 성장할 수 있도록 돕는 여행 동행 플랫폼

## 1. 🎯기획 의도

![슬라이드4](https://github.com/user-attachments/assets/ddf9683f-ce15-4109-b4d3-e1b1c3439555)
![슬라이드5](https://github.com/user-attachments/assets/3d506d85-a4ab-4dc3-bb6a-e2ff3badefdc)



현대의 청년들은 **혼자 여행**에 대한 로망을 갖고 있지만,  
실제로는 아래와 같은 문제를 겪고 있습니다.

-   💸 **높은 여행비**로 인한 경제적 부담
-   😔 **언어와 안전 문제**로 인한 불안감
-   🧳 **혼자 여행의 외로움과 심리적 부담**

또한, 요즘 청년들은 단순한 관광보다  
“**경험을 기록하고, 공유하며, 스스로 성장하는 여행**”을 원합니다.  
이와 동시에 **여행 중 소규모 수익을 창출할 수 있는 기회**에 대한 수요도 높습니다.

이에 Crew Station은

> **“청년들이 함께 여행하고, 기록하고, 나누며, 성장할 수 있는 공간”** 을 목표로 기획되었습니다.

## 2. 💡기대 효과

![슬라이드7](https://github.com/user-attachments/assets/2610393c-fa3b-46a7-a829-a3d0fcfc34e7)

### 1️. 경제적 부담 완화와 기회 형평성 제고

-   **크루 매칭 및 공동 숙박**을 통해 여행 비용을 나눠 부담함으로써 청년층의 경제적 장벽을 낮춤
-   여행지에서의 **기념품 판매 기능**으로 여행 중 소규모 수익 창출 가능

### 2️. 창업적 감각 함양

-   여행 중 판매 데이터를 기반으로 **상품 선호도, 반응, 트렌드 분석 가능**
-   실제 소비자 반응을 통해 **시장성 있는 아이템 발굴 및 사업성 검증**

### 3️. 콘텐츠 기반 성장

-   여행 일기 기능을 통해 **개인의 여행 경험을 콘텐츠로 기록 및 공유**
-   **일기 → 기록 → 콘텐츠 → 영향력**으로 이어지는 자연스러운 성장 구조 형성

### 4️. 심리적 안정감 제공

-   낯선 여행지에서도 **함께할 크루**를 통해 안정감 확보
-   **혼자 여행의 외로움과 불안을 완화**하며 건강한 여행 문화 조성

---

## 3. 🧰프로젝트 사용 툴


| 구분             | 사용 기술                                                                                   |
|------------------|----------------------------------------------------------------------------------------------|
| 🧩 Backend        | Spring Boot, Spring Security, JWT<br>Java, JDK 17.0.10<br>Spring Session & Cache (Redis)<br>OAuth2 Social Login<br>Springdoc OpenAPI (Swagger UI)<br>AOP, Lombok<br>MyBatis |
| 🗄️ Database       | MyBatis, PostgreSQL, Redis                                                                   |
| 🧱 HTML Engine    | Thymeleaf                                                                                    |
| ☁️ Cloud          | AWS S3, AWS IAM, AWS EC2                                                                     |
| 🌐 External APIs  | Boot Pay API, CoolSms API<br> REST API<br>Naver / Kakao / Google Developer API<br>Kakao Daum Postcode API<br>SMTP Gmail API |
| 🧰 Tools          | IntelliJ IDEA, DBeaver<br>Git / GitHub / Sourcetree<br>Slack, Postman                        |
| 🧪 Test           | JUnit5                                                                                       |

## 4. 🗂️ERD

<img width="5002" height="6322" alt="erd" src="https://github.com/user-attachments/assets/ba7d5671-3817-4329-a98a-93d78f74612f" />

## 5. 👩🏻‍💻담당 업무

<img width="1035" height="293" alt="back" src="https://github.com/user-attachments/assets/d2e87aab-b21d-4693-be76-3fb1c44e0b7a" />

### 백엔드

▶ 회원가입

-   이메일 중복 검사
-   이메일, 휴대폰, 비밀번호, 생년월일, MBTI 입력 형식 검사
-   API를 이용한 주소 찾기
-   필수 정보 입력 여부 검사
-   조건 충족 시 회원가입
-   핸드폰 번호 인증 번호 발송
-   소셜 회원가입: 카카오, 네이버, 구글 API를 연동한 OAuth2 간편 회원가입

▶ 로그인

-   이메일, 비밀번호 Spring Security, JWT를 사용하여 로그인 기능 구현
-   소셜 로그인: 카카오, 네이버, 구글 API를 연동한 OAuth2 간편 로그인
-   Redis에 refreshToken 저장 → accessToken 만료 시 재발급 처리

▶ 게스트 로그인

-   주문번호, 핸드폰 번호 Spring Security, JWT를 사용하여 로그인 기능 구현
-   Redis에 refreshToken 저장 → accessToken 만료 시 재발급 처리

▶ 로그아웃

-   로그아웃 시 Redis에 블랙리스트 등록 → 만료되지 않은 access token 차단
-   access token과 refresh token 삭제 → 클라이언트/서버에서 모두 무효화

▶ 비밀번호 재설정

-   가입 된 이메일 확인 정보 있을 경우 다음 단계 이동
-   확인 코드 이메일 발송, 코드 일치 시 다음 단계 이동
-   비밀번호 변경

## 6. 🛠️오류 상황들

#### **( 1 )** 회원과 같은 서비스가 되어버리는 게스트

🌩문제 상황🌩  
<img width="1918" height="992" alt="게스트 글 작성" src="https://github.com/user-attachments/assets/474980f9-3094-4788-be1b-a6001620de1e" />

게스트 로그인 시에도 게시글 작성 페이지에 접근이 가능했습니다.
(게스트 계정은 작성 기능을 사용할 수 없어야 함)

🚨문제 원인🚨  
게스트의 access token이 일반 회원으로 잘못 인식되어
작성 페이지 접근이 허용되었습니다.

🚀해결 방법🚀

1. GuestInterceptor 생성

<img width="1022" height="865" alt="guestInterceptor1" src="https://github.com/user-attachments/assets/b06f3182-d17e-43af-991d-61def09774f9" />
<img width="1026" height="535" alt="guestInterceptor2" src="https://github.com/user-attachments/assets/17c6d518-32e7-4322-acca-b28e68654af2" />



-   로그인한 사용자의 username이 이메일 형식인지 확인 후
-   이메일 형식이 아니면 게스트 계정으로 분류 했습니다.

2. 게스트 계정이 회원 전용 페이지에 접근하려고 하면

<img width="638" height="896" alt="web1" src="https://github.com/user-attachments/assets/83fc4248-729f-4aa2-88da-c633b9bcccff" />
<img width="626" height="542" alt="web2" src="https://github.com/user-attachments/assets/0b5b11de-dea8-4de4-898c-58d0d973fabe" />



-   로그아웃 처리 후
-   로그인 페이지로 리다이렉트 하였습니다.

✅ 결과: 게스트 계정은 회원 전용 기능에 접근할 수 없도록 안전하게 제한되었습니다.

---

#### **( 2 )** 소셜 로그인 후 일반 회원 로그인 불가

🌩문제 상황🌩  
<img width="581" height="149" alt="문제2" src="https://github.com/user-attachments/assets/3d2dca5d-809c-4985-81a9-16c38f89fc10" /><img width="1793" height="176" alt="회원가입후로그인" src="https://github.com/user-attachments/assets/8b3cb7f4-9837-43da-ac02-86bd9457977b" />



소셜 로그인(카카오, 네이버, 구글 등) 이후 로그인 페이지에서 일반 로그인 시도 시 정상적인 계정 정보 입력에도 로그인이 되지 않았습니다.

🚨문제 원인🚨  
소셜 로그인 시 생성된 쿠키(name, provider)가 브라우저에 남아있어 일반 로그인 시 기존 소셜 세션 정보와 충돌이 발생했습니다.

🚀해결 방법🚀

1. resetCookies 메서드 추가

<img width="850" height="705" alt="쿠키 삭제 메소드" src="https://github.com/user-attachments/assets/50957254-36d6-4076-92e2-ff4dc513c5ab" />


-   모든 쿠키 및 Redis에 저장된 refreshToken을 삭제하는 메서드 생성했습니다.

2. service.js 수정

<img width="723" height="237" alt="쿠키_서비스" src="https://github.com/user-attachments/assets/345a2bfc-aa98-4255-bdef-794488e736ff" />

-   로그인 요청 전 resetCookies를 비동기(async)로 실행하도록 수정했습니다.

3. event.js 수정

<img width="277" height="54" alt="쿠키 삭제 사용" src="https://github.com/user-attachments/assets/30ce3841-4e11-4f3c-bf54-bafd470a85e7" />

-   로그인 페이지 로드 시점에 `memberService.resetCookies();` 호출하여 기존 쿠키 및 세션 데이터 초기화했습니다.

✅ 결과: 로그인 페이지 진입 시 모든 쿠키와 Redis refreshToken이 삭제되어 소셜 로그인 후에도 일반 로그인이 정상적으로 동작하게 되었습니다.

#### **( 3 )** 소셜 로그인 같은 이메일 사용시 같은 회원으로 인식

🌩문제 상황🌩  
<img width="1231" height="682" alt="기존코드" src="https://github.com/user-attachments/assets/77c7980f-d472-4ac9-9e54-80e9f3d907c3" />

서로 다른 소셜 로그인이 하나의 이메일을 사용하는 경우, 신규 회원 가입 창이 아닌 기존 회원으로 인식되어 바로 로그인이 되는 문제가 발생했습니다.

🚨문제 원인🚨  
회원 조회 시 이메일만을 기준으로 판단했기 때문에, 소셜 제공자가 다르더라도 이메일이 같으면 동일 회원으로 처리되는 로직이었습니다.

🚀해결 방법🚀

1. MemberMapper.xml 수정

<img width="1696" height="493" alt="mapper-xml" src="https://github.com/user-attachments/assets/42f6cd9b-f516-4432-92e0-624ad49906a3" />


-   provider 조건을 추가하여 이메일과 소셜 제공자를 함께 조회하도록 수정했습니다.

2. MemberMapper.java 수정

<img width="1449" height="748" alt="mapper-java" src="https://github.com/user-attachments/assets/7b9fdc03-e071-44c8-bca9-0e74e39126bd" />

-   provider를 매개변수로 추가하여 DAO 계층에서 전달 가능하도록 변경했습니다.

3. MemberDAO.java 수정

<img width="1175" height="682" alt="dao" src="https://github.com/user-attachments/assets/379ffb79-a09b-481a-ba4a-8d31bd956347" />

-   이메일과 provider를 함께 조건으로 사용하여 정확한 회원 조회가 가능하도록 수정했습니다.

4. CustomOAuth2UserService 수정

<img width="1128" height="921" alt="스크린샷 2025-10-30 170219" src="https://github.com/user-attachments/assets/1d1c82d5-e328-4181-9a77-4fe8d9bb7ec4" />

-   OAuth2 인증 과정에서 registrationId를 통해 소셜 제공자(Google, Naver, Kakao 등)를 식별하고, 사용자 정보에서 provider 값을 추출하여 회원 조회 시 이메일과 함께 비교하도록 개선했습니다.

#### **(3-1)** BadSqlGrammarException 오류 발생

🌩문제 상황🌩

<img width="1171" height="180" alt="6-2_오류" src="https://github.com/user-attachments/assets/e4ec38ce-72cf-4cf7-83cf-288fc49ed60b" />



`BadSqlGrammarException` 예외가 발생했습니다.

🚨문제 원인🚨

<img width="1276" height="72" alt="6-2_기존코드" src="https://github.com/user-attachments/assets/0e72b0a9-dab5-4089-a1ad-8ab247f5757d" />
<img width="657" height="97" alt="6-2_기존코드2" src="https://github.com/user-attachments/assets/cbb881c7-41e9-44d1-a933-8869e9dc3ac7" />


PostgreSQL에서는 `ENUM`이 사용자 정의 타입(`TYPE`)으로 처리되는데, Java 코드에서 `provider` 값을 단순 `String`으로 전달하면서 타입 불일치가 발생했습니다. 이로 인해 SQL 문법 오류가 발생한 것입니다.

🚀해결 방법🚀

<img width="1154" height="922" alt="스크린샷 2025-10-30 170549" src="https://github.com/user-attachments/assets/46b152de-a3db-474c-9e5b-895935e57e0f" />
<img width="1025" height="71" alt="변경코드2" src="https://github.com/user-attachments/assets/0a636ae6-b814-4527-9018-42ebfcf31d8d" />


`MemberProvider` Enum 클래스에서 `provider` 값을 매핑하여, 문자열이 아닌 Enum 객체로 변환한 후 DAO에 전달하도록 수정했습니다.  
이를 통해 PostgreSQL의 ENUM 타입과 정확히 일치하는 값으로 쿼리를 실행할 수 있게 되었고, 타입 불일치로 인한 오류를 해결했습니다.

## 7. 🧪QA 테스트

-   테스트 케이스 설계 및 실행 절차를 기반으로 QA 테스트 문서를 작성하고 기능별 검증을 수행했습니다.  
-   **JUnit5를 활용한 단위 테스트 및 통합 테스트**를 통해 애플리케이션의 안정성과 기능 완성도를 검증했습니다.

<img width="944" height="436" alt="qa" src="https://github.com/user-attachments/assets/f9dc004b-3ca8-4f66-b036-65e84fe1aab4" />

## 8. 📱앱 전환 - Web View

-    통합 구현 능력단위에서 배운 react-native 기술로 모바일 화면을 구축하였습니다.  
-    웹 화면을 앱에 통합하여 모바일 환경에서도 동일한 사용자 경험을 제공하도록 설계하였습니다.  
-    로그인 세션을 앱과 웹 간에 공유할 수 있도록 API 구조를 통합하여 사용자 편의성을 높였습니다.

<img width="500" height="2532" alt="모바일화면" src="https://github.com/user-attachments/assets/d19c5d22-cc17-453c-bddc-365986b3bc63" />


## 9. 📝총평

🌟 **기획 : 꼼꼼함의 중요성**

이번 프로젝트를 통해 기획의 중요성과 그 복잡성을 깊이 체감할 수 있었습니다.  

기획 단계에서 특정 사용자 행동에 대한 시나리오가 충분히 고려되지 않은 경우, 개발 중 예외 처리가 누락되는 문제가 발생했습니다.   
예를 들어, 비회원 사용자가 특정 기능에 접근하거나 예상치 못한 형태의 입력값을 전달했을 때, 시스템이 이를 적절히 처리하지 못해 오류가 발생하거나 사용자 경험이 저하되는 상황이 있었습니다.  
이러한 문제는 기획서에 정의된 흐름이 일반적인 사용 시나리오에만 집중되어 있었기 때문에 발생한 것으로, 실제 구현 과정에서 다양한 사용자 행동을 시뮬레이션하고 테스트하면서 발견되었습니다.    

이를 해결하기 위해 팀원들과 함께 누락된 시나리오를 정리하고, 예외 상황에 대한 처리 로직을 추가함으로써 서비스의 안정성과 완성도를 높일 수 있었습니다.

이번 경험을 통해 기획 단계에서 다양한 사용자 행동을 충분히 예측하고 반영하는 것의 중요성을 실감했으며, 기술적 관점에서 기획을 보완하는 역할이 백엔드 개발자에게도 매우 중요하다는 점을 배울 수 있었습니다.

🌟 **협업 : 소통이 곧 완성도**

이번 프로젝트를 통해 협업의 본질과 개발자 간 소통의 중요성을 깊이 체감할 수 있었습니다.   
특히 화면을 구현한 개발자의 의도나 기능 흐름을 파악할 때, 코드에 남겨진 주석만으로는 충분한 맥락을 이해하기 어렵다는 점을 경험했습니다.   
기능의 목적이나 예외 처리 방식, 사용자 흐름에 대한 배경이 생략된 경우가 많아, 개발자 간 의도 전달이 불완전하다는 것을 느꼈습니다.

이러한 문제를 개선하기 위해 제가 주도적으로 각 기능마다 설명 주석을 체계적으로 작성하도록 팀 내 기준을 제안하고 적용했습니다.  
또한 기능 구현 전후로 팀원들과 기획 의도, 기술적 제약, 데이터 흐름 등을 공유하며 서로의 이해를 맞춰나갔고, 그 결과 더 높은 품질의 결과물과 효율적인 개발 프로세스를 만들어낼 수 있었습니다.  

이러한 경험을 통해 기술적 역량뿐 아니라 소통과 문서화 능력이 협업의 핵심 요소임을 실감했습니다.  
이번 프로젝트는 단순한 기능 구현을 넘어, 팀 전체의 개발 효율성과 코드 가독성을 높이는 데 기여할 수 있었던 의미 있는 시간이었습니다.

🌟 **미래 : 성장에 대한 확신**

프로젝트를 하나씩 완성해 나가는 과정에서 코드의 구조와 품질이 점점 다듬어지고, 문제를 바라보는 시야도 점차 넓어지는 것을 직접 경험했습니다.   
처음에는 단순히 기능을 구현하는 데 집중했지만, 점차 코드의 재사용성, 유지보수성, 예외 처리, 성능까지 고려하게 되었고, 이는 개발자로서 한 단계 성장하는 계기가 되었습니다.

특히 문제를 해결하는 과정에서 다양한 접근 방식을 고민하고, 팀원들과의 논의를 통해 더 나은 해결책을 도출해내는 경험은 매우 도전적이면서도 즐거웠습니다.   
기능 하나하나를 완성할 때마다 기술적 자신감이 쌓였고, 복잡한 문제를 마주했을 때도 두려움보다 호기심이 앞서는 자신을 발견할 수 있었습니다.
이러한 경험을 통해 앞으로 더 나은 코드를 작성할 수 있다는 확신을 갖게 되었으며, 실무에서도 유연하고 효율적인 개발을 이어갈 수 있을 것이라 믿습니다.   
이번 프로젝트는 단순한 학습을 넘어, 개발자로서의 방향성과 가능성을 확인한 의미 있는 여정이었습니다.


🌟 기술적 성장

- **Spring Security와 JWT를 활용한 인증·인가 구현**   
사용자 인증 및 권한 부여 흐름을 직접 설계하며, 토큰 기반 보안 구조에 대한 이해도를 높였습니다.

- **Redis 기반 세션 관리 최적화 및 캐싱 전략 적용**  
인증 토큰 저장과 캐싱을 통해 서버 부하를 줄이고, 응답 속도를 개선함으로써 사용자 경험을 향상시켰습니다.

- **RESTful API 설계 및 Swagger를 통한 명세 자동화**  
RESTful 원칙에 따라 API를 구조화하고 Swagger를 활용해 명세를 자동화하여 프론트엔드와의 협업 효율을 높였습니다.

- **트랜잭션 관리 및 데이터 일관성 확보**   
@Transactional을 활용해 데이터의 일관성을 유지하고, 롤백 조건 및 트랜잭션 전파 방식에 대한 실전 이해를 심화했습니다.

- **AOP(Aspect-Oriented Programming)를 활용한 공통 로직 분리**   
로깅, 인증 체크, 예외 처리 등 반복되는 기능을 AOP로 분리하여 코드의 가독성과 유지보수성을 크게 향상시켰습니다.






📌 **작성자:** 임채민 &nbsp;&nbsp;&nbsp;&nbsp; **TEAM:** crew station  
📅 **기간:** 2025.09.09 ~ 2025.10.21
