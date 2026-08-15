# Topic-Sort · Hệ thống DDA

Web deck (một file HTML) trình bày hệ thống điều chỉnh độ khó động của Topic-Sort:
tổng quan trong game, yêu cầu, cơ chế xếp tier, vấn đề, rủi ro và lộ trình.

14 slide · khoảng 17 phút · phong cách Swiss International (Klein Blue IKB).

## Xem

Bản deploy: GitHub Pages của repo này (workflow `.github/workflows/static.yml` tự chạy khi push lên `main`).

Chạy tại máy: mở thẳng `index.html` bằng trình duyệt, không cần server.

## Điều khiển

| Phím | Tác dụng |
|---|---|
| `←` `→` | Lật trang (hoặc cuộn chuột / vuốt) |
| `ESC` | Xem tổng quan tất cả slide |
| `P` | Chế độ người trình bày: trang hiện tại + trang kế + ghi chú + đồng hồ |
| `B` | Tắt hiệu ứng nền, dùng khi máy chiếu yếu |

Trong chế độ người trình bày còn có: hẹn giờ từng trang, chế độ tập dượt, tự động lật trang,
bút laser (`L`), khoanh vùng (`C`), tắt màn hình khán giả (`B` / `W`), đóng băng (`F`).

## Cấu trúc

```
index.html            deck (toàn bộ CSS/JS nội tuyến)
assets/motion.min.js  thư viện hiệu ứng, bản dự phòng khi mất mạng
images/02-ingame.png  ảnh màn chơi dùng ở slide 02
```

Font Inter / JetBrains Mono và bộ icon tải từ CDN nên khi mất mạng chữ sẽ lùi về font hệ thống,
phần còn lại vẫn chạy bình thường.

## Sửa nội dung

Nội dung nằm ngay trong `index.html`:

- Mỗi trang là một `<section class="slide" data-layout="Sxx" data-slide-id="...">`
- Ghi chú người trình bày nằm ở mảng `SPEAKER_NOTES`, khớp theo `data-slide-id`
- Thay ảnh: ghi đè `images/02-ingame.png` giữ nguyên tên, không phải sửa HTML

Deck dựng bằng skill `guizang-ppt-skill` (phong cách B · Swiss International). Sau khi sửa nên chạy lại:

```bash
node <skill>/scripts/validate-presenter-mode.mjs index.html --target-minutes 17
node <skill>/scripts/validate-swiss-deck.mjs index.html
```
