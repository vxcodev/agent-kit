# agent-kit

Bộ workspace dùng cho **Cursor agent** khi thực hiện nghiệp vụ code.

- Remote: https://github.com/vxcodev/agent-kit.git  
- Clone vào từng dự án (vd. `vssoft-admin/agent-kit/`) nhưng **git độc lập** — pull/push không dính repo host.  
- Được **nâng cấp liên tục** qua các dự án khác nhau để hoàn thiện quy trình.

**Version:** xem [`VERSION`](VERSION) · thay đổi: [`CHANGELOG.md`](CHANGELOG.md)

## Cấu trúc

```text
agent-kit/
├── README.md
├── VERSION
├── CHANGELOG.md
│
├── AGENTS.md
├── BOOTSTRAP.md
├── SOUL.md
├── TOOLS.md
├── SECURITY.md
│
├── agents/           # định nghĩa / profile agent (bổ sung dần)
├── workflows/        # playbook theo việc
├── rules/            # rule cứng tái sử dụng
└── templates/
    └── project/      # mẫu zdocs / file cho host
```

## Gắn vào host

```bash
git clone https://github.com/vxcodev/agent-kit.git agent-kit
# thêm agent-kit/ vào .gitignore của host
```

## Cập nhật / đóng góp kit

```bash
cd agent-kit
git pull origin main
# … sửa quy trình …
git add -A && git commit -m "…" && git push origin main
```

Bắt đầu đọc: [`BOOTSTRAP.md`](BOOTSTRAP.md) → [`AGENTS.md`](AGENTS.md).
