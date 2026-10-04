# Changelog

Mọi thay đổi đáng chú ý của **agent-kit** ghi tại đây.

Format dựa trên [Keep a Changelog](https://keepachangelog.com/); version theo [SemVer](https://semver.org/).

## [0.10.0] — 2026-10-04

### Added

- `catalog/` — kho project mẫu, module, component, function (chưa có mục)
- `templates/project/CATALOG.md` — file nhận diện, mặc định `UNCONFIRMED`
- Bootstrap §3.9: tạo `.agent/CATALOG.md` nếu chưa có, không ghi đè bản đã chốt

### Changed

- `workflows/distill.md` và `rules/knowledge-management.md`: đích có thể là catalog
- Orchestrator, Developer, Reviewer: đối chiếu `.agent/CATALOG.md` và requirement sau khi chốt
- `rules/project-setup.md`: thiết lập cơ bản phải đủ lúc bắt đầu; phần chưa ảnh hưởng thì bổ sung khi bước đó cần dữ liệu
- `rules/brand.md` và `catalog/brand/default`: nhận diện trước khi làm UI; mục thiếu lấy từ bộ mặc định
- Ảnh chuẩn trong `catalog/brand/default/images/` (placehold.co, nhãn ngắn, đúng khổ)

## [0.9.0] — 2026-10-04

### Added

- Canonical rules: `rules/{priority,risk,task-lifecycle,state-management,handoff,approval,knowledge-management}.md`
- Workflows: `workflows/{feature,bugfix,hotfix,refactor,release,distill}.md`
- Lesson template: `templates/project/lessons/`
- Project config template: `templates/project/config.yaml` (`execution.mode`, approval, learning)
- `AUDIT.md` — ownership, conflict, consolidation

### Changed

- `AGENTS.md`: một priority hierarchy; bảng collaboration, không copy contract Agent
- Orchestrator: bỏ hierarchy riêng, trỏ `rules/priority.md`
- `SECURITY.md`: cấm secret trong LESSONS / DECISIONS / REPORTS
- `SOUL.md` và `TOOLS.md`: trỏ owner, không nhân bản policy
- `BOOTSTRAP.md` §3.8 lessons, không ghi đè
- `README.md`: bản đồ kit, mode, learning

## [0.8.0] — 2026-10-04

### Added

- Shared **Orchestrator Agent**: `agents/orchestrator/AGENT.md`
- Template project orchestration: `templates/project/orchestration/{ORCHESTRATION.md,config.yaml}`
- Đăng ký Orchestrator trong `AGENTS.md` (entry point)
- Bootstrap §3.7: khởi tạo `.agent/orchestration/` từ template, không ghi đè

### Changed

- `SECURITY.md`: bổ sung orchestration / không bypass gate
- Luồng chuẩn: User → Orchestrator → adaptive route → Done

## [0.7.0] — 2026-10-04

### Added

- Shared **BA Agent**: `agents/ba/AGENT.md`
- Template project requirements: `templates/project/requirements/{REQUIREMENTS.md,config.yaml}`
- Đăng ký Business Analyst Agent trong `AGENTS.md`
- Bootstrap §3.6: khởi tạo `.agent/requirements/` từ template, không ghi đè

### Changed

- `SECURITY.md`: bổ sung requirements / không lưu secret trong BA output
- Luồng chuẩn: User → BA? → Architect? → Developer → Tester → Reviewer → Deploy (fast path khi không cần BA)

## [0.6.0] — 2026-10-04

### Added

- Shared **Architect Agent**: `agents/architect/AGENT.md`
- Template project architecture: `templates/project/architecture/{ARCHITECTURE_RULES.md,config.yaml}`
- Đăng ký Architect Agent trong `AGENTS.md`
- Bootstrap §3.5: khởi tạo `.agent/architecture/`, giữ `.agent/decisions/`, không ghi đè

### Changed

- `SECURITY.md`: bổ sung architecture / major-change approval
- Luồng chuẩn: Requirement → [BA?] → Architect? → Developer → Tester → Reviewer → Deploy (fast path khi không cần Architect)

## [0.5.0] — 2026-10-04

### Added

- Shared **Developer Agent**: `agents/developer/AGENT.md`
- Template project development: `templates/project/development/{DEVELOPMENT.md,config.yaml}`
- Đăng ký Developer Agent trong `AGENTS.md`
- Bootstrap §3.4: khởi tạo `.agent/development/` từ template, không ghi đè

### Changed

- `SECURITY.md`: bổ sung development / kit protection
- Luồng chuẩn: Requirement → Developer → Tester → Reviewer → Deploy → Verify

## [0.4.0] — 2026-10-04

### Added

- Shared **Reviewer Agent**: `agents/reviewer/AGENT.md`
- Template project review: `templates/project/review/{REVIEW.md,config.yaml}`
- Đăng ký Reviewer Agent trong `AGENTS.md`
- Bootstrap §3.3: khởi tạo `.agent/review/` từ template, không ghi đè

### Changed

- `SECURITY.md`: bổ sung review / không tự sửa rồi APPROVE
- Luồng chuẩn: Implementation → Tester → Reviewer → Deploy

## [0.3.0] — 2026-10-04

### Added

- Shared **Tester Agent**: `agents/tester/AGENT.md`
- Template project testing: `templates/project/testing/{TESTING.md,config.yaml}`
- Đăng ký Tester Agent trong `AGENTS.md`
- Bootstrap §3.2: khởi tạo `.agent/testing/` từ template, không ghi đè

### Changed

- `SECURITY.md`: bổ sung testing / productionTesting
- Luồng chuẩn ghi rõ Tester trước Deploy Agent

## [0.2.0] — 2026-10-04

### Added

- Shared **Deploy Agent**: `agents/deploy/AGENT.md`
- Template project deploy: `templates/project/deploy/{DEPLOY.md,environments.yaml}`
- Đăng ký Deploy Agent trong `AGENTS.md`
- Bootstrap §3.1: khởi tạo `.agent/deploy/` từ template, không ghi đè nếu đã có

### Changed

- `SECURITY.md`: bổ sung production approval, DB destructive, Git destructive, không ghi secret vào state/report

## [0.1.0] — 2026-10-04

### Added

- Khung thư mục ban đầu: `AGENTS.md`, `BOOTSTRAP.md`, `SOUL.md`, `TOOLS.md`, `SECURITY.md`
- Thư mục `agents/`, `workflows/`, `rules/`, `templates/project/`
