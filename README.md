# agent-kit

Bộ workspace dùng cho **Cursor agent** khi thực hiện nghiệp vụ code.

- Remote: https://github.com/vxcodev/agent-kit.git
- Clone vào từng dự án (vd. `vssoft-admin/agent-kit/`) nhưng **git độc lập** — pull/push không dính repo host.
- Được **nâng cấp liên tục** qua các dự án khác nhau để hoàn thiện quy trình / skill / prompt / checklist.

## Dùng trong dự án host

1. Clone (nếu chưa có):

```bash
git clone https://github.com/vxcodev/agent-kit.git agent-kit
```

2. Thêm `agent-kit/` vào `.gitignore` của dự án host.
3. Cập nhật kit:

```bash
cd agent-kit && git pull origin main
```

## Cấu trúc dự kiến (sẽ bổ sung dần)

```text
agent-kit/
  README.md
  prompts/          # prompt nghiệp vụ tái sử dụng
  skills/           # skill / playbook cho agent
  checklists/       # checklist review / deploy
  templates/        # mẫu dexuat, history, PR…
```

Chưa có nội dung chuẩn hóa — commit đầu chỉ khai báo mục tiêu repo.
