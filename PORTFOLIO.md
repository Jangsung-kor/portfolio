# 장성환 | 포트폴리오 (최신 수정본 원본)

## 메인 개요 및 핵심 역량

> 💡 복잡한 인프라 도메인을 안정적인 소프트웨어로 풀어내는 6년 차 풀스택 개발자 장성환입니다.
B2B 데이터센터 인프라 관리(DCIM) 솔루션의 핵심 모듈(성능 분석, 계통 토폴로지, 작업 관리, 품질 안정화)을 화면/ERD 설계부터 백엔드 API, 대규모 데이터 시각화까지 엔드투엔드로 개발해 왔습니다. 안정적인 엔터프라이즈 레거시 환경(Vue 2, Spring, Oracle)과 최신 모던 웹 스택(Vue 3, Vite, Pinia, PWA, Firebase)을 두루 다룹니다.


## 핵심 역량 (Core Competencies)


* 풀스택 시스템 개발: Vue.js 2/3 프론트엔드와 Java/Spring 백엔드, Oracle DB 간의 전체 데이터 흐름을 고려한 컴포넌트 모듈화 및 RESTful API 단독 설계·구현
* 대규모 인프라 데이터 시각화: Highcharts, D3.js, Kakao Maps SDK, SVG/Canvas를 활용하여 시계열 성능 지표, 물리 계통 토폴로지, 공간 GPS 데이터를 웹 브라우저에서 안정적으로 시각화
* 도메인 중심의 실무 문제 해결: 데이터 정합성 리스크 관리, 점검 작업 중 대량 오알람 차단, 대량 데이터 일괄 편집 위저드 등 현장 엔지니어의 작업 동선을 실질적으로 개선하는 소프트웨어 설계
* 품질 표준화 및 안정화: 공�� 조달 필수 요건인 GS 인증 1등급 획득을 주도하며 레거시 시스템의 결함 100여 건 전수 조치 및 공통 예외 처리 체계 정비
* 모던 프론트엔드 역량: Vue 3 Composition API, Vite, Pinia, Firebase NoSQL, PWA 오프라인 캐싱 기술을 활용한 자전거 스탬프 웹 서비스(cycling-stamp.web.app) 단독 기획·개발 및 운영

---


## 프로젝트 상세 (Project Details)





---
# 프로젝트 세부 내용



---
# [프로젝트 01] DCIM 3D 상면 고도화 사업 (차트 분석 & DIMS 자동화)


## 1. 개요 (Overview)

* 기간: 2026.09 ~ 2026.10 (전체 상면 고도화 사업: 2026.07 ~ 2026.10)
* 담당 역할: PL 및 풀스택 개발 - KT 담당자 주간 정기 협의, 화면/ERD 설계, 프론트/백엔드 풀스택 구현
* 기술 스택: Vue.js 2.x, Element UI, Highcharts 11.x, vue-highcharts, SCSS / Java, Spring Framework, MyBatis, Oracle DB, Java Async Task
* 주요 성과: [차트 분석 메뉴] 2-Way 일괄 편집 위저드 구축 / [DIMS 자동화] KT 9개 DC 3만 대 랙 수용을 위한 장비 등록 및 위치 매핑 비동기 파이프라인 개발 / KT 주간 협의를 통한 실무 UI 개선

## 2. 개발 배경 및 목적 (Situation & Task)

KT 9개 데이터센터(DC)의 전산실 인프라를 DCIM 3D 상면 메뉴에 배치하고 관제하는 고도화 사업이 추진되었습니다. KT 자체 자산 관리 시스템(DIMS)에 등록된 랙 장비만 약 3만여 대에 달하여, 이를 사람이 수작업으로 등록하고 위치에 매핑하는 것은 불가능한 상황이었습니다. 또한 3D 상면 뷰와 연계하여 여러 장비의 CPU, 메모리, 온도, 전력 등 다차원 시계열 지표를 교차 분석할 수 있는 고성능 차트 메뉴가 필수적으로 요구되었습니다.

* DIMS 데이터 자동화 파이프라인: 층별 버튼 클릭 한 번으로 대량의 랙 장비를 자동 등록하고 서버실 위치까지 일괄 매핑하는 비동기 배치 로직 구현
* 다차원 차트 분석 시스템: 수십 대의 장비와 수십 개 지표를 한 번에 매핑하는 2-Way 일괄 편집 위저드 및 템플릿 영속화 모듈 구축
* 고객사 주간 협의: KT 담당자와 매주 정기 회의를 진행하며 현장 피드백을 수렴하여 UI 완성도 확보

## 3. 주요 구현 내용 (Action)


### 1) DIMS 연동 및 장비-위치 자동 매핑 파이프라인 (백엔드 비동기 처리)

KT 9개 DC 내 약 3만 대의 랙 장비를 상면에 배치하기 위해 [장비 등록 ➔ DIMS 데이터 매핑 ➔ 장비-위치 매핑] 과정을 자동화했습니다.
• 사전 세팅된 위치 계층(dcim_location: DC > 층 > 서버실)을 기반으로 각 층별 'DIMS 자동화' 트리거 기능 개발
• 운영자가 특정 층(예: 경북 DC > 1층)에서 버튼을 클릭하면, 해당 층의 수백 대 랙 장비를 DIMS에서 조회하여 DCIM 장비로 등록하고 하위 서버실(서버실 A 100대, 서버실 B 150대 등)에 자동으로 매핑
• 수백~수천 대 장비의 일괄 등록 시 웹 요청 타임아웃 및 스레드 블로킹을 방지하기 위해 Java Task 기반의 비동기 처리 로직을 적용하여 백그라운드에서 안전하게 트랜잭션을 수행하도록 설계함.

