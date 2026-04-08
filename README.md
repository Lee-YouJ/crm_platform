# CRM Platform

본 프로젝트는 풀스택 CRM(고객 관계 관리) 플랫폼으로 관리자 웹, 사용자 서비스 웹, 그리고 백엔드 API 서버까지 총 3개의 핵심 모듈로 구성되어 있습니다. 

## 📂 프로젝트 구조

- `api/`: Node.js (Express) 기반 백엔드 API 서버
- `admin/`: React + Vite 기반 관리자 웹 패널
- `front/`: React + Vite 기반 일반 사용자용 웹 서비스

---

## 🚀 환경 설정 및 실행 방법 (How to Run Locally)

본 프로젝트는 의존성 관리를 위해 주로 `yarn` 패키지 매니저를 사용합니다.

### 1. 백엔드 API 서버 (`api`)

백엔드는 MySQL 데이터베이스와 연동되므로 로컬에 DB 환경이 세팅되어 있어야 합니다.

**사전 필수 조건**
- **Node.js** 환경 세팅
- **MySQL 서버** 실행 중 (포트 3306)
  - 기본 접속 정보: 아이디 `root` / 비밀번호 `password`
  - *(설정 정보가 다를 경우 `api/config/default.js` 에서 직접 수정하거나 환경 변수를 이용하세요.)*

**실행 순서**
1. 경로 이동 및 패키지 설치
   ```bash
   cd api
   yarn install
   ```
2. 데이터베이스 초기화 및 테이블 생성
   ```bash
   yarn create-db    # 'platform_db' 데이터베이스 생성
   yarn mig-all      # 테이블 자동 마이그레이션
   ```
3. 서버 시작
   ```bash
   yarn dev          # 개발 환경 실행 (nodemon 자동 리로드 지원)
   # 일반 실행의 경우: yarn start
   ```
   > 💡 접속 확인: 서버가 정상적으로 켜지면 터미널에 `http://localhost:4100` 로그가 출력되며, [http://localhost:4100/api-docs](http://localhost:4100/api-docs) 로 접속해 Swagger(API 명세서)를 확인할 수 있습니다.

---

### 2. 관리자 웹 콘솔 (`admin`)

시스템 관리용 프론트엔드입니다. (API 서버가 켜져 있어야 데이터를 정상적으로 불러올 수 있습니다.)

**실행 순서**
1. 경로 이동 및 패키지 설치
   ```bash
   cd admin
   yarn install
   ```
2. 프론트엔드 서버 시작
   ```bash
   yarn dev
   ```
   > 💡 실행 후 터미널에 표시되는 `http://localhost:xxxx` 주소(보통 `5173` 또는 다른 할당 포트)를 브라우저에 입력하여 접속합니다.

---

### 3. 사용자 웹 페이지 (`front`)

실제 고객/사용자가 접근하는 프레젠테이션용 프론트엔드입니다.

**실행 순서**
1. 경로 이동 및 패키지 설치
   ```bash
   cd front
   yarn install
   ```
2. 프론트엔드 서버 시작
   ```bash
   yarn dev
   ```
   > 💡 마찬가지로 터미널에 나타나는 로컬호스트 주소를 클릭하여 서비스에 접근할 수 있습니다.
