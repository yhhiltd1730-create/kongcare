# KONGCARE FAST-TRACK DELIVERY ARCHITECTURE v1.0

## 목적
품질을 희생하지 않고 calendar time을 줄인다. 핵심은 더 빨리 코딩하는 것이 아니라 대기·직렬화·재작업을 제거하는 것이다.

## Delivery Pattern
Contract -> Parallel Build -> Continuous Presubmit -> Golden Integration -> Independent Validation -> Feature-flag Promotion.

## Fast gates
- PRE-COMMIT: format/lint/schema/unit/accessibility static checks
- PR: unit + component + contract + security + accessibility + Golden smoke
- INTEGRATION: cross-lane Golden E2E + policy truth + rollback
- PILOT: real browser/device/screen-reader/low-network
- RELEASE: independent security/accessibility/data-quality signoff

## Feature flags
Incomplete modules may merge disabled:
- voice
- account
- personalized recommendation
- admin CMS
- local policy automation
This avoids long-lived branches and merge-delay without exposing unfinished functions.

## Golden fixtures first
Freeze a small, verified corpus before broad ingestion:
- central disability registration
- disability pension / pension split cases
- transport
- health/medical cost relief
- utility/telecom discounts
- activity assistance/care
- employment/education
- housing
- emergency welfare
- one kidney/dialysis specialist pack

Every change must preserve expected eligibility wording, region scope, source, effective date and UNKNOWN behavior.

## Parallel ownership
Each lane owns disjoint paths. Shared contracts are versioned and immutable within a cycle. Integration lane alone reconciles shared interfaces.

## Stop-the-line
A red trunk on P0 truth/security/accessibility stops promotion, not all research/build lanes. Other disjoint safe work continues.

## Definition of speed
Velocity is measured by:
- lead time to validated slice
- rework rate
- Golden regression pass
- blocker age
- policy freshness
not by raw commit count.
