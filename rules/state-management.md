# State, Memory, Decision, Report

Bốn kho không trộn nội dung.

| Kho | Câu hỏi | Ví dụ | Path |
|---|---|---|---|
| **STATE** | Đang xảy ra gì? | task, stage, agent, blocker, next | `.agent/STATE.md` |
| **MEMORY** | Nhớ lâu dài điều gì? | convention, constraint ổn định | `.agent/MEMORY.md` |
| **DECISION** | Vì sao chọn? | ADR, trade-off | `.agent/decisions/` |
| **REPORT** | Lần chạy đã xảy ra gì? | test, review, deploy | `.agent/reports/` |

Lesson thô nằm ở `.agent/lessons/` trước khi promote vào MEMORY. Xem `rules/knowledge-management.md`.

Không ghi secret vào bất kỳ kho nào. Owner security: `SECURITY.md`.
