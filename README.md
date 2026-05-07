# ![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=20&height=200&animation=twinkling&section=header&text=BeatBuddy&fontSize=80&fontAlign=75&fontAlignY=36)

# BeatBuddy - 음악 취향 기반 친목 커뮤니티 서비스

## 👀 목차
1. [👥 팀원](#팀원)
2. [📚 프로젝트 개요](#프로젝트-개요)
3. [🔧 시스템 아키텍처](#시스템-아키텍처)
4. [📅 요구사항 명세서](#요구사항-명세서)
5. [🪧 ERD](#erd)
6. [🗃️ 테이블 명세서](#테이블-명세서)
7. [🎯 API 명세서](#api-명세서)
8. [🧪 테스트 계획 및 결과 보고서](#테스트-계획-및-결과-보고서)

---

### 👥 팀원

| 채팅(팀장) | 음악 | 인증 | 친구 | 마이페이지 | 그룹 |
| --- | --- | --- | --- | --- | --- |
| 김예지 | 박하얀 | 방지혁 | 이다윗 | 허진호 | 황희수

## 📌 프로젝트 개요

### 📘 프로젝트 소개

**BeatBuddy**는 소속 집단 구성원들의 음악적 취향 데이터를 분석하여 정서적 공감대가 높은 동료를 연결해 주는 팀 빌딩 지원 플랫폼입니다.

가입 시 최애곡 10곡을 선택하면, 곡의 음악적 특성을 분석하여 16차원 취향 벡터를 생성합니다. 같은 그룹에 속한 멤버들과 코사인 유사도를 계산해 취향이 비슷한 사람을 추천받고, 마음에 드는 상대에게 친구 신청을 보내 1:1 채팅으로 대화할 수 있습니다.

---

### ✅ 배경: 왜 이 서비스가 필요한가?

**취향 기반 연결의 필요성**

기존 소셜 서비스는 외형이나 조건 중심의 매칭으로 인해 실제 깊이 있는 정서적 교감을 기대하기 어렵고, 이는 곧 대화의 단절과 관계 유지를 위한 심리적 피로감으로 이어집니다.

**음악이 가진 연결의 힘**

음악 취향은 성격, 감성, 라이프스타일과 높은 상관관계를 가집니다. 같은 곡을 좋아한다는 사실만으로도 대화의 물꼬를 트기 쉬워집니다.

**그룹 기반 안전한 만남**

그룹 안에서만 추천이 이루어지므로, 불특정 다수와의 무작위 연결이 아닌 신뢰할 수 있는 환경에서 친구를 사귈 수 있습니다.

---

## 🔧 시스템 아키텍처

<details>
<summary> 시스템 아키텍처</summary>

<br>

> ![Web App Reference Architecture](https://github.com/user-attachments/assets/4f84192b-62fc-4ae6-897b-765a117cd097)

</details>

---

## 📋 요구사항 명세서
> [요구사항 명세서](https://docs.google.com/spreadsheets/d/1bW-t6EJQ1NW_uqkoiAgVqqeyeDuuh2muPwpv8ee4Y2s/edit?usp=sharing)

---

## 🪧 ERD
> [ERD](https://www.erdcloud.com/d/MEMRtro3g2PtxsnCE)

---

## 🗃️ 테이블 명세서
> [테이블 명세서](https://docs.google.com/spreadsheets/d/1bW-t6EJQ1NW_uqkoiAgVqqeyeDuuh2muPwpv8ee4Y2s/edit?usp=sharing)

---

## 🎯 API 명세서

> [API 명세서](https://www.notion.so/5-API-f76901cdc00882208183014b29afe442?source=copy_link)



---

---

## 🧪 테스트 계획 및 결과 보고서

> [테스트 계획 및 결과 보고서](https://docs.google.com/spreadsheets/d/1_yQBYho9SeX9E9EfWcyGfwN5yh79QyOxMhvVj6B-Qds/edit?gid=908489767#gid=908489767)

---

## 🛠️ 기술 스택

<details>
> <summary> 기술 스택</summary>

> <br>

| 구분 | 기술 |
|------|------|
| Frontend | ![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white) |
| Backend | ![SpringBoot](https://img.shields.io/badge/SpringBoot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white) |
| Database | ![MariaDB](https://img.shields.io/badge/MariaDB(MySQL)-003545?style=for-the-badge&logo=mariadb&logoColor=white) |
| ORM | ![MyBatis](https://img.shields.io/badge/MyBatis-000000?style=for-the-badge) |
| 인증 | ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white) |
| 이메일 | ![Gmail](https://img.shields.io/badge/GmailSMTP-EA4335?style=for-the-badge&logo=gmail&logoColor=white) |
| 실시간 채팅 | ![WebSocket](https://img.shields.io/badge/WebSocket(STOMP)-010101?style=for-the-badge) |
| 외부 API | ![Spotify](https://img.shields.io/badge/SpotifyAPI-1DB954?style=for-the-badge&logo=spotify&logoColor=white)&nbsp;![RapidAPI](https://img.shields.io/badge/RapidAPI-0055DA?style=for-the-badge&logo=rapid&logoColor=white) |

</details>

---

## 📌 주요 기술적 의사결정

<details>
<summary> 주요 기술적 의사결정 </summary>

<br>

**취향 벡터 설계**
단순 평균이 아닌 평균 + 표준편차를 함께 저장하는 16차원 벡터를 설계했습니다. 표준편차를 포함함으로써 "취향의 폭"까지 반영할 수 있어 매칭 정확도를 높였습니다.

**viewed_profiles 설계**
Redis 대신 DB 테이블로 구현하되 `ON DUPLICATE KEY UPDATE`를 활용해 넘긴 프로필을 30일 후 재노출하는 로직을 구현했습니다. MVP 이후 Redis로의 교체를 고려한 구조입니다.

**채팅방 중복 방지**
`user_a_id < user_b_id` CHECK 제약 조건과 UNIQUE KEY를 조합해 두 사용자 간 채팅방이 중복 생성되는 것을 DB 레벨에서 원천 차단했습니다.

</details>

---

## CI/CD

<details>
<summary> 아키텍쳐 </summary>
</details>
<details>
<summary> 빌드구성 </summary>
<img width="1201" height="651" alt="beatbuddy-build-pipeline (1) drawio (5)" src="https://github.com/user-attachments/assets/0b7ee82e-4e86-4b0c-8cae-344970ce7f1b" />
</details>

---

### 회고록

#### 김예지
> 

#### 박하얀
> 

#### 이다윗
>

#### 황희수
> 

![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=20&height=100&section=footer)
