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
├── CATALOG.md
├── BRAND.md
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

`CATALOG.md` là file nhận diện mẫu (`UNCONFIRMED` cho đến khi Human chốt). Không ghi đè khi đã `CONFIRMED` hoặc `NONE`.
