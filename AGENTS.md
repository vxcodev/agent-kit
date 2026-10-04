# AGENTS

Hướng dẫn cho Cursor agent khi làm việc **trong dự án host** có kèm `agent-kit/`.

## Vai trò

- Đọc kit này trước khi làm nghiệp vụ lặp lại (đề xuất, review, deploy, tách module…).
- Ưu tiên `workflows/` và `rules/` của kit; không invent quy trình lệch kit trừ khi Sếp yêu cầu.
- Khi cải thiện quy trình: cập nhật **agent-kit** (repo riêng), không nhét rule tạm vào từng host.

## Thứ tự đọc

1. `BOOTSTRAP.md` — khởi động phiên / dự án mới  
2. `SOUL.md` — nguyên tắc hành xử  
3. `SECURITY.md` — ranh giới bảo mật  
4. `TOOLS.md` — tool được phép / cách dùng  
5. `workflows/` — playbook theo việc  
6. `rules/` — rule cứng  
7. `templates/project/` — mẫu file cho host  

## Git

- `agent-kit/` là repo **độc lập** với host (`git pull` / `git push` riêng trong thư mục này).
- Host phải `.gitignore` thư mục `agent-kit/`.