DIMS 자동화 버튼.png

DIMS 자동화 진행중.png

DIMS 자동화 매핑 결과.png

▲ [그림 1-1] DIMS 연동 자동화 인터페이스 및 장비-서버실 위치 매핑 화면
각 층별 버튼 클릭으로 DIMS 자산 데이터를 조회하여 DCIM 장비 등록부터 하위 서버실 위치 매핑까지 Java 비동기 Task로 일괄 처리하는 화면입니다.

```Java
taskExecutor.execute(new Runnable()
{
    @Override
    public void run()
    {
        try
        {
            // 1. 비동기 스레드로 세션 및 인증 컨텍스트(ThreadLocal) 안전 전파
            HttpServletRequest dummyRequest = createDummyRequest(clientIp, authentication);
            RequestContextHolder.setRequestAttributes(new ServletRequestAttributes(dummyRequest));

            if (authentication != null)
            {
                SecurityContext securityContext = SecurityContextHolder.createEmptyContext();
                securityContext.setAuthentication(authentication);
                SecurityContextHolder.setContext(securityContext);
            }

            // 2. 대량 랙 장비 등록 및 서버실 위치 매핑 배치 수행
            autoDimsAssetReg(dcCode, flrNm);
        }
        catch (Exception e)
        {
            LOG.error("DIMS auto registration batch error: " + e.getMessage(), e);
        }
        finally
        {
            // 3. 스레드 풀 재사용 시 메모리 누수 및 인증 오염 방지를 위해 컨텍스트 초기화
            RequestContextHolder.resetRequestAttributes();
            SecurityContextHolder.clearContext();
        }
    }
});
```

💡 핵심 포인트: 비동기 스레드 분기 시 발생하는 ThreadLocal 세션 유실을 방지하기 위해 RequestAttributes와 SecurityContext를 명시적으로 주입하고, 작업 완료 후 finally 블록에서 컨텍스트를 클리어하여 스레드 풀 재사용 시의 메모리 누수와 인증 오염을 원천 차단했습니다.


### 2) 2-Way 일괄 구성(Batch Edit) 위저드 구현

수동 설정 작업을 줄이기 위해 분석 목적에 따라 진입 방식을 이원화했습니다.
• 장비 기준 모드 (OBJ_FIRST): 특정 랙이나 장비 목록을 먼저 선택하고 공통 지표(CPU/MEM 등)를 한 번에 매핑
• 성능 자원 기준 모드 (RSC_FIRST): 특정 지표(온도, 전력 피크 등)를 먼저 선택하고 비교할 대상 장비들을 매핑
2단계 위저드(대상 선택 ➔ 슬롯 배치)와 임시 보관함(WizardBasketTable)을 두어 복잡한 N:M 매핑 과정을 단순화했습니다.

차트 일괄 편집_1단계.png

차트 일괄 편집_2단계.png

▲ [그림 1-2] 2-Way 일괄 편집 캔버스 (장비 기준 vs 자원 기준 선택 인터페이스)
장비 또는 성능 지표 중 분석 목적에 맞는 진입 방식을 선택하고, N:M 매핑 대상을 장바구니 형태로 담아 차트 슬롯에 일괄 배치하는 2단계 위저드 화면입니다.


### 3) 대용량 이기종 데이터(OBJ-DIMS-ERP) 매핑 및 4단계 프론트엔드 최적화

• 배경 및 부하: DCIM 장비(OBJ), KT 자산(DIMS), 전사 자원(ERP) 3개 시스템을 LEFT JOIN으로 결합하여 매핑 여부에 따라 [OBJ, DIMS, ERP]가 복합 산출되는 구조로 인해 3만 건 조회 시 브라우저 및 쿼리 부하 발생.
• 4단계 엔지니어링 최적화:
  1. 복합 조인 쿼리 튜닝: 불필요 서브쿼리 제거 및 인덱스 정비로 DB 응답 속도 최적화
  2. 트리 가상 스크롤 전격 도입: el-tree의 3만 개 전체 DOM 렌더링 프리징을 극복하기 위해 el-tree-virtual-scroll로 교체하여 지연 체감 0초 달성
  3. 트리 레벨 페이���: 100대 이상 시 최초 100대만 노출하고 '...more(남은 대수)' 클릭 시 100개씩 점진 로딩
  4. 전역 DC 필터 선행 배치: 9개 DC 선택 필터로 최초 조회 범위 사전 제한
• 시계열 다운샘플링 정책: Highcharts 과부하 방지를 위해 조회 기간별 집계 간격 차등화(3일 이하: 5분 / ~19일: 30분 / ~90일: 2시간 / 90일 초과: 1일)

차트 뷰어ㅏ.png

▲ [그림 1-3] 차트 패널 화면 및 마우스 오버레이 통계 제어 툴바
상위 컨테이너와 위젯을 분리하여 다수 차트 렌더링 시 브라우저 부하를 줄였으며, 마우스 Hover 시 평균/최대/최소 통계값을 실시간으로 토글할 수 있는 오버레이 툴바입니다.


### 4) 컴포넌트 모듈화 및 방어적 예외 코드(ErrorCode) 체계

