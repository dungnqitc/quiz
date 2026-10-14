# Quiz Toán 5 & Tiếng Việt 5

Ứng dụng quiz web tĩnh (HTML + CSS + JS thuần), không cần backend, không cần cài đặt.

## Cấu trúc nhiều trang

- `index.html`: trang chủ, chọn bộ đề.
- `quiz-lop5.html`: Toán 5 & Tiếng Việt 5 — câu hỏi sinh ngẫu nhiên theo chủ đề.
- `quiz-lop8.html`: Toán 8 – Tập 1 — ngân hàng 500 câu tĩnh (5 chương, mỗi chương 100 câu), dữ liệu nhúng sẵn trong trang.
- `quiz-anh6.html`: Tiếng Anh vào 6 CLC Thanh Xuân — 43 câu, 9 chủ đề, dữ liệu nhúng sẵn trong trang.
- `quiz-toan6cg.html`: Ôn thi Toán 6 – Cầu Giấy — 3 phần (Kiến thức, 12 câu trắc nghiệm có chấm điểm, 12 bài tự luận kèm lời giải). Dữ liệu nhúng sẵn trong trang.
- `quiz-khtn8.html`: KHTN 8 – SGK — 300 câu, 3 phân môn (Hóa, Lí, Sinh), mỗi phân môn 100 câu. Dữ liệu nhúng sẵn trong trang.
- `quiz-toan6tx.html`: Ôn thi Toán 6 – Thanh Xuân — 3 phần (Kiến thức, 8 câu trắc nghiệm có chấm điểm, 6 bài tự luận kèm lời giải). Dữ liệu nhúng sẵn trong trang.

Mỗi trang quiz có nút quay về trang chủ và lưu lịch sử riêng.

## Hai chế độ

- Quiz tổng hợp:
  - Toán 5 & Tiếng Việt 5: chọn môn (Toán hoặc Tiếng Việt), mỗi môn một bộ 20 câu ngẫu nhiên.
  - Toán 8: một bộ 20 câu ngẫu nhiên lấy từ toàn bộ 500 câu của cả 5 chương.
- Quiz theo chủ đề:
  - Toán 5 & Tiếng Việt 5: chọn môn rồi chọn chủ đề, mỗi bộ 100 câu ngẫu nhiên.
  - Toán 8: chọn 1 trong 5 chương, làm trọn 100 câu của chương đó.

## Tính năng

- Sinh câu hỏi ngẫu nhiên (không trùng trong một bộ)
- Chọn đáp án, chấm điểm ngay, hiển thị giải thích
- Ôn lại các câu đã làm sai
- Lưu lịch sử làm bài trên trình duyệt (thời gian, môn + chủ điểm, điểm)
- Giao diện responsive, hỗ trợ chế độ tối (dark mode) theo hệ thống

## Lịch sử làm bài

Lịch sử được lưu bằng `localStorage` của trình duyệt (khóa `quiz5_history_v1`).

- Dữ liệu chỉ nằm trên máy/trình duyệt đang dùng, không gửi đi đâu, không cần đăng nhập.
- Mỗi lần hoàn thành một bộ quiz sẽ thêm một bản ghi: thời gian, môn, chủ điểm, điểm.
- Xem lịch sử ở màn hình kết quả; có nút "Xóa toàn bộ lịch sử".
- Xóa cache/dữ liệu trình duyệt hoặc dùng máy khác sẽ không còn lịch sử cũ.

Lưu ý: vì chạy hoàn toàn phía client, ứng dụng phù hợp cho mục đích học tập/ôn luyện, không dùng cho thi cử cần chống gian lận.

## Chạy thử tại máy

Chỉ cần mở `index.html` bằng trình duyệt. Hoặc chạy một web server tĩnh:

```bash
# Python 3
python -m http.server 8000
# rồi mở http://localhost:8000
```

## Đưa lên GitHub và bật GitHub Pages

### 1. Tạo repo và đẩy code

```bash
git init
git add .
git commit -m "Khởi tạo quiz app"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

### 2. Bật GitHub Pages

Có hai cách, chọn một.

Cách A — Deploy từ nhánh (đơn giản nhất):

1. Vào repo trên GitHub > Settings > Pages
2. Mục "Build and deployment" > Source: chọn "Deploy from a branch"
3. Branch: chọn `main`, thư mục `/ (root)` > Save
4. Chờ 1–2 phút, trang sẽ chạy tại `https://<username>.github.io/<repo>/`

Cách B — Dùng GitHub Actions (đã kèm sẵn workflow):

1. Vào Settings > Pages > Source: chọn "GitHub Actions"
2. Mỗi lần push lên `main`, workflow `.github/workflows/deploy.yml` sẽ tự deploy

## Cấu trúc thư mục

```
quiz-app/
├── index.html              # Trang chủ (chọn bộ đề)
├── quiz-lop5.html          # Quiz Toán 5 & Tiếng Việt 5
├── quiz-lop8.html          # Quiz Toán 8 (dữ liệu 500 câu nhúng sẵn)
├── quiz-anh6.html          # Quiz Tiếng Anh vào 6 (dữ liệu 43 câu nhúng sẵn)
├── quiz-toan6cg.html       # Ôn thi Toán 6 Cầu Giấy (kiến thức + trắc nghiệm + tự luận)
├── quiz-khtn8.html         # Quiz KHTN 8 (300 câu, 3 phân môn, nhúng sẵn)
├── quiz-toan6tx.html       # Ôn thi Toán 6 Thanh Xuân (kiến thức + trắc nghiệm + tự luận)
├── README.md
├── .gitignore
└── .github/
    └── workflows/
        └── deploy.yml      # Tự động deploy lên GitHub Pages khi push main
```
