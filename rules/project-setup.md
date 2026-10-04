# Project Setup

Khi bắt đầu project, làm rõ thiết lập cơ bản và ghi vào `.agent/`. Không bịa phần còn trống.

## Phải có trước khi làm việc

| Mục | Chỗ ghi | Đủ nghĩa là |
|---|---|---|
| Dự án là gì | `.agent/PROJECT.md` | Tên và mục đích một câu |
| Việc đang làm | `.agent/requirements/` hoặc `.agent/STATE.md` | Goal của lát cắt hiện tại |
| Mẫu catalog | `.agent/CATALOG.md` | `CONFIRMED` hoặc `NONE` |
| Nhận diện | `.agent/BRAND.md` | `DEFAULT`, `MIXED`, hoặc `PROJECT` |
| Repo | `.agent/PROJECT.md` hoặc `config.yaml` | Remote host nếu đã có git |

Agent điền được từ repo thì không hỏi lại. `execution.mode` thiếu thì dùng `semi-auto`.

`CATALOG.md` còn `UNCONFIRMED` thì dừng ở bước chọn mẫu. Chưa chọn thì không sang implement.

Chưa có bộ nhận diện riêng thì ghi `DEFAULT` và dùng `catalog/brand/default`. Mục riêng thiếu thì lấy mục đó từ default (`MIXED`). Quy tắc: `rules/brand.md`.

## Để sau, khi bước đó cần dữ liệu

| Mục | Bổ sung khi |
|---|---|
| Lệnh build, lint, convention | Developer chạy kiểm tra |
| Lệnh và môi trường test | Tester |
| Rule kiến trúc chi tiết | Architect, khi có thay đổi thiết kế |
| Host, môi trường, domain deploy | Deploy |
| Business rule ngoài lát cắt hiện tại | Lát cắt đó bắt đầu |
| Secret, credential | Bước cần dùng; không ghi giá trị vào `.agent/` |

Thiếu những mục này **không** chặn project nếu bước hiện tại không đọc chúng.

## Cách xử lý chỗ trống

```text
Bước hiện tại có cần dữ liệu này không?
    có, chưa đủ → hỏi Human, không đoán
    không      → ghi "bổ sung khi: <bước>" và tiếp tục
```

Đến bước cần dữ liệu mà vẫn trống → dừng bước đó, hỏi, rồi ghi vào đúng file project. Không bắt điền cả `.agent/` ngay từ đầu.
