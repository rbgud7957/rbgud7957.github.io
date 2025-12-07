---
title: "Todo App – 프로젝트 리뷰"
date: 2025-12-07
categories: ["Project", "Review"]
---

# 🧩 Todo App – 프로젝트 리뷰

## 📝 1. 프로젝트 개요
가장 최근 진행한 프로젝트로 로그인 기반의 Todo 리스트 웹 애플리케이션입니다.  
사용자는 회원가입 후 로그인하여 개인별 할 일 목록을 관리할 수 있으며,  
할 일 등록, 삭제, 수정, 완료 처리 등 핵심 기능을 수행할 수 있습니다.

이 프로젝트는 **Next.js (Frontend)**,  
**Node.js + Express (Backend)**,  
그리고 **MongoDB (Database)** 를 사용해 풀스택 아키텍처로 구축했습니다.

배포 주소 → https://todo-app-eight-alpha-53.vercel.app/

---

## ⚙️ 2. 기술 스택  

### 💻 Frontend  
- **Next.js ** (App Router 기반 라우팅 구조)  
- **Axios** (API 연동, 인터셉터로 JWT 자동 주입)  
- **Tailwind CSS** (빠른 스타일링과 반응형 UI 구성)

### ⚙️ Backend  
- **Node.js + Express.js** (REST API 구축)  
- **JWT (jsonwebtoken)** (토큰 기반 인증)  
- **bcrypt** (비밀번호 해싱)  
- **dotenv** (환경변수 관리)  
- **Mongoose** (MongoDB ODM)

### 🗄️ Database  
- **MongoDB Atlas**  
- 사용자(User), 할 일(Todo) 스키마 구성  
- 로그인한 사용자별 Todo 구분 관리

---

## 🔧 3. 주요 기능 상세

### 👤 회원 인증
- 회원가입 시 비밀번호 **bcrypt 해싱** 저장  
- 로그인 성공 시 **JWT 토큰 발급**  
- 브라우저 **localStorage**에 토큰 저장해 인증 유지  
- 인증이 필요한 페이지에서 **Protected Route 적용**  
- 로그아웃 시 토큰 삭제 후 로그인 페이지로 이동  

### 🧾 Todo CRUD
#### 등록
- 입력한 텍스트를 POST 요청으로 전송 → DB 저장  
- 저장 후 즉시 화면에 반영  

#### 조회
- 로그인 사용자의 Todo만 DB에서 GET 요청으로 불러오기  
- 페이지 로딩 시 자동 렌더링  

#### 수정 (예정)
- 제목 클릭 → 인라인 수정 기능 예정  
- 완료 상태 토글 기능 추가 예정  

#### 삭제
- 삭제 버튼 → DELETE 요청  
- DB 반영 후 UI 즉시 갱신  

### 인증 및 보안  
- 모든 요청에 JWT 자동 포함 (Axios 인터셉터)  
- bcrypt로 비밀번호 보안 강화  
- CORS 설정 → 프론트/백 간 통신 허용  

---

## 🧩 4. 프론트엔드 구조
- `/login` → 로그인  
- `/register` → 회원가입  
- `/` → 메인 Todo 페이지  
- `axiosInstance.js`에서 인증 헤더 자동 설정  
- `TodoForm` 컴포넌트로 추가 기능 관리  

---

## 🧩 5. 백엔드 구조
- `routes/auth.js` → 로그인/회원가입  
- `routes/todos.js` → Todo CRUD API  
- `controllers/authController.js` → 로그인 & JWT 발급  
- `controllers/todoController.js` → CRUD 로직  
- `middleware/verifyToken.js` → 토큰 검증  
- `models/User.js`, `models/Todo.js` → 데이터 스키마  

---

## 🚀 6. 현재 구현된 기능 요약  

-  회원가입 / 로그인 / 로그아웃  
-  JWT 기반 인증 / 로그인 유지  
-  Todo 생성 / 조회 / 삭제  
-  사용자별 Todo 데이터 분리  
-  MongoDB Atlas 연동  
-  Vercel + Render 배포 완료  

---

## 🎯 7. 다음 목표  
-  Todo 수정 기능 추가  
-  완료 상태 토글  
-  Todo 통계 페이지  
-  반응형 UI 개선  

---

## 🔧 8. 트러블슈팅  

- **JWT 만료 문제** → 토큰 갱신 & 자동 로그아웃 기능 적용  
- **`todos.map is not a function` 오류**  
  → API 응답 구조를 배열 형태로 통일  
- **프론트 요청이 백엔드에 도달하지 않는 문제**  
  → axiosInstance에서 baseURL 및 interceptor 수정  
- **MongoDB 및 CORS 설정 오류**  
  → `.env` 변수와 Express CORS 설정 수정  
- **배포 후 CORS 문제**  
  → Render 백엔드에 Vercel 프론트 주소 추가해 해결  

---

## 💬 9. 느낀 점  

이번 프로젝트를 통해 프론트엔드와 백엔드가 **실제로 어떻게 연결되고 통신하는지** 제대로 이해하게 되었습니다.  
특히 JWT 기반 인증 구조와 Next.js App Router 구조를 다루면서  
사용자 인증 흐름 전반을 설계하고 구현하는 경험을 쌓을 수 있었습니다.

MongoDB, Express, Next.js가 함께 동작하는 전체 흐름을 직접 구성해보며  
풀스택 개발자로서 한 단계 성장한 프로젝트였습니다.

---