• 유지보수성과 재사용성을 위한 컴포넌트 분리: 차트 화면을 단일 거대 컴포넌트가 아닌 15종의 세부 컴포넌트(툴바, 템플릿 트리, 위젯, 차트 바디 등)로 모듈화하여, 타 개발자의 유지보수 용이성과 Vue 컴포넌트 재사용성을 확보함.
• 표준 예외 코드(ErrorCode) 기반 안전한 비동기 자동화: 3만 대 장비 등록 중 예기치 못한 데이터 누락/형식 불일치 발생 시 시스템 중단 없이 원인을 추적할 수 있도록 사전 설계된 표준 예외 코드 체계 수립.


## 4. 결과 및 성과 (Result)

* 대규모 수작업 공수 제거: 약 3만 대의 랙 장비를 사람이 직접 등록하고 매핑해야 했던 반복 작업을 자동화하여 데이터 구축 기간을 수개월에서 수일로 단축
* 고속 풀스택 딜리버리: 사업 마감 일정에 맞춰 2개월 만에 차트 프론트엔드 컴포넌트 15종 및 백엔드 REST API를 완성
* 고객사 요구사항 적기 대응: KT 데이터센터 담당자와 매주 정기 회의를 진행하며 현장 피드백을 실시간으로 수렴 및 반영하여 고객 만족도 확보

## 5. 회고 (Lesson Learned)

* 대용량 데이터 시각화의 본질은 '덜어내는 기술': 3만 건의 이기종(OBJ-DIMS-ERP) 데이터를 브라우저에 그대로 밀어 넣지 않고 쿼리 튜닝부터 가상 스크롤, 트리 레벨 점진 로딩, 시계열 다운샘플링까지 단계별로 데이터를 경량화해 나가는 실전 엔지니어링을 체득함.
* 엔지니어링 소통의 힘: 고객사의 요구를 무조건 수용하는 대신, 아키텍처 안정성이나 성능상 위험 요소는 '기술적으로 왜 어려운지'를 투명하게 설명하고 대안을 제시했을 때 오히려 고객사의 깊은 신뢰와 협조를 얻을 수 있음을 배움.
* 짧은 납기 속 트레이드오프: 2개월 동안 대용량 성능 안정화와 비동기 배치에 집중하느라 UI/UX 디자인 협업 요청을 더 일찍 당기지 못했던 아쉬움이 남아, 기획 초기 단계부터 디자인 리소스를 조기 요청하는 일정 안배의 중요성을 깨달음.




---
# [프로젝트 02] DCIM 전산실 작업 관리 및 다채널 스케줄러 개발


## 1. 개요 (Overview)

* 기간: 2026.07 ~ 2026.09
* 담당 역할: 풀스택 개발 - 전산실 운영 요구사항 분석, 화면 동선 재설계, 프론트/백엔드 구현 및 메시징 연동
* 기술 스택: Vue.js 2.x, Element UI, SCSS / Java, Spring Framework, MyBatis, Oracle DB, SMS/Slack/Mail API 연동, AI 페어 프로그래밍(엣지 케이스 검증)

## 2. 배경 및 목적 (Situation & Task)

DCIM은 모체 NMS 솔루션을 포크(fork)하여 구축된 시스템으로, 데이터센터 현장에서 전력·공조 장비 점검 시 상위 장비(UPS/PDU) 점검에 따라 하위에 연결된 수십~수백 대의 랙과 서버에서 통신 단절성 오탐 알람(False-Positive)이 폭증하는 문제가 빈번했습니다. 이로 인해 관제 화면이 마비되고 실제 장애를 놓칠 위험이 컸으며, 이에 작업 기간 동안 대상 장비의 모니터링을 단계별로 일시 정지시키고 전·후 시점에 자동으로 다채널 알람을 발송하는 관리 체계를 구축했습니다.

* 작업 기간 동안 특정 장비의 모니터링 프로세스를 단계별로 제어하는 로직 수립
* 어느 화면에서나 작업을 확인하고 등록할 수 있는 전역 풀 팝업 접근성 확보
* 시작 전, 시작 시, 종료 시점에 맞춰 문자, 메일, 슬랙으로 발송되는 스케줄러 구현

## 3. 주요 구현 내용 (Action)


### 1) 모니터링 프로세스 3단계 계층 제어

프로세스 간 상하 관계(성능 수집 ➔ 이벤트 발생 ➔ 알람 발송)를 정의하여 일시 정지 옵션을 세분화했습니다.
• 수집 중지: 하위 이벤트와 알람까지 모두 멈추는 완전 정지 모드
• 알람만 중지: 외부 알람 발송만 차단하고, 백그라운드 성능 수집과 내부 이벤트 로그는 정상 기록하여 사후 장애 분석용 데이터를 보존하는 모드
이를 통해 불필요한 알람 오발송을 막으면서도 작업 중 성능 지표 로그는 계속 남길 수 있도록 유연성을 확보했습니다.


### 2) 글로�� 풀 팝업(Full Popup) 동선 개선

기존에 작업 관리를 하려면 별도 메뉴로 페이지를 이동해야 했던 방식을 개선하여, DCIM 상단 헤더 프레임에 작업관리 아이콘을 배치했습니다. 사용자가 상면 3D 맵이나 계통 맵 등 어떤 화면에서 작업하더라도 컨텍스트를 유지한 채 즉시 풀 팝업으로 작업 일정을 조회하고 등록할 수 있도록 접근성을 높였습니다.

