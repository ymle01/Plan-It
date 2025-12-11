# Plan-It 🗺️

> AI 기반 여행 설계 플랫폼

**Plan-It**은 AI 기반 여행 설계 플랫폼으로, 사용자가 여행지를 탐색하고 맞춤형 여행 코스를 생성·관리할 수 있는 웹 서비스입니다.

사용자는 전국의 여행지와 축제 정보를 검색하고, AI 플래너와 대화하며 개인 맞춤형 여행 일정을 추천받을 수 있습니다.

추천받은 코스는 직접 수정·편집할 수 있으며, 구글맵으로 시각화하여 실제 여행 계획에 활용할 수 있습니다.

또한 공공데이터(한국관광공사, KCISA)와 AI 기술을 결합하여 정확하고 신뢰할 수 있는 여행 정보를 제공하도록 설계되었습니다.

---

## 📁 프로젝트 구조

```
planit/
├── pib/          # Backend (Spring Boot 3.5)
└── pfa/          # Frontend (React 19)
```

- **`pib`** (Plan-It Backend): Spring Boot 3.5 기반 백엔드 서버
- **`pfa`** (Plan-It Frontend): React 19 기반 프론트엔드 웹 클라이언트

각 모듈의 상세 정보는 해당 디렉터리의 README를 참고하세요.

---

## 🛠️ 기술 스택 및 인프라

### Backend
- Spring Boot 3.5
- Spring Security
- Spring Data JPA
- JWT

### Frontend
- React 19
- React Router v7
- Axios
- React Icons
- React Slick

### Database
- MySQL 8.x
- Redis

### API
- OpenAI API
- 한국관광공사 TourAPI
- KCISA API
- Kakao REST API
- Google Maps API
- CoolSMS API

### 인증 / 보안
- JWT
- BCrypt
- OAuth 2.0 (Google)
- SSL/TLS
- Gmail SMTP

### DevOps & Infra
- Gradle
- npm
- CORS 설정
- WebClient (WebFlux)
- Apache HttpClient5

### Collaboration
- Git, GitHub
- Notion (문서화)

---

## 🎯 주요 기능

• **AI 여행 플래너**: OpenAI API를 활용한 대화형 AI가 사용자의 여행 스타일(맛집 탐방, 여유로운 힐링, 관광&인생샷)을 분석하여 맞춤형 여행 일정을 자동 생성하고 대화 히스토리를 저장

• **여행지 및 축제 탐색**: 한국관광공사 TourAPI와 KCISA 공공데이터를 연동하여 전국의 여행지와 축제 정보를 실시간으로 검색하고, 지역/카테고리별 필터링 및 상세 정보 제공

• **테마별 여행 추천**: 계절별(봄꽃, 여름휴가, 가을단풍, 겨울축제) 테마 페이지를 통해 시즌에 맞는 여행지와 코스를 큐레이션하여 제공

• **나만의 코스 관리**: 사용자가 직접 여행 코스를 생성·수정·삭제할 수 있으며, AI 추천 코스를 저장하고 편집하여 개인화된 여행 계획 수립 가능

• **지도 시각화 및 장소 관리**: Google Maps API와 Kakao 지도를 활용하여 여행 코스와 찜한 장소를 지도에 시각화하고, 좌표 기반으로 경로를 확인

• **코스 공유 및 소셜 기능**: 작성한 여행 코스를 공개/비공개로 설정하고, 다른 사용자의 코스에 좋아요·댓글·리뷰를 남기며 조회수 집계 및 공유 기능 제공

• **이메일/SMS 인증**: Gmail SMTP와 CoolSMS를 활용한 이중 인증 시스템으로 회원가입 시 본인 인증을 진행하고 계정 보안 강화

• **관리자 콘솔**: 신고 관리, 회원/탈퇴자 목록 조회, 통계 대시보드, CSV/엑셀 백업 기능을 제공하여 서비스 운영 및 모니터링 지원

---

## 🚀 실행 방법

### 사전 요구사항

1. **MySQL 8.x** 설치 및 `planit` 데이터베이스 생성
2. **Redis** 서버 실행
3. **Node.js** (v16 이상) 및 **npm** 설치
4. **JDK 17** 이상 설치
5. 외부 API 키 발급
   - OpenAI API Key
   - Kakao REST API Key
   - Google Maps API Key
   - KCISA API Key
   - CoolSMS API Key
   - Gmail 앱 비밀번호

