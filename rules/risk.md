# Risk

Thang canonical, độc lập với complexity:

| Level | Nghĩa |
|---|---|
| **LOW** | Hỏng cũng giới hạn, dễ đảo, không đụng auth/data/prod |
| **MEDIUM** | Sai behavior cục bộ hoặc contract nội bộ |
| **HIGH** | Authz, data quan trọng, integration, migration, workflow user-facing lớn |
| **CRITICAL** | Security boundary, payment, phá data production, credential, core authz |

Complexity (`TRIVIAL`–`COMPLEX`) đo độ rộng việc. Risk đo hậu quả. Một diff nhỏ vẫn có thể CRITICAL.

Agent được thêm ví dụ theo vai trò. Không được đổi nghĩa bốn mức trên.
