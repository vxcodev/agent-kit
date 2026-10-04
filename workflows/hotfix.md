# Workflow — Hotfix

## Purpose

Sửa khẩn trên đường release, vẫn giữ quality gate.

## Entry

Sự cố cần sửa sớm. Chữ “urgent” không bỏ security.

## Classification

Type HOTFIX. Risk thường HIGH trở lên cho đến khi chứng minh ngược lại.

## Default Route

```text
Developer → Focused Test → Reviewer → Deploy → Verify
```

## Optional Agents

BA/Architect chỉ khi behavior hoặc design chưa đủ để sửa an toàn.

## Required Gates

Focused test PASS trên lỗi và vùng hồi quy trực tiếp. Reviewer APPROVE. Post-deploy verify nếu có Deploy.

## Approval Gates

Production deploy vẫn cần Human approval theo policy. Không bypass.

## Failure Paths

Test/review fail → quay Developer. Deploy fail → rollback hoặc stop.

## Completion

Verify PASS sau release trong scope. Nếu chưa deploy, DONE chỉ ở mức implementation đã review.

## Artifacts

Diff tối thiểu, test evidence, review, deploy/verify report.
