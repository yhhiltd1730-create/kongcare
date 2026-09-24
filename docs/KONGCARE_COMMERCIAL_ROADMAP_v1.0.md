# 콩케어 전국 상용화 실행 로드맵 v1.1 — QUALITY-PRESERVING FAST TRACK

STATUS: ACTIVE
GOAL: 품질 Gate는 낮추지 않고 개발 대기시간·직렬작업·재작업을 제거하여 최대한 빠르게 전국형 상용 V1에 도달한다.

## 0. 핵심 원칙
기간 단축은 "테스트 생략"이 아니라 아래 방식으로만 한다.
- 병렬화: UI / 정책데이터 / 접근성 / 보안 / AI대화 / 테스트를 동시에 진행
- Shift-left: 코딩과 동시에 접근성·보안·단위·계약 테스트
- 작은 변경 + 짧은 브랜치 + 빠른 통합
- Feature Flag: 미완성 기능은 숨기고 통합을 지연시키지 않음
- Contract-first: 정책 데이터/API/컴포넌트 계약을 먼저 고정
- Golden fixture: 대표 정책·지역·장애유형의 정답 세트를 먼저 만들고 모든 변경에 회귀검증
- Mock/Simulation first: 외부기관/API가 준비되지 않아도 내부 계약으로 개발 지속
- Risk-based testing: P0(정확도·보안·접근성)은 전수, 저위험 UI는 자동회귀 중심
- Evidence Before Claim: 시간 단축을 이유로 PASS 기준을 낮추지 않음
- Production/개인정보/비용/외부제출은 Human Gate 유지

## 1. 압축 일정

### T+0 ~ 72시간 — FAST FOUNDATION / 클릭 가능한 전국형 Alpha
병렬 Lane:
A. UI/Design System
B. 정책 데이터 스키마 + Golden fixtures
C. 접근성 컴포넌트/자동검사
D. 보안 P0 격리
E. 검색/필터/체크리스트
F. AI 대화 인터페이스 Mock
G. CI/회귀테스트

완료 기준:
- 전국형 홈/지역/장애유형/혜택 흐름 클릭 가능
- 기존 신장·투석 콘텐츠 전문팩으로 이관 가능
- client-side 관리자 PIN 제거 설계/격리
- 정책 Source/기준일/상태 필수 필드
- 자동 테스트가 이후 개발을 막아주는 상태

### T+4 ~ 7일 — QUALITY ALPHA
- 중앙정부 핵심 복지정책 Golden dataset
- 최소 3개 권역 지역팩
- 혜택 검색/필터/체크리스트
- 큰글씨/스크린리더/키보드/쉬운글
- 음성 질문의 내부 Mock E2E
- 관리자 Draft -> Review -> Publish 흐름 초안
- 보안/접근성 회귀 CI

완료 기준:
- 핵심 사용자 여정 Golden E2E PASS
- P0 보안/접근성 Blocker 0
- 공식 근거 없는 정책 노출 0

### T+8 ~ 14일 — NATIONAL MVP
- 전국 시도/시군구 구조
- 중앙정책 + 우선지역 정책 데이터
- 실제 공식 출처 ingestion
- 정책 변경상태/만료/검증일
- 보호자 모드
- 음성/대화 Read-only Beta
- 저속망/오프라인 graceful degradation
- 관측/오류보고

완료 기준:
- "전국 어디서나 검색 가능한 구조" 완성
- 전국 모든 지자체의 완전한 데이터 충족을 MVP 완료조건으로 삼지 않음
- 데이터가 없는 지역은 UNKNOWN/확인필요로 정직하게 표시

### T+3 ~ 4주 — PILOT / REALITY E2E
- 전남/광주 + 수도권 + 영남/충청 중 추가 권역
- 실제 장애유형 사용자 시나리오
- 보조기기/스크린리더 실사용 테스트
- 정책 변경감지 -> 검토 -> 게시 실제 흐름
- 복구/rollback/incident drill
- 개인정보 최소수집 설계 검증

