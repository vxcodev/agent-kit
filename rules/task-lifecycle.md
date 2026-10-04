# Task Lifecycle

Orchestrator sở hữu lifecycle trong `.agent/STATE.md`. Agent con trả result; không tự đánh dấu task DONE.

## States

Dùng khi phù hợp — không bắt buộc mọi state:

```text
NEW
ANALYZING
NEEDS_CLARIFICATION
READY
IN_PROGRESS
BLOCKED
TESTING
REVIEWING
READY_TO_DEPLOY
DEPLOYING
VERIFYING
DONE
FAILED
CANCELLED
```

## Result

Generic: `success` · `blocked` · `failed` · `needs_input` · `changes_required`

Role decision (Orchestrator đọc cả hai):

| Agent | Decision |
|---|---|
| BA | READY / NEEDS_CLARIFICATION |
| Architect | READY / BLOCKED |
| Developer | COMPLETE / BLOCKED |
| Tester | PASS / FAIL / BLOCKED |
| Reviewer | APPROVE / REQUEST_CHANGES / BLOCKED |
| Deploy | SUCCESS / FAILED / BLOCKED |

Invocation thành công ≠ task thành công.

## Definition of Done

```text
DONE =
  required stages của route đã xong
  + required quality gates pass
  + required approvals tồn tại
  + deploy + verify pass   (chỉ khi deploy nằm trong scope)
```

`TASK DONE` khác `PRODUCTION DEPLOYED`.

## Loops

- Tester FAIL → Developer → Tester. Không Deploy khi Tester bắt buộc đang FAIL.
- Reviewer REQUEST_CHANGES → Developer → Tester nếu behavior đổi → Reviewer.
- Design thiếu → Architect → Developer.
- Business mơ hồ → BA → Human nếu cần → resume.
- Deploy fail → Rollback hoặc Stop → Diagnosis. Không bỏ gate.

## Retry

Cùng failure lặp ≥ `retry.maxSameFailure` (mặc định 2) → STOP → ESCALATE. Không retry vô hạn cùng input.
