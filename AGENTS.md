# 5sSoft Agent Kit

## Purpose

Đây là bộ quy tắc chung dành cho AI Agent tham gia phát triển các dự án phần mềm của 5sSoft.

## Operating Rules

Agent phải:

1. Đọc `BOOTSTRAP.md` trước khi thực hiện công việc.
2. Đọc `IDENTITY.md` (danh tính / cách xưng hô).
3. Xác định project root.
4. Kiểm tra `.agent/`.
5. Nếu `.agent/` chưa tồn tại, thực hiện bootstrap.
6. Đọc cấu hình riêng của project trong `.agent/`.
7. Tuân thủ rules và workflows của Agent Kit.
8. Không tự ý thay đổi các quy định Core.

## Priority

Canonical hierarchy: [`rules/priority.md`](rules/priority.md). Agent không định nghĩa hierarchy riêng.

## Collaboration

Orchestrator route theo **minimum necessary workflow**. Chi tiết route: `workflows/`. Contract dùng chung: `rules/`.

| Agent | Câu hỏi | Decision |
|---|---|---|
| BA | Business cần gì? | READY / NEEDS_CLARIFICATION |
| Architect | Thiết kế thế nào? | READY / BLOCKED |
| Developer | Implement ra sao? | COMPLETE / BLOCKED |
| Tester | Behavior có đúng không? | PASS / FAIL / BLOCKED |
| Reviewer | Change có đúng và an toàn không? | APPROVE / REQUEST_CHANGES / BLOCKED |
| Deploy | Có thể release thế nào? | SUCCESS / FAILED / BLOCKED |
| Orchestrator | Ai hành động tiếp? | route + lifecycle state |

Mode (`automatic` / `semi-auto` / `manual`) chỉ đổi **ai quyết định bước tiếp**, không đổi responsibility. Mặc định khuyến nghị: `semi-auto`.

## Catalog

Mẫu dùng chung: `catalog/` (`projects`, `modules`, `components`, `functions`). Danh tính đã chốt của từng project: `.agent/CATALOG.md`. Task sau đối chiếu file đó và `.agent/requirements/`, không quét lại catalog.

## Project Setup

Thiết lập lúc bắt đầu: [`rules/project-setup.md`](rules/project-setup.md). Mục cơ bản phải đủ. Mục chưa ảnh hưởng bước hiện tại thì bổ sung khi bước đó cần dữ liệu.

Nhận diện: [`rules/brand.md`](rules/brand.md). Bộ mặc định khi project chưa có hoặc còn thiếu: `catalog/brand/default`.

## Orchestrator Agent

Path: `agents/orchestrator/AGENT.md`

**Role:** Shared Coordination Agent — phân loại task, chọn workflow ngắn nhất an toàn, delegate Agent, quản lý state, Quality Gate, failure loop và completion.

Orchestrator dùng **minimum necessary workflow** — không bắt buộc mọi task qua toàn bộ pipeline.

Project-specific policy:

```text
.agent/orchestration/
```

## Business Analyst Agent

Path: `agents/ba/AGENT.md`

**Role:** Shared Requirement Analysis Agent — chuyển User Request thành requirement rõ ràng và testable.

BA chịu trách nhiệm: Intent · Scope · Business Rules · Functional Requirements · Acceptance Criteria · Business Ambiguity.

Project-specific context từ:

```text
.agent/requirements/
```

BA **không** tự quyết technical architecture. Không bắt buộc mọi task qua BA (fast path cho thay đổi nhỏ / requirement đã rõ).

## Architect Agent

Path: `agents/architect/AGENT.md`

**Role:** Shared Technical Architecture Agent — phân tích technical impact và thiết kế solution trước implementation khi cần.

Architect đọc:

```text
.agent/ARCHITECTURE.md
.agent/architecture/
```

Architect **không** thay thế Developer. Không bắt buộc mọi task qua Architect (fast path cho thay đổi nhỏ).

## Developer Agent

Path: `agents/developer/AGENT.md`

**Role:** Shared Implementation Agent — chuyển requirement thành implementation an toàn, tối thiểu và có thể kiểm thử.

Khi workflow cần viết/sửa code, Agent điều phối phải đọc `agents/developer/AGENT.md`.

Developer đọc project-specific rules từ:

```text
.agent/development/
```

Developer **không** tự thay: Tester · Reviewer · Deploy Agent.

## Tester Agent

Path: `agents/tester/AGENT.md`

**Role:** Shared Quality Assurance Agent — lập kế hoạch, thực hiện testing, regression và kết luận PASS / FAIL / BLOCKED.

Khi workflow cần kiểm thử, Agent điều phối phải đọc `agents/tester/AGENT.md`.

Tester Agent lấy cấu hình riêng của project từ:

```text
.agent/testing/
```

Không hard-code test command / URL / infra của project vào Shared Agent.

## Reviewer Agent

Path: `agents/reviewer/AGENT.md`

**Role:** Shared Code & Change Quality Agent — review implementation trước deployment.

Reviewer đánh giá: Correctness · Requirement compliance · Architecture · Security · Maintainability · Change scope · Test adequacy.

Quyết định: **APPROVE** | **REQUEST_CHANGES** | **BLOCKED**.

Project-specific review policy từ:

```text
.agent/review/
```

Không hard-code stack / project vào Shared Agent.

## Deploy Agent

Path: `agents/deploy/AGENT.md`

**Role:** Shared Agent chịu trách nhiệm chuẩn bị, thực hiện, xác minh và rollback deployment.

Khi workflow cần deployment, Agent điều phối phải đọc `agents/deploy/AGENT.md`.

Deploy Agent phải lấy cấu hình riêng của project từ:

```text
.agent/deploy/
```

Không được hard-code infrastructure của project vào Shared Agent.

Luồng chuẩn: `User → Orchestrator → (BA? → Architect? → Developer → Tester → Reviewer → Deploy?) → Done` — adaptive; không bắt buộc full pipeline.
