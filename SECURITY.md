# SECURITY

## Cấm

- Commit / log / dexuat / STATE / MEMORY / LESSONS / DECISIONS / REPORTS / deployment report chứa **API key, bot token, mật khẩu, private key, SSH key**.  
- Push secret lên `agent-kit` hoặc host.  
- Commit `.env` / credentials.  
- Chạy lệnh phá hủy prod khi chưa được Sếp xác nhận rõ.  
- Tự ý thao tác Git phá hủy (`push --force`, `reset --hard`, `clean -fd`, xóa branch) khi chưa có yêu cầu rõ.  
- Tự ý `DROP` / `TRUNCATE` / xóa data production hoặc destructive migration khi chưa có authorization rõ.

## Deploy / Production

- Production deployment: tuân thủ approval trong `.agent/deploy/environments.yaml` (mặc định template: `approval.production: required`).  
- Database migration: `approval.databaseMigration: required` → dừng xin duyệt trước khi chạy.  
- Chỉ báo secret dạng `configured` / `missing` — không in giá trị.  
- Chi tiết: `agents/deploy/AGENT.md`.

## Testing

- Không xóa / stress production ngoài authorization; không disable security để test PASS.  
- Production testing: tuân thủ `.agent/testing/config.yaml` (`approval.productionTesting` nếu có).  
- Evidence / report không chứa secret.  
- Chi tiết: `agents/tester/AGENT.md`.

## Review

- Reviewer không APPROVE khi còn critical security / secret exposure / authz bypass.  
- Review report không chứa secret.  
- Không tự sửa application rồi tự APPROVE.  
- Chi tiết: `agents/reviewer/AGENT.md`.

## Development

- Không hard-code secret; không commit `.env` có credential.  
- Không bypass authorization / disable security để “cho chạy”.  
- Không destructive prod / force-push / phá Git state người khác.  
- Đang làm project: không tự sửa `agent-kit/` Core khi chưa được phép.  
- Chi tiết: `agents/developer/AGENT.md`.

## Architecture

- Security by design; không lưu secret trong design / ADR / `.agent/`.  
- Major architecture change / destructive migration: approval theo `.agent/architecture/config.yaml`.  
- Chi tiết: `agents/architect/AGENT.md`.

## Requirements / BA

- Không lưu credential / secret trong requirement, STATE, MEMORY, reports.  
- User cung cấp secret → ghi `CONFIGURED EXTERNALLY`, không propagate giá trị.  
- Chi tiết: `agents/ba/AGENT.md`.

## Orchestration

- Không bypass security / Quality Gate vì “urgent” hoặc User skip tùy tiện.  
- Silence ≠ approval. Không ghi secrets vào STATE/MEMORY/report.  
- Chi tiết: `agents/orchestrator/AGENT.md`.

## Nên

- Secret chỉ trên host (`~/.…/secrets`, `.env` gitignore).  
- Dexuat ghi **path** file secret, không ghi nội dung.  
- Review diff trước push kit (tránh lỡ dán key vào markdown).

## Repo public

`agent-kit` có thể public — coi mọi file trong kit là **không chứa secret**.
