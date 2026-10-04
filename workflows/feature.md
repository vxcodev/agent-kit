# Workflow — Feature

## Purpose

Thêm hoặc đổi behavior theo requirement.

## Entry

User yêu cầu capability mới hoặc thay đổi behavior.

## Classification

Type FEATURE hoặc CHANGE. Complexity và risk tách riêng (`rules/risk.md`).

## Default Route

```text
BA? → Architect? → Developer → Tester → Reviewer → Deploy?
```

## Optional Agents

- Bỏ BA khi requirement đã rõ.
- Bỏ Architect khi impact NONE/MINOR và pattern hiện có đủ.
- Bỏ Deploy khi User không yêu cầu release.

## Required Gates

Tester PASS và Reviewer APPROVE khi route có hai vai đó.

## Approval Gates

Deploy production, migration, destructive: `rules/approval.md`.

## Failure Paths

`rules/task-lifecycle.md` — test fail, review changes, requirement loop, architecture loop.

## Completion

DoD của route. Deploy chỉ tính khi nằm trong scope.

## Artifacts

Requirement (nếu có), diff, test result, review result, STATE.
