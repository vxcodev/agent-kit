# Workflow — Bugfix

## Purpose

Sửa behavior sai so với requirement hoặc so với behavior đã chốt.

## Entry

Báo lỗi tái hiện được, hoặc symptom rõ.

## Classification

Type BUG. Đánh giá risk riêng (retry/idempotency/auth có thể HIGH dù diff nhỏ).

## Default Route

```text
Understand / Reproduce → Developer → Tester → Reviewer → Deploy?
```

## Optional Agents

- BA khi expected behavior chưa rõ.
- Architect khi root cause là thiết kế.

## Required Gates

Tester PASS trên case gốc + regression liên quan. Reviewer APPROVE.

## Approval Gates

Như `rules/approval.md` nếu đụng prod/data.

## Failure Paths

Tester FAIL quay Developer. Không Deploy khi test bắt buộc FAIL.

## Completion

Bug gốc được verify. DoD của route.

## Artifacts

Current vs desired, diff, test evidence, review result.
