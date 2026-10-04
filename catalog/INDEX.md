# Catalog

Thư viện mẫu dùng chung. Project host không sửa thư mục này trong lúc làm việc. Chỉ ghi sau `workflows/distill.md` và Human Accept.

Project, module, component, function: chưa có mục. Không thêm mẫu giả.

Brand mặc định (có sẵn): `brand/default` @ 1.0.0. Quy tắc: `rules/brand.md`.

## Loại

| Kind | Path |
|---|---|
| `project` | `projects/<id>/` — `manifest.yaml`, `BLUEPRINT.md`, `tree/` |
| `module` | `modules/<id>/` |
| `component` | `components/<id>/` |
| `function` | `functions/<id>/` |
| `brand` | `brand/<id>/` — `manifest.yaml`, `BRAND.md` |

## manifest.yaml

```yaml
id: <id>
kind: project
version: 1.0.0
status: active
summary: ""
tags: []
provides: []
needs: []
related: []
derivedFrom: []
lineage: []
```

`status`: `draft` | `active` | `deprecated`.

Version của **mục** (không phải version kit):

| Thay đổi | Version |
|---|---|
| Làm rõ, không đổi khung | PATCH |
| Thêm phần tùy chọn | MINOR |
| Đổi ranh giới | MAJOR hoặc id mới |

Bản cũ giữ trong git. Không xóa. Không ghi secret, domain khách, `.env`.

## So khớp

Lần phân tích đầu: đọc file này, gợi ý theo `tags` và `provides`, Human chọn.

Sau khi `.agent/CATALOG.md` là `CONFIRMED` hoặc `NONE`: không đọc lại INDEX, trừ khi Human yêu cầu đổi mẫu.
