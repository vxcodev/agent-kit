# Workflow — Release

## Purpose

Đưa bản đã implement, test, review lên môi trường.

## Entry

Source đã COMPLETE + Tester PASS + Reviewer APPROVE, hoặc User chỉ yêu cầu deploy bản đó.

## Classification

Type DEPLOY.

## Default Route

```text
Deploy → Verify
```

## Optional Agents

Không chạy lại BA, Architect, Developer nếu không có thay đổi mới.

## Required Gates

Pre-deploy checks của Deploy Agent. Post-deploy verification PASS.

## Approval Gates

`PRODUCTION_DEPLOY_APPROVED` khi policy yêu cầu. Reviewer APPROVE không thay giấy này.

## Failure Paths

Deploy fail → rollback hoặc stop → diagnosis. Không đánh DONE.

## Completion

Deploy SUCCESS và verify PASS.

## Artifacts

Deploy report, verify result, STATE.
