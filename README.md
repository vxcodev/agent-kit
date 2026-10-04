# agent-kit

Shared framework cho AI Agent phát triển phần mềm 5sSoft. Mỗi project kế thừa Core, giữ knowledge riêng, và chỉ đề xuất cải tiến Core sau distill + duyệt.

- Remote: https://github.com/vxcodev/agent-kit.git
- Clone vào host (`<project>/agent-kit/`) với **git riêng**. Không commit kit vào repo host.
- **Version:** [`VERSION`](VERSION) · [`CHANGELOG.md`](CHANGELOG.md)

## Cài

```bash
git clone https://github.com/vxcodev/agent-kit.git agent-kit
```

Thêm `agent-kit/` vào `.gitignore` của host. Project ghi version đang dùng tại `.agent/config.yaml` → `agentKit.installedVersion`. Không tự upgrade.

## Khởi tạo

Đọc [`BOOTSTRAP.md`](BOOTSTRAP.md). Nếu chưa có `.agent/`, copy từ `templates/project/` rồi điền fact. Đã có thì không ghi đè.

## Mode

`execution.mode` trong config project:

| Mode | Ai chọn bước tiếp |
|---|---|
| `manual` | Human chọn Agent / workflow / approval |
| `semi-auto` | Agent chạy route; dừng ở approval và blocker (mặc định) |
| `automatic` | Agent chạy hết route policy cho phép; production, destructive, security gate vẫn dừng |

Mode không đổi việc mỗi Agent được phép làm.

## Agent

Đăng ký: [`AGENTS.md`](AGENTS.md). Entry: Orchestrator.

```text
User → Orchestrator → workflow thích nghi → Agent chuyên biệt
    → quality gate → xong → lesson project → distill → đề xuất Core
```

## Workflow và rule

- Route: `workflows/` (`feature`, `bugfix`, `hotfix`, `refactor`, `release`, `distill`)
- Contract: `rules/` (priority, risk, lifecycle, state, handoff, approval, knowledge)
- Security: [`SECURITY.md`](SECURITY.md) — một owner

## Learning

Quan sát ghi `.agent/lessons/`. Nhớ lâu trong `.agent/MEMORY.md`. Đưa lên kit chỉ qua `workflows/distill.md` và Human approval, rồi bump version.

Mẫu nghiệp vụ nằm ở `catalog/` (project, module, component, function). `templates/project/` chỉ tạo khung `.agent/`. Project ghi mẫu đã chọn trong `.agent/CATALOG.md`.

Lúc mở project: đủ thiết lập cơ bản theo `rules/project-setup.md`. Phần chưa cần thì điền khi bước tương ứng dùng tới.

Nhận diện (logo, màu, banner, tỷ lệ, kích thước ảnh): `rules/brand.md`. Chưa có bộ riêng thì dùng `catalog/brand/default`.

## Cập nhật kit

```bash
cd agent-kit
git pull origin main
```

Sửa Core là task riêng: commit trong `agent-kit/`, không lẫn commit host.