작업 관리 버튼 헤더 프레임.png

작업관리 풀 팝업.png

▲ [그림 3-1] 글로벌 헤더 프레임 연동 작업관리 풀 팝업 (Full Popup)
상면 맵, 계통 맵 등 어떤 화면을 보고 있더라도 컨텍스트를 유지한 채 상단 아이콘 클릭으로 즉시 작업 일정을 확인하고 등록할 수 있는 전역 팝업 인터페이스입니다.


### 3) 2단계 마법사 및 다채널 알람 스케줄러 (AI 페어 프로그래밍)

• 1단계: 기본 정보(기간, 작업 구분, 제어 옵션) 및 대상 장비 선택
• 2단계: 알람 발송 수단(SMS, 이메일, 슬랙)과 발송 시점(시작 N분 전, 시작 시, 종료 시) 설정
• 복잡한 반복 주기 및 Range 스캔 엣지 케이스 교차 검증: 일/주/월/말일 등 복잡한 반복 스케줄링 시 발생할 수 있는 윤달, 월말 일자 누락 및 정시 틱 지연 시의 누락 방지 로직을 빈틈없이 설계하기 위해 대화형 AI를 페어 프로그래밍 파트너로 활용하여 수십 가지 엣지 케이스 시나리오를 신속하게 도출하고 비즈니스 규칙의 무결성을 확보함.

```Java
// [작업 관리] 1. 주기별(일/주/월) 반복 작업 자동 분할 생성 및 월말 예외 처리
private List<WorkMgmt> convertWorkMgmtData(WorkMgmt workMgmt, DcimWorkScheduleVO schedule) throws Exception {
    List<WorkMgmt> resultList = new ArrayList<>();
    String scheduleType = workMgmt.getScheduleType();

    Date initialStart = schedule.getStartDatetime();
    Date initialEnd = schedule.getEndDatetime();
    Date endScheduleDate = schedule.getEndScheduleDate();

    if ("O".equals(scheduleType)) { // 단건 작업
        resultList.add(createWorkMgmtClone(workMgmt, initialStart, initialEnd));
        return resultList;
    }

    Calendar startCal = Calendar.getInstance();
    startCal.setTime(initialStart);
    Calendar endCal = Calendar.getInstance();
    endCal.setTime(initialEnd);

    // 마지노선(endScheduleDate)까지 주기별 루프를 돌며 개별 작업 인스턴스 분할 생성
    while (startCal.getTime().compareTo(endScheduleDate) <= 0) {
        Date currentStart = startCal.getTime();
        Date currentEnd = endCal.getTime();
        if (currentEnd.compareTo(endScheduleDate) > 0) {
            currentEnd = endScheduleDate;
        }
        resultList.add(createWorkMgmtClone(workMgmt, currentStart, currentEnd));

        if ("D".equals(scheduleType)) {
            startCal.add(Calendar.DATE, 1);
            endCal.add(Calendar.DATE, 1);
        } else if ("W".equals(scheduleType)) {
            startCal.add(Calendar.DATE, 7);
            endCal.add(Calendar.DATE, 7);
        } else if ("M".equals(scheduleType)) {
            startCal.add(Calendar.MONTH, 1);
            endCal.add(Calendar.MONTH, 1);
            // 31일 등 말일 등록 시 2월/4월 등의 일자 누락 방지를 위한 월말 일자 보정
            int origStartDay = (schedule.getStartDate() != null) ? schedule.getStartDate() : startCal.get(Calendar.DATE);
            startCal.set(Calendar.DATE, Math.min(origStartDay, startCal.getActualMaximum(Calendar.DAY_OF_MONTH)));

            int origEndDay = (schedule.getEndDate() != null) ? schedule.getEndDate() : endCal.get(Calendar.DATE);
            endCal.set(Calendar.DATE, Math.min(origEndDay, endCal.getActualMaximum(Calendar.DAY_OF_MONTH)));
        }
    }
    return resultList;
}
```

```Java
// [작업 관리] 2. 매 분 백그라운드 알람 발송 트리거 태스크 (누락 방지 Range 스캔)
@Component
public class DcimWorkMgmtPushAlarmTask implements TaskIF {
    @Override
    public void execute() {
        try {
            if (!isWorkMgmtEnabled()) return; // 작업 관리 모듈 활성화 확인

            Calendar now = Calendar.getInstance();
            truncateMinute(now); // 현재 시간 분 단위 절사 (예: 14:30:00)
            Calendar nextMinute = (Calendar) now.clone();
            nextMinute.add(Calendar.MINUTE, 1); // 다음 1분 (예: 14:31:00)

            // 정시 단일 매칭 대신 시간 범위([now, nextMinute)) 스캔으로 태스크 지연 시 알람 누락 방지
            DcimWorkMgmtAlarmExample example = new DcimWorkMgmtAlarmExample();
            example.createCriteria()
                .andAlarmDatetimeGreaterThanOrEqualTo(now.getTime())
                .andAlarmDatetimeLessThan(nextMinute.getTime());

            List<DcimWorkMgmtAlarm> alarmList = alarmMapper.selectByExample(example);
            for (DcimWorkMgmtAlarm alarm : alarmList) {
                PushNotificationParamVO pushParam = new PushNotificationParamVO();
                pushParam.setInfoType(PushNotificationDefine.INFO_TYPE_DCIM_ALARM_WORK);
                pushParam.setData(buildAlarmPayload(alarm));

                // Spring ApplicationContext 이벤트 발행 -> SMS/Mail/Slack 디스패치
                eventPublisher.publishEvent(new PushNotificationCallEvent(this, pushParam));
            }
        } catch (Exception e) {
            LOG.error("[DcimWorkMgmtPushAlarmTask] 알람 스케줄러 처리 실패", e);
        }
    }
}
```