완료 기준:
- 5개 이상 지역 Golden E2E
- 대표 장애유형 핵심 과업 성공률 측정
- Critical/High 보안 결함 0

### T+5 ~ 6주 — PUBLIC BETA 후보
- 전국 정책 커버리지 확대
- 음성/대화 Golden E2E
- 사용자 신고/정정 루프
- 운영 CMS
- 성능/관측/백업
- 접근성 실제 사용자 검증 1차 완료

출시 여부는 날짜가 아니라 Gate PASS로 결정.

### T+8 ~ 12주 — COMMERCIAL V1 후보
- B2B/B2G 관리자 대시보드
- 정책 품질 SLA/신선도 지표
- 기관별 tenancy/권한
- 감사로그/복구
- 약관/개인정보/보안/접근성 Release Gate
- 운영 Runbook / 장애대응 / 지원 프로세스

## 2. 기존 일정 대비
- 기존 전국 MVP: 6주 -> 목표 2주
- 기존 실사용 베타: 10~16주 -> 목표 5~6주
- 기존 Commercial V1: 4~6개월 -> 목표 8~12주

이 수치는 "기능 축소"가 아니라 병렬개발·자동검증·Mock/Contract-first·재사용을 전제로 한 공격적 목표다.
전국 모든 지자체 정책을 높은 정확도로 완전히 채우는 일은 출시 후에도 지속되는 DataOps 업무이며, 제품 코드 완료와 분리한다.

## 3. 7-LANE 가상세계 제작 구조
LANE-1 UX/UI
LANE-2 POLICY DATA
LANE-3 ACCESSIBILITY
LANE-4 SECURITY/PRIVACY
LANE-5 AI/VOICE
LANE-6 QA/GOLDEN E2E
LANE-7 INTEGRATION/RELEASE

규칙:
- 공통 계약만 공유하고 구현은 병렬
- lane 간 직접 충돌 금지, 통합은 Integration lane
- Producer != final validator
- P0/P1 실패 시 해당 lane만 HOLD, 나머지 독립작업은 계속
- 동일 파일 다중 writer 금지

## 4. 시간 잡아먹는 요소 제거
- 회의/승인 대기 -> 안전한 내부 변경은 자동진행
- 실제 API 대기 -> mock adapter
- 정책 원문 수집 대기 -> canonical fixture + 이후 incremental ingestion
- 화면 완성 후 접근성 점검 -> 컴포넌트 생성 순간부터 검사
- 마지막에 보안감사 -> PR마다 security checks
- 거대한 기능 PR -> 하루 이내 작은 slice
- 수동 회귀 -> Golden automated regression
- 모든 지역 완성 후 출시 -> coverage 표시 + UNKNOWN 상태로 점진 확대

## 5. 절대 단축하지 않는 품질 Gate
1. 정책 근거/시행일/지역범위
2. 접근성 blocker
3. 민감정보/인증/권한
4. 정책 오정보 rollback
5. 실제 장애인/보조기기 검증
6. External production release
7. 결제/개인정보/기관 계약

## 6. 사용자 체감 목표
- 첫 혜택 도달 <= 30초
- 핵심 과업 3탭 이내
- 결과 카드에서 "얼마/누가/어디서/무엇을 준비/공식근거" 즉시 확인
- 쉬운글/큰글씨/음성/보호자 모드가 별도 앱이 아니라 동일 제품에 내장
- 사용자가 정책명을 몰라도 자연어로 찾을 수 있음

## 7. 현재 다음 자동 실행 순서
1. policy schema + Golden fixture
2. component/design system + accessibility baseline
3. admin 기능 격리
4. 지역/장애유형 routing
5. benefit search/checklist
6. AI/voice mock adapter
7. CI Golden E2E
8. 실제 official-source ingestion
9. pilot region expansion
10. real-user accessibility validation

## Human Gate
자동 진행 금지:
- production 배포
- 신규 유료 API/서비스 비용
- 개인정보 수집 개시
- 외부기관 제휴/계약/제출
- 결제/도메인
- 실제 사용자 민감정보 처리
