# Brand — default

Bộ trung tính của Agent Kit. Dùng khi project chưa có nhận diện, hoặc để điền mục project để trống. Không phải logo của một khách hàng.

## Logo

Ảnh tạo từ [placehold.co](https://placehold.co/). Nền `color.paper` hoặc `color.accent`, chữ `color.ink` hoặc `color.on-accent`. Nhãn viết tắt.

| Slot | File | @2x | Khổ |
|---|---|---|---|
| Mark | `images/mark.png` | `images/mark@2x.png` | 64×64, nhãn `M` |
| Wordmark | `images/word.png` | `images/word@2x.png` | 320×64, nhãn `WORD` |
| Lockup ngang | `images/lock-h.png` | `images/lock-h@2x.png` | 320×64, nhãn `LOCK-H` |
| Lockup dọc | `images/lock-v.png` | `images/lock-v@2x.png` | 160×200, nhãn `LOCK-V` |

Mark tối thiểu khi dùng thật vẫn là 24px. Lockup ngang tối thiểu 120px rộng. Vùng an toàn mỗi phía = chiều cao mark.

Khi project có SVG riêng, thay cả bốn slot và ghi vào `.agent/BRAND.md`. Không trộn mark default với wordmark của khách.

## Màu

| Token | Hex | Việc |
|---|---|---|
| `color.paper` | `#FFFFFF` | Nền |
| `color.ink` | `#1A1A1A` | Chữ chính |
| `color.muted` | `#5C6570` | Chữ phụ |
| `color.line` | `#E4E7EB` | Viền, gạch |
| `color.accent` | `#1F4B99` | Nút, mark, điểm nhấn |
| `color.on-accent` | `#FFFFFF` | Chữ trên accent |

Không thêm màu ngoài bảng này khi đang ở status `DEFAULT`.

## Banner

| Khổ | Tỷ lệ | Pixel | File | Nhãn |
|---|---|---|---|---|
| Hero | 16:9 | 1920×1080 | `images/hero.png` | `HERO` |
| Cover | 3:1 | 1500×500 | `images/cover.png` | `COVER` |
| Social | 1.91:1 | 1200×628 | `images/social.png` | `SOCIAL` |
| Story | 9:16 | 1080×1920 | `images/story.png` | `STORY` |

Nền banner mặc định: `color.paper`. Chữ: `color.ink`. Dải accent cao 8px sát cạnh trên. Logo trong vùng 80% giữa, cách mép dưới ít nhất 48px với hero và story.

## Ảnh

| Vai trò | Tỷ lệ | Kích thước | File | Nhãn |
|---|---|---|---|---|
| Thumb | 1:1 | 400×400 | `images/thumb.png` | `THUMB` |
| Card | 4:3 | 800×600 | `images/card.png` | `CARD` |
| Content | 16:9 | 1280×720 | `images/content.png` | `CONTENT` |
| Đầy | 3:2 | 1920×1280 | `images/full.png` | `FULL` |

Ảnh chụp: WebP hoặc JPEG. Logo và icon: SVG, hoặc PNG trong suốt `@1x` `@2x`.
