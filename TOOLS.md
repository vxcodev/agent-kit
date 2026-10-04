# TOOLS

Tool policy: **cách dùng tool an toàn**. Agent quyết định **việc cần làm**; file này không thay responsibility trong `agents/*/AGENT.md`.

Git destructive và secret: authoritative tại [`SECURITY.md`](SECURITY.md). Không commit/push `agent-kit` từ workflow project — hai repository tách biệt.

## Trong repo host

- Đọc/sửa code bằng file tools của Cursor.  
- Shell: build, test, git — theo rule host.  
- Không commit `agent-kit/` vào host.

## Trong `agent-kit/`

```bash
cd agent-kit
git status
git pull origin main
git add … && git commit … && git push origin main
```

Remote mặc định: `https://github.com/vxcodev/agent-kit.git`

## Tài liệu host thường gặp

| Path host | Mục đích |
|---|---|
| `zdocs/dexuat/` | Đề xuất chờ duyệt |
| `zdocs/history/` | Nhật ký đã apply |
| `zdocs/prompts/` | Prompt tạm / task |

Mẫu có thể lấy từ `templates/project/`.
