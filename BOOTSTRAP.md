# Project Bootstrap

Khi Agent bắt đầu làm việc với một project.

## 1. Find Project Root

Xác định thư mục root của project (thư mục chứa `.git` của **host**, không phải `agent-kit/`).

## 2. Check Project Agent Configuration

Kiểm tra thư mục:

```text
.agent/
```

Nếu **đã tồn tại**:

- Không tạo lại.
- Không ghi đè.
- Đọc cấu hình hiện tại.

Nếu **chưa tồn tại**:

- Khởi tạo từ `agent-kit/templates/project/`.

## 3. Initialize

Tạo cấu trúc:

```text
.agent/
├── config.yaml
├── PROJECT.md
├── USER.md
├── ARCHITECTURE.md
├── MEMORY.md
├── STATE.md
├── tasks/
├── decisions/              # ADR — giữ nguyên nếu đã có
├── reports/
├── deploy/                 # nếu chưa có — xem §3.1
│   ├── DEPLOY.md
│   └── environments.yaml
├── testing/                # nếu chưa có — xem §3.2
│   ├── TESTING.md
│   └── config.yaml
├── review/                 # nếu chưa có — xem §3.3
│   ├── REVIEW.md
│   └── config.yaml
├── development/            # nếu chưa có — xem §3.4
│   ├── DEVELOPMENT.md
│   └── config.yaml
├── architecture/           # nếu chưa có — xem §3.5
│   ├── ARCHITECTURE_RULES.md
│   └── config.yaml
├── requirements/           # nếu chưa có — xem §3.6
│   ├── REQUIREMENTS.md
│   └── config.yaml
├── orchestration/          # nếu chưa có — xem §3.7
│   ├── ORCHESTRATION.md
│   └── config.yaml
├── lessons/                # nếu chưa có — xem §3.8
│   └── README.md
├── CATALOG.md              # nếu chưa có — xem §3.9
└── BRAND.md                # nếu chưa có — xem §3.10
```

### 3.1. Deployment configuration

```text
.agent/deploy exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/deploy/
```

- Nếu `.agent/deploy/` **chưa** tồn tại: copy từ `agent-kit/templates/project/deploy/`.
- Nếu **đã** tồn tại: **không** ghi đè.

### 3.2. Testing configuration

```text
.agent/testing exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/testing/
```

- Nếu `.agent/testing/` **chưa** tồn tại: copy từ `agent-kit/templates/project/testing/` (`TESTING.md`, `config.yaml`).
- Nếu **đã** tồn tại: **không** ghi đè.

### 3.3. Review configuration

```text
.agent/review exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/review/
```

- Nếu `.agent/review/` **chưa** tồn tại: copy từ `agent-kit/templates/project/review/` (`REVIEW.md`, `config.yaml`).
- Nếu **đã** tồn tại: **không** ghi đè.

### 3.4. Development configuration

```text
.agent/development exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/development/
```

- Nếu `.agent/development/` **chưa** tồn tại: copy từ `agent-kit/templates/project/development/` (`DEVELOPMENT.md`, `config.yaml`).
- Nếu **đã** tồn tại: **không** ghi đè.

### 3.5. Architecture configuration

```text
.agent/architecture exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/architecture/
```

- Nếu `.agent/architecture/` **chưa** tồn tại: copy từ `agent-kit/templates/project/architecture/` (`ARCHITECTURE_RULES.md`, `config.yaml`).
- Nếu **đã** tồn tại: **không** ghi đè.
- Đảm bảo `.agent/decisions/` tồn tại (tạo trống nếu chưa có); **không** xóa ADR cũ.
- `.agent/ARCHITECTURE.md` (trạng thái kiến trúc hiện tại) khác với `.agent/architecture/` (rules) — không gộp / ghi đè lẫn nhau.

### 3.6. Requirements configuration

```text
.agent/requirements exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/requirements/
```

- Nếu `.agent/requirements/` **chưa** tồn tại: copy từ `agent-kit/templates/project/requirements/` (`REQUIREMENTS.md`, `config.yaml`).
- Nếu **đã** tồn tại: **không** ghi đè.
- Không reset business knowledge của project khi Agent Kit update.
- Task cụ thể dùng `.agent/tasks/` (hoặc convention hiện có) — không tạo hệ thống task thứ hai.