### Backend 실행 (pib)

```bash
cd pib

# application.properties 설정 (API 키, DB 정보 등)
# src/main/resources/application.properties 파일 수정

# 실행
./gradlew clean bootRun

# 또는 JAR 빌드 후 실행
./gradlew bootJar
java -jar build/libs/*.jar
```

백엔드 서버는 기본적으로 `http://localhost:8080`에서 실행됩니다.

### Frontend 실행 (pfa)

```bash
cd pfa

# 의존성 설치
npm install

# 개발 서버 실행 (포트 80)
npm start

# 프로덕션 빌드
npm run build
```

프론트엔드는 기본적으로 `http://localhost` (포트 80)에서 실행됩니다.

---

## 🔧 환경 변수 설정

### Backend (application.properties)

```properties
# Database
spring.datasource.url=jdbc:mysql://localhost:3306/planit?serverTimezone=Asia/Seoul
spring.datasource.username=<your-username>
spring.datasource.password=<your-password>

# Redis
spring.data.redis.host=localhost
spring.data.redis.port=6379

# Email
spring.mail.username=<your-gmail>
spring.mail.password=<gmail-app-password>

# SMS
coolsms.api.key=<your-coolsms-key>
coolsms.api.secret=<your-coolsms-secret>

# API Keys
openai.api.key=<your-openai-key>
kcisa.key=<your-kcisa-key>
kakao.api.key=<your-kakao-js-key>
kakao.rest.key=<your-kakao-rest-key>

# File Upload
file.upload.dir=C:/planit/uploads
file.access-path=/uploads/
```

### Frontend (.env)

```env
REACT_APP_GOOGLE_MAPS_API_KEY=<your-google-maps-key>
```

---

## 📖 API 문서

주요 엔드포인트:

| 엔드포인트 | 메서드 | 설명 | 권한 |
|-----------|--------|------|------|
| `/api/auth/signup` | POST | 회원가입 | Public |
| `/api/auth/login` | POST | 로그인 | Public |
| `/api/chat/ask-ai` | POST | AI 코스 추천 | USER |
| `/api/festival` | GET | 축제 리스트 | Public |
| `/api/tour/detail/user/{id}` | GET | 여행지 상세 | USER |
| `/api/my-course` | CRUD | 나만의 코스 관리 | USER |
| `/api/admin/reports` | GET | 신고 목록 | ADMIN |

자세한 API 스펙은 각 컨트롤러 파일을 참고하세요.

---

## �‍💻 담당 역할 및 API 연동 구현

### 여행지/축제 정보 제공 및 API 연동 구현
• 한국관광공사 TourAPI 기반 카테고리별 검색 조건 세분화 구현
• 시도 조합으로 제공 지역 구분 및 세부 지역 검색 기능 개발
• 사용자 중심의 여행지 상세 정보 제공 및 필터링 기능 구현
• 여행지 상세 정보 제공 시 스크랩 여부 확인 및 이미지 제공 등 DTO 분류 및 API 호출 로직 정리

### 여행 코스 및 인프라 (코스 데이터 / 상호작용 / 시스템 백엔드 구조 설계)
• 여행 코스 CRUD 기능 구현 및 사용자 권한 검증 로직 개발
• AI 추천 코스 저장 및 편집 기능 구현
• 코스 좋아요/조회수/공유 등 상호작용 집계 기능 개발

### 지도 기반 여행지 시각화 기능 개발
• Kakao Map API 연동으로 검색한 여행지를 위치 기반으로 마커 표시, 카테고리 별로 필터 기능 구현
• 마커 클릭 시 여행지 상세 정보 팝업 표시 및 스크랩 기능 연동
• 코스 데이터 기반 경로 시각화 및 일정별 마커 표시 기능 구현
• 프론트엔드 맵 컴포넌트 개발 및 UX 최적화

---

## 🐛 기술적 문제 해결 사례 (Trouble Shooting)

### [문제] TourAPI 서비스 중단(점검 시 서비스 여행지 검색 기능 전체가 비활성 문제
• **상황**: 검색, 여행지 상세 조회, 코스 구성 등 주요 기능이 모두 의존하고 있어 서비스 전체가 동작 불가

• **원인 분석**: TourAPI 인프라 정비로 인해 API 응답이 불안정 또는 완전 중단 상태

