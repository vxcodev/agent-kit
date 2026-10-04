# Knowledge

```text
Execution → Observation → Project Lesson → Project Memory
    → Candidate → Distill → Core Proposal → Human Review → Agent Kit
```

Lesson trước tiên thuộc **project** (`.agent/lessons/`, `.agent/MEMORY.md`). Không tự ghi vào `agent-kit/`.

Promote khi: tái sử dụng được, không dính customer/project, không secret, không mâu thuẫn Core, lợi ích rõ, có evidence.

Workflow: `workflows/distill.md`.

Project mới kế thừa Core agents, workflows, rules, templates. Không kế thừa STATE, secret, data khách, memory tạm, business rule của project khác — trừ khi đã được chấp nhận thành Core.

`PROJECT GIT` khác `AGENT-KIT GIT`. Không commit/push Core từ workflow project.
