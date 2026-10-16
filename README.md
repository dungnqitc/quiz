# Quiz Toán 5 & Tiếng Việt 5

Ứng dụng quiz web tĩnh (HTML + CSS + JS thuần), không cần backend, không cần cài đặt.

## Cấu trúc nhiều trang

- `index.html`: trang chủ, chọn bộ đề.
- `quiz-lop5.html`: Toán 5 & Tiếng Việt 5 (SGK Tập 1) — câu hỏi sinh ngẫu nhiên theo chủ đề.
- `quiz-lop5-tap2.html`: Toán 5 & Tiếng Việt 5 (SGK Tập 2) — câu hỏi sinh ngẫu nhiên, 2 engine (Toán 6 chủ đề, Tiếng Việt 4 chủ điểm) nhúng sẵn.
- `quiz-tienganh5.html`: Tiếng Anh 5 – Global Success: Tập 1 — ngữ pháp theo unit, quiz từ vựng (Anh↔Việt) và quiz ngữ pháp. Dữ liệu nhúng sẵn trong trang.
- `quiz-lop8.html`: Toán 8 – Tập 1 — ngân hàng 500 câu tĩnh (5 chương, mỗi chương 100 câu), dữ liệu nhúng sẵn trong trang.
- `quiz-anh6.html`: Tiếng Anh vào 6 CLC Thanh Xuân — 43 câu, 9 chủ đề, dữ liệu nhúng sẵn trong trang.
- `quiz-toan6cg.html`: Ôn thi Toán 6 – Cầu Giấy — 3 phần (Kiến thức, 12 câu trắc nghiệm có chấm điểm, 12 bài tự luận kèm lời giải). Dữ liệu nhúng sẵn trong trang.
- `quiz-khtn8.html`: KHTN 8 – SGK — 300 câu, 3 phân môn (Hóa, Lí, Sinh), mỗi phân môn 100 câu. Dữ liệu nhúng sẵn trong trang.
- `quiz-toan6tx.html`: Ôn thi Toán 6 – Thanh Xuân — 3 phần (Kiến thức, 8 câu trắc nghiệm có chấm điểm, 6 bài tự luận kèm lời giải). Dữ liệu nhúng sẵn trong trang.

Mỗi trang quiz có nút quay về trang chủ và lưu lịch sử riêng.

## Hai chế độ

- Quiz tổng hợp: 15 câu ngẫu nhiên lấy từ toàn bộ kho câu hỏi của bộ đề.
- Quiz theo chủ đề: 20 câu ngẫu nhiên lấy từ bộ câu hỏi của chủ đề/chương/phân môn được chọn.

Áp dụng cho các trang có 2 chế độ: Toán 5 & Tiếng Việt 5, Toán 8, KHTN 8, Tiếng Anh vào 6. Hai trang Cầu Giấy và Thanh Xuân là tài liệu ôn thi (Kiến thức + Trắc nghiệm + Tự luận) nên không áp dụng.

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
├── quiz-tienganh8.html     # Tiếng Anh 8 Global Success (ôn ngữ pháp + quiz từ vựng + quiz ngữ pháp)
├── quiz-toan6tx.html       # Ôn thi Toán 6 Thanh Xuân (kiến thức + trắc nghiệm + tự luận)
├── quiz-tienganh5.html     # Tiếng Anh 5 Global Success Tập 1 (ngữ pháp + quiz từ vựng + quiz ngữ pháp)
├── quiz-lop5-tap2.html     # Toán 5 & Tiếng Việt 5 SGK Tập 2 (sinh câu động, 2 chế độ)
├── relax-video.html        # Trang nhúng playlist YouTube (mục Relax)
├── history.html            # Tổng hợp lịch sử làm bài của mọi bộ đề
├── README.md
├── .gitignore
└── .github/
    └── workflows/
        └── deploy.yml      # Tự động deploy lên GitHub Pages khi push main
```
