# Workflow — Distill

## Purpose

Chưng cất lesson project thành đề xuất Core. Không sửa `agent-kit/` trong workflow này.

## Entry

Có lesson đánh dấu reusable hoặc Core candidate.

## Classification

Type ANALYSIS. Không phải implementation.

## Default Route

```text
Select lesson → Generalize → Duplication check
→ Conflict check → Security check → Core proposal → Human review
```

## Optional Agents

Reviewer có thể đọc proposal. Không Deploy.

## Required Gates

Bỏ chi tiết project/customer. Không secret. Không trùng rule đã có. Không mâu thuẫn `SECURITY.md` và `rules/`.

## Approval Gates

Human approval trước khi ai được sửa Agent Kit. Accept hoặc Reject.

## Failure Paths

Không đủ điều kiện → giữ trong `.agent/lessons/` hoặc MEMORY. Không push Core.

## Completion

Proposal được ghi (report hoặc dexuat) và có quyết định Human. Core chỉ đổi ở task cập nhật kit riêng, kèm VERSION và CHANGELOG.

## Artifacts

Lesson đã generalize, proposal, quyết định Accept/Reject.
