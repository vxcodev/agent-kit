# Approval

Ba loại không dùng chung một từ “approved”:

| Loại | Ai | Ví dụ |
|---|---|---|
| **Agent Decision** | Agent trong vai trò | Reviewer `APPROVE` |
| **Human Approval** | Người có quyền | `PRODUCTION_DEPLOY_APPROVED` |
| **Policy Approval** | Config project | `approval.production: required` |

Reviewer `APPROVE` không phải giấy phép deploy production.

Im lặng không phải approval. Gate bắt buộc → trạng thái `WAITING FOR APPROVAL` rồi dừng.

Gate thường gặp: production deploy, database migration, destructive operation, major architecture change, security boundary change.

Chi tiết cấm: `SECURITY.md`. Mode `automatic` không bỏ các gate này.
