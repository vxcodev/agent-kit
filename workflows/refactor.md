# Workflow — Refactor

## Purpose

Đổi cấu trúc bên trong, giữ behavior.

## Entry

Task ghi rõ refactor. Không tự mở refactor từ task behavior khác.

## Classification

Type REFACTOR. Risk theo vùng đụng (auth/data = không còn LOW).

## Default Route

```text
Developer → Tester → Reviewer
```

## Optional Agents

Architect khi đổi boundary/module. BA không cần nếu behavior không đổi. Deploy theo yêu cầu.

## Required Gates

Regression phù hợp PASS. Reviewer kiểm tra scope không lẫn behavior change.

## Approval Gates

Major structure change: Human approval theo `.agent/architecture/`.

## Failure Paths

Behavior đổi ngoài ý muốn → coi như bugfix loop, không APPROVE.

## Completion

Behavior giữ nguyên đã được test. DoD của route.

## Artifacts

Phạm vi refactor, test regression, review.