### 3.7. Orchestration configuration

```text
.agent/orchestration exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/orchestration/
```

- Nếu `.agent/orchestration/` **chưa** tồn tại: copy từ `agent-kit/templates/project/orchestration/` (`ORCHESTRATION.md`, `config.yaml`).
- Nếu **đã** tồn tại: **không** ghi đè.
- Không reset workflow policy của project khi Agent Kit update.

### 3.8. Lessons

```text
.agent/lessons exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/lessons/
```

- Nếu `.agent/lessons/` **chưa** tồn tại: copy từ `agent-kit/templates/project/lessons/`.
- Nếu **đã** tồn tại: **không** ghi đè, **không** xóa lesson cũ.
- Lesson là project knowledge. Promote lên Core hoặc `catalog/` chỉ qua `workflows/distill.md` + Human approval.

### 3.9. Catalog binding

```text
.agent/CATALOG.md exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/CATALOG.md
```

- Nếu chưa có: copy `templates/project/CATALOG.md` (`Status: UNCONFIRMED`).
- Nếu đã có, kể cả `CONFIRMED` hoặc `NONE`: **không** ghi đè, **không** nâng version theo catalog kit.

### 3.10. Brand

```text
.agent/BRAND.md exists?
       │
   ┌───┴───┐
   NO      YES
   ↓        ↓
CREATE     KEEP
from       DO NOT OVERWRITE
templates/project/BRAND.md
```

- Nếu chưa có: copy `templates/project/BRAND.md` (`Status: DEFAULT`).
- Nếu đã có: **không** ghi đè.
- Mục trống trong bộ `MIXED` lấy từ `catalog/brand/default`. Chi tiết: `rules/brand.md`.

`templates/project/` vẫn chỉ là khung `.agent/`. Project mẫu nghiệp vụ nằm ở `catalog/projects/`.

Contract cross-cutting (không copy vào Bootstrap): `rules/priority.md`, `rules/project-setup.md`, `rules/task-lifecycle.md`, `rules/state-management.md`, `rules/handoff.md`, `rules/approval.md`, `rules/risk.md`, `rules/knowledge-management.md`. Security: `SECURITY.md`. Workflow: `workflows/`.

## 4. Analyze Project

Agent được phép phân tích source code để điền các thông tin có thể xác định chắc chắn.

Không được tự suy đoán thông tin business chưa biết.

Thiết lập lúc mở project: `rules/project-setup.md`. Phần cơ bản phải đủ trước khi làm việc. Phần chưa đụng tới thì ghi "bổ sung khi" và điền ở bước cần dữ liệu đó.

## 5. GitHub

Xác định và ghi nhận remote GitHub của **project host** (không nhầm với remote của `agent-kit`).

1. Chạy trong project root:

   ```bash
   git remote -v
   git branch -vv
   git status
   ```

2. Ghi vào `.agent/PROJECT.md` (hoặc `config.yaml`):

   - Remote URL (vd. `https://github.com/<org>/<repo>.git`)
   - Default branch (`main` / `master`)
   - Branch hiện tại + tracking

3. Quy tắc làm việc với GitHub:

   - Pull/push **host** chỉ trong root host; pull/push **agent-kit** chỉ trong `agent-kit/`.
   - Không force-push `main`/`master` trừ khi Sếp yêu cầu rõ.
   - Không commit secret (`.env`, API key, token).
   - Trước khi push: `git status` + xem diff; không push file không liên quan task.
   - Prefer `gh` cho PR/issue khi đã cài và đã đăng nhập; nếu không có `gh`, dùng remote HTTPS/SSH như cấu hình sẵn.
   - Không đổi `git config` global/user trên máy trừ khi Sếp yêu cầu.

4. Nếu project **chưa có** remote GitHub:

   - Ghi chú trong `.agent/STATE.md`.
   - Không tự tạo repo / tự `git remote add` trừ khi Sếp chỉ định URL.

## 6. Continue

Sau khi bootstrap hoàn thành:

1. Load `PROJECT.md`
2. Load `ARCHITECTURE.md`
3. Load `MEMORY.md`
4. Load `STATE.md`
5. Chọn workflow phù hợp
6. Thực hiện task
