# [인수인계서] 이력서 및 포트폴리오 컨설팅 세션 인수인계

> **작성 일시**: 2026-10-19  
> **세션 ID**: `1c2cf410-cf89-4ca6-a3c1-f27ac112eb0b`  
> **컨설턴트 역할**: 5~6년 차 풀스택 개발자 맞춤형 이력서/포트폴리오 전문 컨설턴트  
> **재접속 명령어**:  
> `agy --conversation 1c2cf410-cf89-4ca6-a3c1-f27ac112eb0b --dangerously-skip-permissions`

---

## 1. 개발자 프로필 및 성향 (Client Profile)

* **이름 / 연차**: 장성환 님 / 6년 차 풀스택 개발자 (미드-시니어)
* **주요 도메인**: B2B 데이터센터 인프라 관리(DCIM) 솔루션, 지리 공간 데이터 기반 PWA 모던 웹
* **메인 기술 스택**:
  * 프론트엔드: Vue.js 2.x & 3.x (Composition API), Pinia, Element UI, Vant, Highcharts, D3.js, Vite, PWA
  * 백엔드 / DB: Java, Spring Framework (MVC), MyBatis, Oracle DB, Firebase (Firestore, Auth)
* **상황**: **첫 이직 준비 중**
* **작성 시 절대 원칙 (Client Philosophy)**:
  * ❌ **과장된 표현 절대 금지**: 근거 없는 수치(300% 향상 등)나 무책임한 뻥튀기 지양
  * ❌ **AI 티(냄새) 절대 지양**: 뜬구름 잡는 미사여구(시너지 창출, 패러다임 전환 등) 및 천편일률적 번역투 배제
  * ✅ **사실 기반(Fact-based) 실무 언어**: 실제 코드를 짜고 고민한 5~6년 차 개발자다운 담백한 기술적 의사결정, 트레이드오프, 트러블슈팅 중심 서술

---

## 2. 지금까지 진행된 핵심 컨설팅 및 의사결정 내역

### 1) 기존 노션 포트폴리오 진단 및 전면 개편
* **원본 노션 링크**: `https://simple-busby-0f0.notion.site/3f80aa834ca980b59f18f2186e412c42`
* **주요 조치 사항 5가지**:
  1. **타사 솔루션('애플망고') 노출 및 모방 프레임 제거**:
     * 특정 사명 전면 삭제. "이종 모니터링 시스템을 분석하여 DCIM 복잡도에 맞게 독자적으로 2-Way 일괄 구성 아키텍처로 재설계"로 워딩 격상.
  2. **'기여도 100%' 프레임 수정**:
     * 협업 능력 의구심을 방지하기 위해 "PL로서 엔드투엔드 설계 및 구현 전담 주도"로 전환.
  3. **교과서적 AI 요약투 제거 & 기술 디테일 보강**:
     * Oracle 시계열 버킷팅 집계 쿼리 최적화, 렌더링 부하 방지를 위한 컨테이너-컴포넌트 분리(`DcimChartPanel`), 템플릿 메타데이터 영속화 등 구체적 엔지니어링 메커니즘 명시.
  4. **프로젝트 02 (D3 계통 시각화 실패)의 자산화**:
     * "파트장이 수습해 준 실패작"이 아니라, "실시간 수집 엔진의 데이터 무결성을 보호하기 위한 선제적 연동 중단 의사결정"과 "대규모 SVG 렌더링 최적화 노하우 획득"이라는 시니어다운 교훈으로 리프레이밍.
  5. **프로젝트 04 (GS 인증)의 체계화**:
     * 단순 야근/갈아넣기 서술 탈피, "신규 DB 정합성 전수 복원 및 전사 공통 예외 처리 체계 수립"으로 격상.

### 2) 신규 프로젝트 05 탑재 (`cycling-app` - 자전거 스탬프 PWA)
* **목적**: 기존 4개 프로젝트가 모두 Vue 2(현재 EOL)에 머물러 있는 약점을 방어하고, 최신 모던 웹 스택(Vue 3, Pinia, Vite, PWA, Firebase) 및 공간 데이터 처리 역량을 증명.
* **AI-Native 엔지니어링 포지셔닝**:
  * 클라이언트의 고백: *"코딩 99%는 AI가 했고 나는 구조만 잡았다."*
  * 컨설팅 방향: 면접에서 "AI가 다 했다"고 하면 100% 탈락하므로, **"AI 코딩 에이전트를 테크니컬 레버리지로 오케스트레이션하여 1인 스프린트로 기획, 시스템 아키텍처 정의, PWA 배포까지 주도한 AI-Native 테크 리드"**로 포지셔닝.
  * 아키텍처 핵심: 오프라인 벡터 SVG 생성기(`stampGenerator.js`), GPS 100m 반경 및 24시간 쿨다운 안티-어뷰징, 하위 호환 데이터 마이그레이션, Polyline 코스 테마 동기화.

---

## 3. 생성된 작업 산출물 파일 목록

모든 산출물은 `C:\cycling-app\_no_commit_sessions`에 저장되어 Git 커밋에 포함되지 않습니다:

| 파일명 | 파일 설명 |
|:---|:---|
| [`session_ids.txt`](file:///C:/cycling-app/_no_commit_sessions/session_ids.txt) | 에이전트 세션 ID 및 CLI 재접속 명령어 모음 |
| [`portfolio_review.md`](file:///C:/cycling-app/_no_commit_sessions/portfolio_review.md) | 기존 노션 포트폴리오 정밀 진단 및 Before & After 개선 가이드 |
| [`NOTION_PORTFOLIO_DRAFT.md`](file:///C:/cycling-app/_no_commit_sessions/NOTION_PORTFOLIO_DRAFT.md) | **노션에 바로 복사-붙여넣기(`Ctrl + V`)할 수 있는 5개 프로젝트 전체 포트폴리오 완성본** |
| [`CYCLING_APP_INTERVIEW_GUIDE.md`](file:///C:/cycling-app/_no_commit_sessions/CYCLING_APP_INTERVIEW_GUIDE.md) | 자전거 스탬프 PWA 프로젝트 기술 면접 대비 Q&A 치트시트 (핵심 질문 5선) |
| [`HANDOVER_PORTFOLIO.md`](file:///C:/cycling-app/_no_commit_sessions/HANDOVER_PORTFOLIO.md) | **(현재 파일) 다음 세션을 위한 종합 인수인계 문서** |

---

## 4. 다음 세션에서 이어서 진행할 수 있는 추천 작업 (Next Steps)

1. **노션 적용 후 피드백 및 미세 튜닝**:
   * 클라이언트가 노션에 적용한 후 어색하거나 추가하고 싶은 실무 경험(특정 장애 해결, 고객사 피드백 등) 반영
2. **1~2장 분량의 '메인 경력기술서(요약본)' 작성**:
   * 링크드인, 원티드, 사람인 등에 PDF로 제출할 수 있는 핵심 이력서 텍스트 정리
3. **실전 기술 면접 모의 인터뷰 (Mock Interview)**:
   * 포트폴리오의 5개 프로젝트를 기반으로 면접관 관점에서 날카로운 질문을 던지고 답변을 코칭
4. **타깃 기업 맞춤형 이력서 최적화**:
   * 지원하고자 하는 특정 기업(빅테크, 시리즈 B/C 스타트업 등)의 JD(채용 공고)에 맞춘 키워드 튜닝
