# 콩케어 여수한국병원 데모 사용자 개선사항 수집·반영 루프 v1.0

STATUS: ACTIVE
SCOPE: 여수한국병원 데모/Closed Beta -> 개선 -> 재검증 -> 전국 V2 환류

## 목표
데모를 실제로 사용하게 한 뒤, 사용자 개선사항을 정형화해 빠르게 반영한다.
"의견 수집"에서 끝내지 않고, 모든 의견을 Evidence -> 분류 -> 수정 -> 회귀테스트 -> 재배포 후보까지 닫는다.

## 수집 채널
1. 앱 안 "불편했어요 / 제안하기" 폼
2. 현장 종이/QR 피드백
3. 직원/보호자 관찰 메모
4. 오류/정책오류 신고
5. 사용성 테스트 결과

민감정보는 수집하지 않는다.
이름/전화/주민번호/상세진단/병력 자유서술을 요구하지 않는다.

## 피드백 데이터 최소 스키마
- FEEDBACK_ID
- TEST_STAGE: D1/D2/D3/D4...
- USER_TYPE: 환자/보호자/직원/기타
- DEVICE_CLASS: Android/iPhone/PC/기타
- TASK: 무엇을 하려 했는지
- ISSUE_TYPE:
  - UX
  - ACCESSIBILITY
  - POLICY_TRUTH
  - MISSING_BENEFIT
  - LINK
  - PERFORMANCE
  - CONTENT_CLARITY
  - SECURITY_PRIVACY
  - OTHER
- SEVERITY: P0/P1/P2/P3
- COMMENT: 비식별 자유메모
- TIME_TO_COMPLETE
- SUCCESS: YES/NO
- EVIDENCE: screenshot/log/test-id optional
- STATUS: NEW/TRIAGED/FIXING/FIXED/RETEST/PASS/HOLD
- FIX_COMMIT
- RETEST_RESULT
- PROMOTED_TO_NATIONAL: YES/NO

## 우선순위
P0:
- 잘못된 복지/지원 정보
- 개인정보/보안 위험
- 접근성 차단
- 잘못된 긴급/의료 안내
=> 즉시 해당 기능 HOLD 또는 표시 제거 후 수정

P1:
- 핵심 과업 실패
- 링크 단절
- 3탭/30초 목표 실패
=> 다음 배포 전 수정

P2:
- 이해 어려움
- 동선 불편
- 가독성
=> 주기 내 개선

P3:
- 선호/디자인/부가 아이디어
=> 백로그

## 자동 반영 루프
COLLECT
-> DEDUPE
-> CLASSIFY
-> ROOT_CAUSE
-> FIX
-> UNIT/ACCESSIBILITY/POLICY REGRESSION
-> GOLDEN E2E RETEST
-> DEMO CANDIDATE
-> OWNER/HOSPITAL GATE IF EXTERNAL
-> RELEASE
-> NATIONAL_REUSE REVIEW

## 데모 앱 내 피드백 UX
버튼 2개:
- "불편했어요"
- "좋았어요 / 더 있었으면"

최대 3문항:
1. 무엇을 찾으셨나요?
2. 찾을 수 있었나요? 예/아니오
3. 가장 불편한 점은?
선택형 우선 + 선택적 짧은 메모.
개인정보를 적지 말라는 안내를 항상 표시.

## 개선 속도 SLA
- P0: 발견 즉시 격리, 같은 날 수정 목표
- P1: 24시간 내 수정 후보
- P2: 72시간 내
- P3: 주간 묶음

시간은 목표이며 PASS는 테스트 Evidence로만 선언.

## 전국 V2 환류
여수한국병원에서 반복되는 개선은 지역 특수 요구와 공통 요구로 나눈다.
- COMMON -> 전국 디자인/컴포넌트/정책엔진에 반영
- YEOSU_LOCAL -> 여수/전남 지역팩
- KIDNEY_SPECIALIST -> 신장·투석 전문팩
- HOSPITAL_WORKFLOW -> 기관용/B2B 모드

## Human Gate
- 병원에 새 버전 공식 배포
- QR 교체/게시
- 직원 공지
- 개인정보 수집 시작
- 외부 분석도구 신규 도입
은 OWNER 승인 + 필요한 병원 측 허용 확인 후 실행.
