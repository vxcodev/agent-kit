# Brand

Trước khi làm UI hoặc ảnh, project phải có bộ nhận diện. File của project: `.agent/BRAND.md`.

Bộ riêng thiếu mục nào thì lấy mục đó từ `catalog/brand/default`. Không tự đặt màu, logo, tỷ lệ mới.

## Trạng thái

| Status | Nghĩa |
|---|---|
| `DEFAULT` | Cả bộ lấy từ `catalog/brand/default` |
| `MIXED` | Mục project khai báo thì dùng; mục trống lấy từ default |
| `PROJECT` | Đủ logo, màu, banner, tỷ lệ, kích thước ảnh. Không đọc default |

Chưa có file, hoặc chưa chọn: ghi `DEFAULT` và tiếp tục. Không chặn dự án để đợi logo nếu Human chưa có file.

Khi Human đưa logo hoặc bảng màu sau: đổi mục tương ứng sang giá trị project, đổi status thành `MIXED` hoặc `PROJECT`. Không sửa `catalog/brand/default` từ project.

## Mục bắt buộc trong bộ

- Logo: mark, wordmark, lockup ngang, lockup dọc
- Màu: nền, chữ, chữ phụ, viền, accent, accent chữ
- Banner: các khổ ở dưới
- Tỷ lệ và kích thước ảnh chuẩn
- Vùng an toàn logo và kích thước nhỏ nhất

## Logo

- File vector (SVG) là bản gốc. PNG chỉ để chỗ không nhận SVG, đủ `@1x` và `@2x`.
- Không kéo giãn, không xoay, không thêm bóng, không đổi màu ngoài bảng màu.
- Vùng an toàn mỗi phía bằng chiều cao của mark.
- Mark trên màn hình không nhỏ hơn 24px cạnh. Lockup ngang không nhỏ hơn 120px rộng.
- Nền ảnh logo trong suốt. Không đặt logo lên ảnh rối nếu độ tương phản chữ dưới 4.5:1.

## Màu

Chỉ dùng token trong `BRAND.md`. Không thêm hex trong component nếu token đã có.

Chữ trên nền thường và chữ trên accent phải đọc được (tương phản tối thiểu 4.5:1 với chữ nhỏ).

## Banner

| Khổ | Tỷ lệ | Pixel chuẩn |
|---|---|---|
| Hero | 16:9 | 1920×1080 |
| Cover | 3:1 | 1500×500 |
| Social | 1.91:1 | 1200×628 |
| Story | 9:16 | 1080×1920 |

Vùng chữ và logo nằm trong 80% giữa khung. Không đặt thông tin sát mép dưới 48px với hero và story.

## Ảnh nội dung

| Vai trò | Tỷ lệ | Cạnh dài tối đa |
|---|---|---|
| Thumb | 1:1 | 400 |
| Card | 4:3 | 800×600 |
| Content | 16:9 | 1280×720 |
| Ảnh đầy | giữ tỷ lệ gốc | 1920 |

Không phóng ảnh nhỏ hơn kích thước hiển thị. Ảnh nặng cắt về cạnh dài 1920 trước khi đưa vào repo. Định dạng ảnh chụp: WebP hoặc JPEG. Icon và logo: SVG hoặc PNG.

## Khi làm việc

Developer và Reviewer đọc `.agent/BRAND.md` trước khi thêm UI hoặc ảnh. Sai token, sai tỷ lệ banner, hoặc logo bị biến dạng → sửa cho khớp bộ đang ghi, không nới quy tắc trong lúc làm task.

Ảnh sẵn của bộ default nằm ở `catalog/brand/default/images/`, tạo bằng [placehold.co](https://placehold.co/) theo token màu và nhãn ngắn (`HERO`, `M`, `LOCK-H`, …).
