# N01-Day178
# Hướng dẫn thực hành Ngày 18 – Human-Centered AI Design

## 1. Chuẩn bị và Định hình phạm vi
* [cite_start]**Lập nhóm và chọn đề tài:** Nhóm gồm 3 người hãy chọn một bối cảnh từ 4 hướng: AI Travel Planner, AI Personal Assistant for Students, AI Customer Support Agent, hoặc lấy một tính năng AI cụ thể từ dự án nhóm đang phát triển[cite: 38, 39, 40, 41, 42, 43].
* [cite_start]**Chọn "lát cắt" sản phẩm:** Hãy chọn một lát cắt tính năng cụ thể để thiết kế sâu, không chọn toàn bộ sản phẩm[cite: 50].
* [cite_start]**Chốt số lượng kịch bản:** Nhóm cần làm tối thiểu 5 kịch bản tổng cộng, bao gồm: 1 flow onboarding bắt buộc, ít nhất 2 kịch bản trong khi tương tác, và ít nhất 2 kịch bản về sai sót, không chắc chắn hoặc khôi phục[cite: 153, 154, 155, 156, 157].

## 2. Các bước thiết kế Prototype (Gợi ý trong 120 phút)
[cite_start]Làm trực tiếp trong công cụ prototype ngay từ đầu, không dành nửa buổi chỉ để viết tài liệu[cite: 419]. Lộ trình thực hiện như sau:
* [cite_start]**Giai đoạn 0 (10 phút):** Chọn track, lát cắt và các kịch bản để tạo ra bản đồ phạm vi và danh sách flow[cite: 420].
* [cite_start]**Giai đoạn 1 (10 phút):** Nối vòng đời trải nghiệm để tạo sơ đồ liền mạch: Onboarding -> During -> After -> Feedback[cite: 420].
* [cite_start]**Giai đoạn 2 (15 phút):** Thiết kế Onboarding, bao gồm màn hình đầu, kỳ vọng, dữ liệu và quyền[cite: 420].
* [cite_start]**Giai đoạn 3 (20 phút):** Thiết kế luồng chính cộng với việc xác định ranh giới tự chủ (Agency) cho AI ở ba mức: Act, Ask, và Don't Act[cite: 420].
* [cite_start]**Giai đoạn 4 (30 phút):** Thiết kế nhánh xử lý sai sót và khôi phục (cần có ít nhất hai nhánh failure/recovery)[cite: 420].
* [cite_start]**Giai đoạn 5 (20 phút):** Thiết kế vòng phản hồi hai chiều, đảm bảo có đủ ma trận 2x2 cộng với vòng feedback hoàn chỉnh[cite: 420].
* [cite_start]**Giai đoạn 6 (15 phút):** Nối prototype, thêm các thẻ chú thích (design rationale) và tập demo sao cho có thể chạy mượt trong 5 phút[cite: 420].

## 3. Đóng gói và Nộp bài
* [cite_start]**Tạo Repository:** Tạo repository và đặt tên theo đúng cấu trúc: `Day18-Track1-MãHV-Họ Và Tên` (thay MãHV và Họ Và Tên bằng thông tin của người nộp bài)[cite: 4, 5, 6].
* [cite_start]**Kiểm tra đầu ra:** Những gì nhóm cần nộp cuối cùng bao gồm 4 yếu tố[cite: 438]:
    * [cite_start]Một liên kết prototype đã cấp quyền xem[cite: 439].
    * [cite_start]Một flow map trực quan nằm trong cùng tệp prototype[cite: 440].
    * [cite_start]Các thẻ design rationale đặt cạnh những flow quan trọng[cite: 441].
    * [cite_start]Một demo path giúp giảng viên chạy đúng các nhánh trong 5 phút[cite: 442].