### 4) '연관 장비 탐색' 기반 선택적 추가 UX 설계 (의사결정)

• 쟁점: 상위 장비(PDU)를 선택하면 연결된 하위 장비(수십 개의 랙, 서버)를 무조건 자동 일괄 등록하자는 의견이 있었음.
• 문제점: 특정 랙 1~2개만 부분 점검하려 할 때 오히려 수십 개의 하위 장비를 일일이 체크 해제해야 하는 불편함이 크고, 원치 않는 장비의 모니터링까지 중단될 위험이 있었음.
• 해결책: 무조건적인 자동 등록 대신 '연결 랙', '연결 PDU', '계통', '상면' 등 연관 분류별 목록을 조회해 주고 필요한 장비만 클릭하여 선택적으로 추가하는 방식으로 설계하여 운영 안정성을 확보함.

작업관리_연관 장비 등록.png

작업관리_스케줄러 등록.png

▲ [그림 3-2] 연관 분류 기반 작업 대상 장비 선택 및 알람 스케줄러 설정 위저드
무조건적인 일괄 등록 대신 연결 랙/PDU/계통 등 연관 분류를 조회하고 필요한 장비만 선택적으로 추가하여 운영 안정성을 확보한 화면입니다.


## 4. 결과 및 성과 (Result)

* 전산실 점검 작업 중 발생하던 수백 건의 불필요한 오탐 알람을 차단하여 관제 피로도 해소
* '알람만 중지' 옵션을 통해 작업 중에도 성능 수집 로그를 유지하여 사후 분석 데이터의 연속성 확보

## 5. 회고 (Lesson Learned)

* 기획-개발 일정 불균형과 멀티 프로젝트 병행의 한계: 상세 기획 문서화(PPTX)에 1개월이 소요되어 후반 개발 일정이 촉박했고, 동시 진행되던 '3D 상면 고도화 사업'의 개발 PL로서 매주 KT 미팅 참석과 주말 개발을 병행하며 높은 컨텍스트 스위칭 비용을 경험함.
* AI 페어 프로그래밍의 실무 적용과 스코프 관리의 교훈: 대화형 AI를 통해 복합 엣지 케이스를 빠르게 도출하고 구현 속도를 끌어올렸으나, 촉박한 사업 마감 일정 속에서 단위 테스트 자동화 체계를 조기에 완벽히 구축하지 못했던 아쉬움이 남음. 생산성 도구의 레버리지와 함께 릴리즈 스코프의 단계적 분할 및 조기 테스트 자동화가 선행되어야 함을 배움.




---
# [프로젝트 03] DCIM 인프라 장비 물리 계통 시각화 개발 및 회고


## 1. 개요 (Overview)

* 기간: 2026.03 ~ 2026.05
* 담당 역할: 프론트엔드 및 시각화 개발 - D3.js 노드-링크 인터랙션 및 화면 렌더링 구현, 백엔드 수집 엔진 연동 가능성 검토
* 기술 스택: Vue.js 2.x, D3.js, SVG/Canvas, Element UI / Spring Framework, Oracle DB

## 2. 개발 배경 및 목적 (Situation & Task)

• 모체 NMS 토폴로지와 FMS(설비) 계통의 괴리: 기존 계통 맵은 모체 솔루션의 NMS(네트워크 망) 토폴로지를 그대로 가져온 것으로, 전력·공조(UPS ➔ PDU ➔ 랙 ➔ 서버) 설비 계통을 표현하기에 구조적 한계가 컸고, 초기 엔지니어 수작업 구축 후 고객사의 자체 유지보수가 거의 불가능했음.
• 기술 전환 로드맵 (qunee ➔ D3.js): 레퍼런스가 없고 코드가 복잡한 외산 qunee 라이브러리를 극복하기 위해 오픈소스 생태계가 풍부한 D3.js를 도입하여, 설정 메뉴의 '연결관계'를 신규 구축하고 향후 메인 계통 맵까지 단계적으로 전환하기로 결정함.

* D3.js를 사용해 장비 노드를 드래그 앤 드롭으로 배치하고 포트 간 연결선을 그리는 화면 구현
* 장비 간 전원 공급 및 상하위 물리 연결 데이터를 구조화하여 관리할 수 있는 계통 데이터 모델 수립

## 3. 주요 구현 내용 (Action)

• 기술적 의사결정 (자동화의 유혹과 현실적 제약): 초기 경영진의 '장비 배치 시 하위 장비 자동 탐색/일괄 렌더링' 요구에 대해, 현장 전산실의 이중화/바이패스 등 물리적 변수를 분석하여 무리한 자동화가 수집 엔진 데이터를 오염시킬 수 있음을 설득함. 이에 수동 매핑 후 [저장 시 계통 맵 반영] 옵션을 거치는 안정성 중심 구조 확립.
• D3.js 기반 동적 토폴로지 캔버스 렌더링: SVG 기반으로 장비 노드 드래그 앤 드롭 및 포트 간 Bezier 곡선 동적 계산 연결, 대규모 노드 확장을 고려한 Zoom & Pan 및 좌표계 변환 구현.

