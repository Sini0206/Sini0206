## Hi there 👋

<!--
**Sini0206/Sini0206** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<a href="https://github.com/devxb/gitanimals">
<img
  src="https://render.gitanimals.org/farms/Sini0206"
  width="600"
  height="300"
/>
</a>

[놀러오세요! 기술 블로그](https://velog.io/@sumurf/posts)🤗 

---
# [UOSLIFE](https://www.uoslife.team) 
- 기간: 2024.12 ~ 현재
- 소개: 서울시립대학교 캠퍼스 라이프 플랫폼 운영 동아리
- 서비스 규모: 누적 가입자 2.2만 명, DAU 1,200명ㆍWAU 5,200명 규모 프로덕션 운영
- Github 링크: https://github.com/uoslife

# 주요 프로젝트
## 1. 시대팅 시즌 7 
- 소개: 서울시립대학교 재학생·졸업생 대상 유료 소개팅 매칭 서비스
- 기간: 2026.02 ~ 2026.05
  
### 결제 시스템 재설계 
- 기술 스택: `Kotlin`, `Spring Boot`, `Spring Data JPA`, `PostgreSQL`, `Spring Batch`
- 역할: 결제 도메인 전체 설계 및 구현
- 배경: 이전 시즌(시즌 6) 당시 주문 상태·결제 정보가 단일 엔티티에 혼재되어 결제 최종 상태만 남는 구조. CS 22건 발생 당시 결제 흐름 복기 불가
- 수행 내용
  - 주문과 결제 이벤트 1:N 분리, 이벤트는 Append-only 로그로 설계
  - PG사 응답 원문을 JSONB로 저장
  - 상태 머신(FSM) 기반 주문 상태 전이 관리
  - 중복 웹훅 수신에 대한 멱등성 처리 
  - 외부 API 호출과 DB 트랜잭션 범위 분리로 커넥션 풀 고갈 방지
  - PG사 원장-내부 DB 간 대사 배치 구축
- 성과:
  - 결제 요청 4배 증가(648→2,591건) 환경에서 CS 22건 → 0건
  - 결제 실패율 25.31% → 4.44%
  
### 채팅 시스템 아키텍처 설계
- 기술 스택: `Kotlin`, `Spring WebFlux`, `Redis`, `MongoDB`, `AWS ECS`
- 역할: 채팅 시스템 전체 아키텍처 설계 및 구현
- 수행 내용
  - Transactional Outbox 패턴으로 메시지 유실 방지 (DB 저장과 발행의 원자성 보장)
  - 메시지 발행 서버와 소켓 서버 물리적 분리, 장애 전파 차단
  - Redis Streams로 접속 유저용 수신 큐·미접속 유저용 알림 큐 분리 운영
## 2. 대학 시간표 검색 서비스 
- 기간: 2025.02 ~ 2025.03
- 기술 스택: `Kotlin`, `Spring Boot`, `Spring Data JPA`, `PostgreSQL`
- 역할: 시간표 생성 및 시간표 조회 API 개발
- 수행 내용
  - 다중 교과목 속성을 비트마스크로 압축하여 JOIN 연산 제거
  - 커서 기반 페이지네이션 전환으로 인덱스 활용 개선
- 성과: 평균 응답 속도 93.5% 향상 (2초 → 0.13초)
