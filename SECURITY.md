# SECURITY

## Cấm

- Commit / log / dexuat chứa **API key, bot token, mật khẩu, private key**.  
- Push secret lên `agent-kit` hoặc host.  
- Chạy lệnh phá hủy prod khi chưa được Sếp xác nhận rõ.

## Nên

- Secret chỉ trên host (`~/.…/secrets`, `.env` gitignore).  
- Dexuat ghi **path** file secret, không ghi nội dung.  
- Review diff trước push kit (tránh lỡ dán key vào markdown).

## Repo public

`agent-kit` có thể public — coi mọi file trong kit là **không chứa secret**.