**[해결 방법]**
• 대체 공공데이터 API(KCISA Open API)를 전급 검토하여 즉시 전환
• KCISA 데이터가 구조가 TourAPI와 다르므로 백엔드에서 DTO를 분리하여 프론트에서 별도 처리 없이 대응
• 맵핑 변환하는 매핑 레이어 개발

**[성과]**
• TourAPI 전면 장애 상황에서도 서비스 중단 없이 복구
• 데이터 변경 시에도 매핑 레이어 수정만으로 유연하게 대응

---

### [문제] 지역 기반 검색 시 세부 지역 카테고리 정렬이 검색되지 않는 문제
• **상황**: "서울 중구", "제주 애월" 등 세부 지역 카테고리를 입력하면
KCISA가 광역 시 지역 전체를 반환하여 관련 없는 관광지가 섞여 나옴

• **원인 분석**: KCISA가 기본 파라미터가 광역단위 매핑을 수용
지역명과 주소 필드가 구조화되어 있지 않아 필터링 추후 필요

**[해결 방법]**
• 검색어를 생성할 때, 동 단위로 분리하여 나눠 검색 구조로 재설계
• KCISA 응답 후 중 주소(소재지)를 수동해 2차 필터링 수행
• 위치 기반 정렬(거리순) 로직 추가 시 실제 사용자 입장 향상
• 카테고리 매핑 로직 이미지화하여 직관 구조도 작성

---

### [문제] 지도 기반 시각화 시 세부 지역 검색 결과가 정렬이 검색되지 않는 문제
• **상황**: 세부 지역 검색 시 전체 광역시 관광지가 검색되어 관련 없는 관광지가 혼재

• **원인 분석**: KCISA가 기본 검색 파라미터가 광역단위 매핑을 수용
지역명과 주소 필드가 구조화되지 않아 필터링이 추후 수행

**[해결 방법]**
• 경계값을 설정하여, 동 단위로 분리하여 나눠 검색 구조로 재설계
• KCISA 응답 후 중 주소(소재지)를 수동해 2차 필터링 수행
• 위치 기반 정렬(거리순) 로직 추가 시 실제 사용자 입장 향상
• 카테고리 매핑 로직 이미지화하여 직관 구조도 작성

---

### [문제] AI 여행지 추천 결과가 실제 여행 코스와 연결되지 않는 문제
• **상황**: 사용자가 선택한 여행지와 AI 추천이 무관하거나 지나치게 일반적인 장소 반복 추천되는 문제 발생

• **원인 분석**: 프롬프트에서 여행지 문맥 카테고리가 정보를 충분히 제공하지 않음
초반 기준이 명확하지 않아 AI가 보편적인 답변을 생성

**[해결 방법]**
• 여행지의 데이터, 분류(카, 위치 특성을 분석해 프롬프트에 포함
• "선택한 여행지 조합을 매 적합한 장소 추천" 규칙 명시화
• JSON 기반 결과 스키마를 AI 응답에 구조화하여 FrontEnd서 별로 기능화도록 함

**[성과]**
• AI 추천 정확도 약 55% → 92%까지 개선
• 관광명 검색 결과 반영이 감소해 사용자 만족도 향상 - 장소 수동 입력화


---

---

## 📝 개발 가이드

### 코드 스타일
- Backend: Spring Boot 컨벤션 준수
- Frontend: React Hooks 패턴 사용
- 변수명: camelCase
- 클래스명: PascalCase

### Git 브랜치 전략
- `main`: 프로덕션 배포 브랜치
- `develop`: 개발 통합 브랜치
- `feature/*`: 기능 개발 브랜치
- `hotfix/*`: 긴급 수정 브랜치

### 커밋 메시지 규칙
```
feat: 새로운 기능 추가
fix: 버그 수정
docs: 문서 수정
style: 코드 포맷팅
refactor: 코드 리팩토링
test: 테스트 코드
chore: 빌드 설정 등
```

---

## 📄 라이선스

이 프로젝트는 개인 포트폴리오 프로젝트입니다.

---

## 👥 개발자

- **개발자**: 이영민
- **이메일**: babdoy123@gmail.com
- **GitHub**: https://github.com/ymle01

---

## 🔗 관련 링크

- [Backend 상세 문서](./planit/pib/README.md)
- [Frontend 상세 문서](./planit/pfa/README.md)
---

**Made with ❤️ by Plan-It Team**
