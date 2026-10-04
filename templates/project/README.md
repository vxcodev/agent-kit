# templates/project

Mẫu khởi tạo `.agent/` khi host chưa có thư mục đó. Đã có thì không ghi đè.

```text
.agent/
├── config.yaml
├── PROJECT.md
├── USER.md
├── ARCHITECTURE.md
├── MEMORY.md
├── STATE.md
├── tasks/
├── decisions/
├── reports/
├── lessons/
├── requirements/
├── architecture/
├── development/
├── testing/
├── review/
├── deploy/
└── orchestration/
```

`PROJECT.md`, `USER.md`, `ARCHITECTURE.md`, `MEMORY.md`, `STATE.md` được điền từ fact của host lúc bootstrap — không có bản mẫu chứa dữ liệu project.

`execution.mode`: `automatic` | `semi-auto` | `manual`. Khuyến nghị `semi-auto`.
