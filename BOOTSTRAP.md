# BOOTSTRAP

Checklist khi **bắt đầu phiên** hoặc **gắn kit vào dự án mới**.

## Gắn kit vào host mới

1. `git clone https://github.com/vxcodev/agent-kit.git agent-kit`
2. Thêm `agent-kit/` vào `.gitignore` của host
3. Ghi chú trong README host: cách `cd agent-kit && git pull`
4. (Tuỳ chọn) Copy mẫu từ `templates/project/` vào `zdocs/` của host nếu chưa có

## Mỗi phiên agent

1. Xác định host project + mục tiêu Sếp  
2. Đọc `AGENTS.md` + `SOUL.md` + `SECURITY.md`  
3. Chọn workflow phù hợp trong `workflows/`  
4. Không commit secret; không push nhầm vào repo host từ trong `agent-kit/`  

## Cập nhật kit

```bash
cd agent-kit
git pull origin main
```