연결관계 맵 화면.png

▲ [그림 3-1] D3.js 기반 인프라 장비 계통 토폴로지 시각화 화면
UPS부터 PDU, 랙, 서버로 이어지는 물리적 전원/네트워크 연결관계를 SVG Bezier 곡선과 드래그 앤 드롭 노드로 구현한 캔버스 화면입니다.


## 4. 실서비스 연동을 멈춘 이유 (회고)

화면상에서 노드를 띄우고 선을 잇는 기능 자체는 구현을 마쳤으나, 최종 단계에서 실제 수집 엔진과의 연동을 진행하지 않고 화면 뷰 수준으로 제한했습니다. 이유는 다음과 같습니다.

1. 실서버 데이터 정합성 훼손 위험: 현장 관리자가 화면에서 마우스로 연결선을 잘못 잇거나 삭제할 경우, 24시간 가동 중인 백엔드 수집 엔진의 계통 데이터가 꼬일 위험이 컸음. 시스템 안정성을 위해 실서버 데이터와의 자동 동기화는 보류하기로 결정함.
2. 실무 편의성보다 구현 난이도에 집중했던 한계: D3.js의 캔버스 조작 로직을 바닥부터 구현하는 데 많은 공수가 들어갔으나, 정작 현장 관리자가 필요로 했던 것은 '자유롭게 선을 그리는 기능'보다 '수집된 데이터를 바탕으로 계통을 빠르고 편하게 확인하는 것'이었음을 확인함.


## 5. 배운 점 (Lesson Learned)

* 데이터 모델링(ERD) 조율의 비용과 사전 합의의 중요성: 인프라 연결관계를 추상화하는 ER 설계에 많은 시간을 쏟았으나, 리드급과의 데이터 계층 구조 관점 차이로 잦은 스키마 수정과 공수 소모를 겪으며 초기 사전 합의의 중요성을 배움.
* '포기하지 않는 끈기'의 역설: GS인증에서 얻은 끈기만으로 접근했으나, 불확실성이 큰 R&D 프로젝트에서는 무작정 끈기보다 현대적 개발 생산성 도구 도입과 빠른 프로토타이핑이 필수적임을 깨달음.
* 기능의 화려함보다 데이터 정합성이 최우선: 화면에서 아무리 매끄러운 인터랙션이 동작하더라도 실제 수집 데이터 무결성을 위협한다면 좋은 소프트웨어가 될 수 없음을 배웠으며, 이는 이후 [차트 분석]과 [작업 관리]에서 안전한 위저드 방식을 설계하는 든든한 밑거름이 됨.




---
# [프로젝트 04] DCIM GS 인증 획득 및 SW 품질 안정화


## 1. 개요 (Overview)

* 기간: 2025.04 ~ 2025.06
* 담당 역할: 개발 전담 리드 - 신규 DB 구축 환경 검증, 인프라 엔지니어 협업, 제품 전 모듈 결함 100여 건 전수 분석 및 조치, 2차 재심사 최종 통과
* 기술 스택: Java, Spring Framework, MyBatis, Oracle DB, JavaScript, Vue.js 2.x

## 2. 배경 및 목적 (Situation & Task)

• 신설 조직 환경과 모체 솔루션 포팅 결함의 누적: 2024년 각 팀의 대리급 개발자들이 모여 신설된 초기 팀 환경에서, 사내 모체 NMS 관제 솔루션의 방대한 코드베이스를 DCIM 전산실 환경으로 분기(fork)·포팅하며 전담 QA 부재와 도메인 차이로 인한 DDL 스키마 불일치, 외래키 제약조건 오류, 모체 종속 로직 등 잠재 결함이 대량 누적된 상태였음.
• 공공 조달 필수 관문인 GS 인증 1등급 추진: 초기 현장 납품 결함을 해소하고 공공 조달 등록 자격을 획득하기 위해 소프트웨어 품질인증(GS) 1등급 획득이 회사의 최우선 과제로 지정됨. 대리 승진 후 첫 책임 프로젝트로서 제품 전반의 결함 해결과 인증 심사 통과를 총괄함.

* 신규 DB 인스턴스 구축 및 기준정보, DDL 스크립트 정합성 검증
* 장비 관리, 상면, 계통, 설정, 권한 관리 등 제품 내 모든 화면과 기능에 대한 전수 결함 조치
* 1차 심사 불합격 이후 지적된 잔여 결함을 보완하여 2차 재심사 통과

## 3. 주요 수행 내용 (Action)

• 신규 데이터베이스 정합성 검증: DDL 스키마 불일치, 외래키(FK) 제약조건 오류, 공통 코드 기준정보 누락을 추적하여 초기 데이터 정합성을 확보함.
• 제품 전반 결함 100여 건 전수 조치: 후배 엔지니어 1명과 함께 수동 트랜잭션 rollback 누락 방어(롤백 보장 트랜잭션 템플릿 도입), 모체 솔루션 종속 참조로 인한 NPE 해결(방어 분기 및 Null-safe 로직), UI 유효성 검증 누락 및 비동기 렌더링 예외 처리 전수 해결.
• 1차 심사 불합격 극복 및 2차 재심사 전 항목 '적합' 획득: 심사 기관 체크리스트를 정밀 분석하고 원인 분석부터 코드 수정, 자체 회귀 테스트까지 완수하여 2차 재심사 최종 통과.

GS 인증서.png

