# 콩케어 익명 이벤트·정책분석 스키마 v1.0

## Event envelope
- event_id: random UUID, rotating/nonpersistent
- occurred_at
- session_id: short-lived random
- region_level_1: 시도
- region_level_2: 시군구 (optional)
- user_role: self/caregiver/staff/other/unknown
- disability_category: optional broad category/unknown
- event_type
- feature
- policy_id: optional
- task_id: optional
- success: yes/no/unknown
- duration_bucket
- issue_type
- source_version
- app_version

## Forbidden fields
- name
- phone
- resident registration number
- exact address
- hospital patient number
- detailed diagnosis narrative
- medical record
- persistent device fingerprint
- ad id
- precise GPS
- raw IP storage for analytics

## Event types
- app_open
- benefit_search
- benefit_result_view
- policy_card_open
- official_link_click
- checklist_add
- search_no_result
- unknown_result
- feedback_submit
- accessibility_toggle
- urgent_route_open

## Aggregation examples
- demand_by_region
- demand_by_category
- unmet_need_rate
- policy_clickthrough
- task_success_rate
- accessibility_friction
- average_time_to_help
- policy_gap_candidate

## Privacy threshold
기관/공개 리포트에서 세부 교차표는 최소 집단크기 기준을 적용한다.
초기 기본값 후보: n>=20.
실제 기준은 법률/보안/프라이버시 검토 후 확정한다.
