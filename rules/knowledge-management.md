# Knowledge

```text
Execution → Observation → Project Lesson → Project Memory
    → Candidate → Distill → Human Review → Agent Kit
```

Đích sau Human Accept:

- Quy trình / rule Core, hoặc
- `catalog/` — project mẫu, module, component, function

Lesson trước tiên thuộc **project** (`.agent/lessons/`, `.agent/MEMORY.md`). Không tự ghi vào `agent-kit/`.

Promote khi: tái sử dụng được, không dính customer/project, không secret, không mâu thuẫn Core, lợi ích rõ, có evidence.

Workflow: `workflows/distill.md`. Kho mẫu: `catalog/INDEX.md`.

Project đã chốt mẫu ghi cứng trong `.agent/CATALOG.md`. Task sau đối chiếu file đó và `.agent/requirements/`. Không tự nâng version trong file này khi catalog có bản mới.

Project mới kế thừa Core agents, workflows, rules, templates, và catalog đã Accept. Không kế thừa STATE, secret, data khách, memory tạm, business rule của project khác.

`PROJECT GIT` khác `AGENT-KIT GIT`. Không commit/push Core từ workflow project.
