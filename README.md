<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2563EB,100:14B8A6&height=180&section=header&text=Welcome%20to%20suhannoh%20GitHub!👋&fontSize=36&fontColor=ffffff&animation=fadeIn&fontAlignY=36" />
</p>

<h1 align="center">노수한 | Suhan Noh</h1>

<p align="center">
  <a href="mailto:suhannoh@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-suhannoh%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white" />
  </a>
</p>

---

## About

#### 안녕하세요, 신입 백엔드 개발자 노수한입니다.

Java/Spring Boot 기반으로 백엔드 개발을 학습하고 있습니다.  
단순히 기능을 구현하는 것보다, 서비스의 핵심 판단과 데이터가 서버에서 일관되게 관리되는 구조에 관심이 있습니다.

팀 프로젝트에서는 추천 로직, 캐싱, 배치 알림처럼 서버가 결정하고 처리해야 하는 흐름을 구현했습니다.  
개인 프로젝트에서는 AI Agent를 활용하되, 생성된 결과를 그대로 공개하지 않고 검토 가능한 데이터와 사용자 공개 데이터를 분리하는 방식에 관심을 두고 실험했습니다.

---

## Skills

### Backend
![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=flat-square&logo=spring&logoColor=white)

### Database
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

### Frontend
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

### Tools
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## Projects

### 멍냥트립

: 사용자, 반려동물, 날씨 정보를 기반으로 반려동물 동반 장소를 추천하고 알림으로 전달하는 서비스

`Java 21` `Spring Boot` `JPA` `PostgreSQL` `PostGIS` `Redis` `Gemini` `공공데이터 날씨 API` `NCloud SENS`  
FE(1명), BE(2명), INFRA(1명) | ROLE: Backend

[GitHub](https://github.com/suhannoh/meongnyangtrip-portfolio)

> - 서버 주도 추천 파이프라인 설계
>
>   - 사용자, 반려동물, 날씨 정보를 결합해 추천 후보를 구성하고, 거리 필터링과 점수 기반 랭킹으로 최종 추천 장소를 선정했습니다.
>   - AI가 추천 순위를 바꾸지 않도록 추천 결정은 서버 로직에서 수행하고, Gemini는 추천 이유를 생성하는 설명 전용 구조로 분리했습니다.
>   - 후보 탐색, 점수 계산, 추천 근거 생성, AI 설명 생성, 결과 캐싱 단계를 나누어 추천 파이프라인을 구성했습니다.
>
> - Redis 기반 캐싱과 중복 요청 제어
>
>   - 날씨 API, Gemini 응답, 당일 추천 결과를 Redis에 캐싱해 외부 API 호출 비용과 응답 시간을 줄였습니다.
>   - 사용자 단위 Redis Lock을 적용해 동일 사용자의 중복 추천 요청을 차단했습니다.
>   - 최근 추천 장소 이력을 Redis List로 관리하고 점수 계산 시 패널티를 적용해 반복 추천을 줄였습니다.
>
> - 배치 알림 처리 성능 개선
>
>   - 추천, 로그 저장, 알림 발송까지 이어지는 End-to-End 파이프라인을 구현했습니다.
>   - Java 21 Virtual Thread와 Semaphore를 활용해 공공데이터 날씨 API, Gemini, NCloud SENS 등 외부 I/O 중심의 병목을 줄이고, 배치 처리 동시성을 제어했습니다.
>   - 테스트 기준 배치 처리 시간이 188,972ms에서 1,950ms로 단축되었고, 처리량은 5.29 TPS에서 512.82 TPS로 개선되었습니다.

---

### Zup

: AI Agent를 활용한 개발 흐름과 데이터 검토 기준을 학습하기 위해 만든 무료 혜택 큐레이션 개인 MVP

`Java 21` `Spring Boot` `PostgreSQL` `Next.js` `React` `Docker Compose`  
ROLE: Planning + Service Structure + Agent Workflow

[GitHub](https://github.com/suhannoh/zup) | [Demo](https://zupday.kr/)

> - 혜택 탐색 서비스 구조 구성
>
>   - 생일, 멤버십, 통신사, OTT 등 여러 곳에 흩어진 무료 혜택 정보를 카테고리와 브랜드 기준으로 탐색할 수 있도록 구성했습니다.
>   - 사용자 화면에서는 검토가 완료된 혜택만 조회할 수 있도록 Public API와 관리자용 API의 역할을 나누었습니다.
>   - 혜택, 브랜드, 출처, 검토 상태를 서버에서 관리하며 사용자에게 보여줄 데이터 기준을 정리했습니다.
>
> - AI Agent 활용 흐름 실험
>
>   - Codex와 Hermes를 활용해 요구사항 정리, 혜택 후보 정리, 코드/문서 검토, 반복 구현 보조 흐름을 실험했습니다.
>   - AI가 정리한 혜택 후보를 바로 사용자에게 공개하지 않고, 공식 출처와 필수 정보를 확인한 뒤 반영하는 방식으로 구성했습니다.
>   - 현재 약 100개의 혜택 데이터를 검토해 서비스 화면에 노출하고 있습니다.
>
> - 배포와 검증 흐름 정리
>
>   - Docker Compose 기반으로 프론트엔드, 백엔드, DB 실행 환경을 구성했습니다.
>   - 테스트, 빌드, 기본 smoke check를 거쳐 배포할 수 있도록 검증 흐름을 정리했습니다.

---

## Education

### 연세IT미래교육원 AI 활용 실무 풀스택 개발자 과정

`2025.09 ~ 2026.05`

Java/Spring Boot 기반 백엔드와 React 기반 프론트엔드 개발을 학습하고,  
팀 프로젝트와 개인 프로젝트를 통해 기획, 개발, 배포 과정을 경험했습니다.

---

## Certificate

| 자격증 | 발급기관 | 취득일 |
| --- | --- | --- |
| 정보처리기사 | 한국산업인력공단 | 2025.12 |
| 정보처리기능사 | 한국산업인력공단 | 2025.07 |
| 전기기능사 | 한국산업인력공단 | 2020.09 |
