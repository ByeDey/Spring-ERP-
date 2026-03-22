# 🏢 GWERP — Spring 기반 그룹웨어 ERP 시스템

> Java Spring MVC + MyBatis + Oracle DB로 구현한 기업용 그룹웨어 웹 애플리케이션

---

## 📌 프로젝트 개요

| 항목 | 내용 |
|------|------|
| 프로젝트명 | GWERP (GroupWare ERP) |
| 유형 | 팀 프로젝트 |
| 기간 | 20XX.XX ~ 20XX.XX |
| 인원 | X명 |
| 역할 | (예: 로그인·인증, 결재 모듈 담당) |

사원 관리, 근태, 전자결재, 메시지, 급여, 공지사항 등 기업 내 다양한 업무를 하나의 플랫폼에서 처리할 수 있는 **그룹웨어 ERP 시스템**입니다.

---

## ✨ 주요 기능

### 👤 인증 / 로그인
- JWT 기반 로그인 및 세션 관리
- 비밀번호 찾기 (OTP 이메일 발송)
- QR 코드 생성을 통한 사원 인증

### 🧑‍💼 사원 관리 (Employee)
- 사원 등록 / 수정 / 목록 / 상세 조회
- 부서(Dept) 및 권한(Auth) 관리
- 공통 코드(CmmCode) 관리

### ✅ 전자결재 (Approval)
- 결재 요청 / 동반 결재 / 결재 반려
- 결재 완료 목록 / 진행 현황 조회

### 🕐 근태 관리 (Commute)
- 출퇴근 기록 조회
- 근무 시간 자동 계산 유틸리티

### 💬 메시지 (Message)
- 사내 1:1 메시지 전송 / 수신 / 답장 / 삭제
- 쪽지 전달(Pass) 기능

### 📋 공지사항 (Notice)
- 공지 작성 / 수정 / 삭제
- 관리자·부서·전체 공지 구분 목록

### 💰 급여 (Salary)
- 급여 정보 조회

### 🗂️ 문서 / 첨부파일
- 문서 등록 및 조회
- 파일 업로드 / 다운로드

### 💡 기타
- 대시보드 메인 화면
- 댓글(Reply) 기능
- 권한별 UI 메뉴 노출 제어

---

## 🛠️ 기술 스택

| 구분 | 기술 |
|------|------|
| Language | Java |
| Framework | Spring MVC 3.x, Spring Security 3.x, Spring WebSocket 4.x |
| View | JSP, JSTL, jQuery, Ajax |
| ORM | MyBatis 3.x |
| Database | Oracle DB (ojdbc6) |
| Build | Maven |
| IDE | Eclipse (STS) |
| 인증 | JWT (jjwt 0.9.1) |
| 메일 | Jakarta Mail (OTP 발송) |
| QR | Google ZXing 3.5.2 |
| 파일 업로드 | Apache Commons FileUpload |

---

## 📁 프로젝트 구조

```
GroupWare/
└── src/main/java/
    ├── Login/          # 로그인, 비밀번호 찾기
    ├── admin/          # 사원·부서·권한·공통코드 관리
    ├── approval/       # 전자결재
    ├── attach/         # 파일 업로드/다운로드
    ├── commute/        # 근태 관리
    ├── document/       # 문서 관리
    ├── employee/       # 사원 CRUD
    ├── jwt/            # JWT 유틸리티
    ├── main/           # 대시보드, 라우터
    ├── message/        # 사내 메시지
    ├── notice/         # 공지사항
    ├── qrGenerator/    # QR 코드 생성
    ├── reply/          # 댓글
    ├── salary/         # 급여
    ├── vacation/       # 휴가
    └── mybatis/        # MyBatis SQL mapper XML
```

---

## ⚙️ 실행 방법

### 사전 요구 사항
- Java 1.6+
- Oracle DB
- Apache Tomcat 8.x+
- Maven

### 1. 저장소 클론
```bash
git clone https://github.com/le-30/GWERP.git
cd GWERP/GroupWare
```

### 2. Oracle DB 설정
`src/main/resources/` 의 DB 설정 파일에서 접속 정보를 본인 환경에 맞게 수정합니다.
```xml
<property name="url" value="jdbc:oracle:thin:@localhost:1521:xe"/>
<property name="username" value="아이디"/>
<property name="password" value="비밀번호"/>
```

### 3. Maven 빌드 및 배포
```bash
mvn clean package
# 생성된 .war 파일을 Tomcat webapps/ 에 배포
```

---

## 👥 팀원 및 역할

| 이름 | 담당 기능 |
|------|----------|
| 홍길동 | 로그인/인증, 전자결재 |
| (팀원2) | 사원관리, 부서/권한 |
| (팀원3) | 근태, 급여, 공지사항 |
| (팀원4) | 메시지, 파일 첨부, 대시보드 |

---

## 📸 화면 예시

> 스크린샷을 `/docs/screenshots/` 폴더에 추가 후 아래 경로를 수정하세요.

| 대시보드 | 전자결재 | 메시지 |
|---------|---------|-------|
| ![dashboard](docs/screenshots/dashboard.png) | ![approval](docs/screenshots/approval.png) | ![message](docs/screenshots/message.png) |

---

## 📝 느낀 점 / 트러블슈팅

- **JWT + Spring Security 연동**: Spring Security 3.x 환경에서 JWT 필터를 수동으로 등록하는 과정에서 어려움이 있었고, `OncePerRequestFilter`를 활용해 해결했습니다.
- **권한별 메뉴 제어**: 서버 권한 정보를 `window.userAuths`로 프론트에 전달해 Ajax 라우터에서 동적으로 버튼 노출을 제어하는 구조로 구현했습니다.
- *(본인이 겪은 문제와 해결 방법을 여기에 추가하세요)*

---

## 📄 라이선스

This project is for educational purposes.