▲ [그림 4-1] 소프트웨어 품질인증(GS) 1등급 인증서
전 모듈 100여 건의 결함 조치 및 데이터베이스 정합성 검증을 거쳐 2차 재심사에서 전 항목 적합 판정을 받고 공공 조달 요건을 확보한 인증서 사본입니다.


## 4. 결과 및 성과 (Result)

* 최종 GS 인증 획득을 완료하여 공공 조달 등록 자격 요건 충족
* 제품 전반의 레거시 코드와 화면 동작 구조를 파악하게 되어, 이후 DCIM의 신규 기능 개발 및 PL 역할을 안정적으로 수행할 수 있는 기술적 기반 마련
* 일회성 결함 수정을 넘어 제품 전반의 공통 예외 처리와 유효성 검증 규칙을 정비하여 이후 결함 발생률 완화

## 5. 회고 (Lesson Learned)

* 야전에서 배운 엔지니어링 끈기와 책임감: 대리 승진 후 단독 책임을 맡은 첫 프로젝트로서, 1차 불합격 위기 속에서도 후배와 끝까지 포기하지 않고 원인을 추적하여 2차 전 항목 적합 판정을 이끌어냄. '포기하지 않고 집요하게 파고들면 반드시 해결할 수 있다'는 엔지니어로서의 강한 자신감과 끈기를 체득함.
* 사후 유지보수 비용에 대한 자각: 아키텍처와 예외 처리가 초기에 정교하게 설계되지 않은 소프트웨어의 막대한 사후 디버깅 비용을 뼈저리게 체감하고, 이후 프로젝트에서 데이터 모델링과 방어적 프로그래밍에 각별히 공을 들이는 습관을 확립함.




---
# [프로젝트 05] 국토종주 자전거 스탬프 PWA 서비스 개발


## 1. 개요 (Overview)

* 기간: 2026.10 ~ 현재 (실 서비스 배포 및 운영 중)
* 서비스 링크: https://cycling-stamp.web.app
* 담당 역할: 기획, UI 설계, 프론트엔드 및 클라우드 배포 1인 개발 (개인 사이드 프로젝트)
* 기술 스택: Vue.js 3 (Composition API), Vite, Pinia, Firebase (Auth, Firestore, Hosting), PWA (Service Worker), Kakao Maps SDK, Vant UI

## 2. 개발 배경 및 목적 (Situation & Task)

기존 국토종주 공공 앱('자전거 행복나눔')은 전체 코스를 한눈에 파악하기 어렵고, 부분 지도로만 제공되어 장거리 주행 계획을 세우는 데 불편함이 있었습니다. 또한 앱스토어 설치를 강제하고 네트워크가 불안정한 강변/산간 구간에서 오프라인 대응이 미흡한 점을 개선하고자 직접 사용할 목적으로 개발을 시작했습니다.

* 앱스토어 설치 없이 링크나 QR 스캔으로 바로 홈 화면에 추가할 수 있는 PWA 구축
* 전국 85개 인증센터 및 13개 종주 코스 경로를 한눈에 볼 수 있는 인터랙티브 지도 뷰 제공
* GPS 기반 스탬프 자동 획득 및 다회차(N회 방문) 주행 이력 기록 기능 구현

## 3. 주요 구현 내용 (Action)


### 1) 오프라인 벡터 SVG 도장 렌더링 엔진 (stampGenerator.js)

통신 음영 지역에서도 도장 이미지가 깨지지 않도록 외부 이미지 서버 의존성을 완전히 제거했습니다. 85개 인증센터 고유 심볼을 브라우저에서 직접 그리는 경량 벡터 SVG 생성 함수를 작성하여, 네트워크 요청 없이 오프라인에서도 즉시 렌더링되도록 구현했습니다. 사용자가 선택한 테마 색상(Ash Red, Mint, Blue)의 hex 코드를 파라미터로 주입하여 실시간 색상 변경이 가능하도록 설계했습니다.

```JavaScript
// [stampGenerator.js] 오프라인 브라우저 연산 기반 고해상도 벡터 인주 도장 생성기
export const generateStampSvg = (center, isAcquired, inkColor = '#1E5E4E') => {
  const shortName = center.name.replace(/인증센터|자전거길/g, '').trim().substring(0, 4);
  const meta = centerCustomIcons[center.id];
  const symbol = meta ? meta.icon : '🚴';

  // SVG 문자열 조립: 테마 컬러(inkColor) 동적 주입 및 이중 인주 테두리 렌더링
  const svg = `
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 120 120" width="100%" height="100%">
      <circle cx="60" cy="60" r="54" fill="none" stroke="${inkColor}" stroke-width="4" stroke-dasharray="${isAcquired ? 'none' : '4 3'}"/>
      <circle cx="60" cy="60" r="48" fill="none" stroke="${inkColor}" stroke-width="1.5" opacity="0.8"/>
      <text x="60" y="55" font-size="28" text-anchor="middle" dominant-baseline="central">${symbol}</text>
      <text x="60" y="88" font-size="12" font-weight="bold" fill="${inkColor}" text-anchor="middle">${shortName}</text>
    </svg>`;
  return `data:image/svg+xml;utf8,${encodeURIComponent(svg)}`;
};
```

> 💡 💡 핵심 포인트: 85개 인증센터 심볼을 브라우저 런타임에서 즉시 조립하는 순수 SVG 제너레이터 함수를 구축하여 외부 이미지 네트워크 요청 0건 및 번들 크기 최소화를 달성했습니다.

