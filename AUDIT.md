# AUDIT — 5sSoft Agent Kit 0.9.0

Ngày: 2026-10-04. Phạm vi: toàn bộ `agent-kit/` sau các Agent Orchestrator, BA, Architect, Developer, Tester, Reviewer, Deploy.

## Architecture Reviewed

```text
User → Orchestrator → Adaptive Workflow → Specialized Agents
    → Quality Gates → Completion → Project Learning
    → Distillation → Core Proposal
```

Core: identity, security, tools, bootstrap, registry. Process: agents, workflows, routing. Knowledge: memory, decisions, lessons — nằm ở `.agent/`, không nằm trong Core.

## Conflicts Found

| Concern | Trước | Xử lý |
|---|---|---|
| Priority | `AGENTS.md` 4 mức; Orchestrator 5 mức | Một hierarchy trong `rules/priority.md` |
| Task DONE | Orchestrator tự mô tả; Developer cấm tự DONE nhưng không có owner chung | `rules/task-lifecycle.md` |
| Approval | Reviewer APPROVE lẫn với production approval | `rules/approval.md` tách Agent Decision / Human / Policy |
| State vs memory | Rải trong Orchestrator và MEMORY host | `rules/state-management.md` |
| Security vs SOUL | SOUL đặt yêu cầu Sếp lên trước, không nêu security | SOUL nhường `SECURITY.md` |

## Duplicates Found

Security, git destructive, và secret được nhắc lại trong từng Agent và `SECURITY.md`. Giữ nhắc ngắn trong Agent. Owner dài: `SECURITY.md`. Không tạo `rules/git-safety.md` để tránh bản sao thứ hai.

Ví dụ risk trong từng Agent giữ lại như diễn giải theo vai. Nghĩa bốn mức nằm ở `rules/risk.md`.

## Changes Made

KEEP: bảy `agents/*/AGENT.md` (chỉ Orchestrator bỏ hierarchy riêng), template deploy/testing/review/development/architecture/requirements/orchestration, `IDENTITY.md`.

ADD: `rules/*` (7), `workflows/*` (6), `templates/project/config.yaml`, `templates/project/lessons/`, `AUDIT.md`.

REFERENCE: `AGENTS.md`, `BOOTSTRAP.md`, `SOUL.md`, `TOOLS.md`, `SECURITY.md`, `README.md`.

REMOVE: không xóa file.

## Ownership Decisions

| Concern | Owner |
|---|---|
| Security, git destructive, secret | `SECURITY.md` |
| Priority | `rules/priority.md` |
| Risk scale | `rules/risk.md` |
| Task state, result, DoD, retry | `rules/task-lifecycle.md` |
| STATE / MEMORY / DECISION / REPORT | `rules/state-management.md` |
| Handoff | `rules/handoff.md` |
| Approval kinds | `rules/approval.md` |
| Learning, distill, Core promotion | `rules/knowledge-management.md` + `workflows/distill.md` |
| Route theo loại việc | `workflows/*.md` |
| Role contract | `agents/*/AGENT.md` |
| Registry | `AGENTS.md` |
| Init | `BOOTSTRAP.md` |
| Tool use | `TOOLS.md` |
| Persona | `SOUL.md`, `IDENTITY.md` |
| Project facts | `.agent/` |

## Missing Parts Added

Workflow layer (trước đó chỉ `.gitkeep`). Execution mode. Lesson artifact. Distill workflow. Config template có `installedVersion`.

## Backward Compatibility

Template cũ không bị đổi schema yaml của deploy/testing/review. Key approval trong các file đó giữ nguyên (`approval.production`, `productionTesting`, …).

`templates/project/config.yaml` là file mới. Project đã có `.agent/config.yaml` không bị thay các key cũ; chỉ thêm `agentKit`, `execution`, `workflow`, `state`, `memory`, `learning`.

Migration Required: **NO** để chạy tiếp. **YES** nếu muốn project cũ khai báo mode: thêm các key trên. Thiếu key → coi `semi-auto` và adaptive như mặc định kit.

## Remaining Risks

- Agent file vẫn kể lại loop và risk example. Nhất quán nhờ reference, chưa xóa hết đoạn trùng để tránh rewrite hàng loạt.
- `TOOLS.md` còn ví dụ path `zdocs/` của host 5sSoft. Chưa phải secret; chưa generalize thêm.
- Chưa có CLI migration.

## Recommendations

- Lần sau đụng một Agent, thay đoạn policy dài bằng một link tới `rules/`.
- Push kit khi được yêu cầu.
- Không promote lesson vssoft-admin vào Core.
