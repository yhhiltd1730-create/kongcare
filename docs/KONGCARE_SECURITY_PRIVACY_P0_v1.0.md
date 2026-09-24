# 콩케어 상용화 보안·개인정보 P0 감사 v1.0

## 발견된 즉시조치 항목
1. 현재 공개 index.html에 관리자 PIN 상수가 포함되어 있음.
   - 클라이언트 PIN은 인증수단으로 인정하지 않음.
   - 상용화 브랜치에서 관리자 수정기능을 사용자 화면과 분리하고 서버측 인증으로 이동.

2. 현재 단일 HTML에 데이터/표시/관리 기능이 혼재.
   - 정책 데이터, UI, 관리도구 분리 필요.
   - 잘못된 정책 업데이트가 전체 서비스에 즉시 영향을 주지 않도록 draft/review/publish 상태 도입.

3. 전국/전 장애유형 확장 시 건강·장애정보가 유입될 가능성.
   - V1은 비로그인·로컬 저장 우선.
   - 서버 저장이 필요해질 때 별도 Privacy Gate.

4. 외부 QR 생성 서비스 호출 존재.
   - 사용 URL이 제3자에게 노출될 수 있으므로 상용화 시 자체 QR 생성 또는 로컬 라이브러리 검토.

5. 외부 링크 다수.
   - 링크 allowlist/health-check/변경감시 필요.

## 출시 전 필수
- CSP/보안헤더
- dependency/SCA
- secret scan
- XSS/URL validation
- admin RBAC + MFA 권장
- audit log
- backup/rollback
- incident response
- 개인정보처리방침/삭제/문의 경로
- 접근성+보안 회귀 테스트
