# 여수한국병원 콩케어 데모·베타 검증 체크리스트 v1.0

## A. 사용성
- [ ] 첫 화면에서 목적을 5초 안에 이해
- [ ] 핵심 기능 3탭 이내
- [ ] 첫 혜택/도움 경로 30초 이내
- [ ] 글씨 크게 버튼 즉시 동작
- [ ] 보호자도 용어를 이해
- [ ] 뒤로가기/재탐색이 자연스러움

## B. 접근성
- [ ] 200% 확대에서도 내용 손실 없음
- [ ] 스크린리더 제목/버튼 순서 정상
- [ ] 색상만으로 상태 전달하지 않음
- [ ] 터치타깃 충분
- [ ] 쉬운글 표현
- [ ] 키보드/스위치 탐색 가능

## C. 정책 진실성
- [ ] 모든 정책카드 공식출처
- [ ] 기준일/지역범위 표시
- [ ] 받을 수 있음/없음 확정표현 금지
- [ ] 데이터 없으면 UNKNOWN/확인필요
- [ ] 만료/변경 정책 ACTIVE 오표기 없음

## D. 보안/개인정보
- [ ] 관리자 PIN/비밀정보 클라이언트에 없음
- [ ] 개인정보 입력 요구 없음
- [ ] 민감정보 저장 없음
- [ ] 외부 링크 rel=noopener
- [ ] QR/공유에 개인정보 포함 없음
- [ ] 로그에 민감정보 없음

## E. 현장성
- [ ] 환자 대기 중 한 손 사용 가능
- [ ] 고령자에게 긴 문장 최소화
- [ ] 직원이 3분 안에 설명 가능
- [ ] 보호자 공유 쉬움
- [ ] 네트워크 불안정 시 실패 메시지 명확

## F. Beta Evidence
각 테스트:
- TEST_ID
- DEVICE
- USER_TYPE (환자/보호자/직원; 식별정보 금지)
- TASK
- SUCCESS YES/NO
- TIME_TO_COMPLETE
- CONFUSION_POINT
- POLICY_ERROR YES/NO
- ACCESSIBILITY_BLOCKER YES/NO
- FIX
- RETEST_RESULT

## Promotion Gate
DEMO -> CLOSED BETA:
- P0 정책오류 0
- 접근성 Blocker 0
- 개인정보 수집 0
- 핵심 5개 시나리오 Golden PASS

CLOSED BETA -> HOSPITAL PILOT:
- 핵심과업 성공률 >= 90% 목표
- Critical/High 보안결함 0
- 잘못된 수급확정 표현 0
- rollback 가능
- OWNER 승인 + 병원 측 허용 확인