▲ [그림 5-1] 오프라인 벡터 SVG 동적 인주 도장 렌더링 화면
네트워크 음영 지역에서도 외부 이미지 서버 없이 브라우저 연산으로 즉시 렌더링되는 경량 벡터 SVG 도장 및 테마 동기화 결과물입니다.


### 2) GPS 위치 측위 및 24시간 쿨다운 로직

모바일 브라우저 Geolocation API의 수평 오차(20~50m)를 감안하여, 현장 필드 테스트를 거쳐 정상 인증과 오차를 절충한 100m 반경을 적용했습니다. 거리 계산에는 하버사인(Haversine) 공식을 사용했습니다. 동일 인증센터에서 마지막 인증 성공 후 24시간 이내에는 재인증을 차단하는 쿨다운 로직을 Pinia 스토어와 Firestore 보안 규칙에 탑재하여 중복/부정 인증을 방지했습니다.

```JavaScript
// [stores/stamp.js] 24시간 쿨다운 안티-어뷰징 및 하위 호환 정규화 로직 (Pinia)
const COOLDOWN_MS = 24 * 60 * 60 * 1000; // 24시간 쿨다운 (밀리초)

// 하위 호환성을 위한 스탬프 데이터 정규화 (N회차 방문 스키마 자동 보정)
const normalizeStamp = (s) => ({
  ...s,
  visitCount: s.visitCount || (s.history ? s.history.length : 1),
  history: s.history && s.history.length > 0 ? s.history : [{ round: 1, acquiredAt: s.acquiredAt }]
});

// 스탬프 획득 및 24시간 쿨다운 기반 다회차(xN) 인증 처리
async function addStamp(center) {
  const existing = this.acquiredStamps.find(s => s.id === center.id);
  const nowMs = Date.now();

  if (existing) {
    const lastAcquiredAt = existing.history?.slice(-1)[0]?.acquiredAt || existing.acquiredAt;
    const diffMs = nowMs - new Date(lastAcquiredAt).getTime();

    // 24시간 이내 재인증 차단 (쿨다운 규칙)
    if (diffMs < COOLDOWN_MS) {
      const remainingHours = Math.max(1, Math.ceil((COOLDOWN_MS - diffMs) / (1000 * 60 * 60)));
      return { success: false, code: 'COOLDOWN', remainingHours };
    }

    // 24시간 경과: N회차 스탬프 획득 성공 (x2, x3...)
    existing.visitCount = (existing.visitCount || 1) + 1;
    existing.history.push({ round: existing.visitCount, acquiredAt: new Date().toISOString() });
    await this.saveStampsToFirestore();
    return { success: true, visitCount: existing.visitCount };
  }
}
```


### 3) 하위 호환성을 고려한 데이터 모델 설계

초기 단일 방문 구조에서 다회차(N회 방문) 지원으로 확장할 때, 기존 사용자 데이터를 손상 없이 보존하기 위해 클라이언트 로딩 시점에 visitCount와 history 배열을 보정하는 데이터 정규화 레이어를 추가했습니다.


### 4) 전국 13개 종주 코스 Polyline 가시화

50여 개 연결 구간의 좌표 데이터를 구조화하여, 인접 인증센터 완주 여부에 따라 지도 위 경로선을 실선(완주) 또는 점선(미완주)으로 동적 렌더링했습니다. 사용자가 선택한 스탬프 테마 색상과 지도 위 완주 경로선 색상을 전역 동기화했습니다.

> 💡 💡 핵심 포인트: Kakao Maps SDK 위에 13개 종주 코스(50여 개 세그먼트)의 순서��을 정의하고, 사용자 스탬프 테마 컬러와 완주 경로선(실선 vs 점선)을 전역 동기화하여 높은 몰입감을 제공합니다.

▲ [그림 5-2] 모바일 브라우저 PWA 실행 화면 및 전국 13개 종주 코스 인터랙티브 지도
앱스토어 설치 없이 즉시 실행되며, Kakao Maps SDK를 기반으로 전국 85개 인증센터 위치와 종주 경로 완주 여부(실선/점선)를 한눈에 확인할 수 있는 화면입니다.


## 4. 결과 및 성과 (Result)

* Firebase Hosting을 통해 실제 상용 배포를 완료하고, 모바일 실기기에서 PWA 오프라인 캐싱 및 GPS 인증 동작 검증 완료
* Vue 3 Composition API, Vite, Pinia, Firebase NoSQL, PWA 등 모던 웹 기술 스택을 활용한 독자적인 서비스 완성

## 5. 회고 (Lesson Learned)

* AI 코딩 에이전트 오케스트레이션과 개발 생산성 혁신: 1인 스프린트로 기획, 시스템 아키텍처 정의, PWA 배포까지 전 과정을 완수하며, AI 도구를 적극 활용하되 컴포넌트 라이프사이클 누수 검증, 상태 정규화, 오프라인 캐싱 등 핵심 엔지니어링 결정은 개발자가 직접 주도하는 현대적 'AI-Native' 개발 워크플로우를 체득함.
* 오프라인-퍼스트 설계의 실효성 체감: 산간/강변 자전거길의 네트워크 음영 지역에서도 사용자 경험이 단절되지 않도록 외부 이미지 서버 요청을 완전히 배제하고 브라우저 연산(SVG 동적 생성)과 PWA Service Worker 캐싱을 극대화한 아키텍처의 강력한 안정성을 확인함.


