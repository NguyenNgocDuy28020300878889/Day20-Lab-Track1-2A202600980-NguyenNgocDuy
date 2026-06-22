# Kế Hoạch Thực Thi Thiết Kế Prototype: AI Smart Packing & Prep (120 Phút)

**Track:** AI Travel Planner
**Lát cắt:** Gợi ý hành trang theo thời tiết và hoạt động (Smart Packing & Prep).
[cite_start]**Tổng quan:** Thiết kế lát cắt xuyên suốt vòng đời: Onboarding -> Trong tương tác -> Sau tương tác -> Phản hồi & Khôi phục [cite: 99-106, 453].

---

## [cite_start]Giai đoạn 0: Bản đồ phạm vi (10 Phút) 
*Thao tác trên công cụ:* Mở một Frame riêng để liệt kê nhanh 5 kịch bản đã chốt để làm "kim chỉ nam".
* **Kịch bản 1 (Onboarding):** Thiết lập kỳ vọng và xin quyền truy cập thời tiết/lịch trình.
* **Kịch bản 2 (Tương tác - Ask):** Hỏi rõ mục đích chuyến đi khi dữ liệu đầu vào mơ hồ (ví dụ: chỉ nhập "Đà Lạt").
* **Kịch bản 3 (Tương tác - Explainability):** AI tự động tạo checklist (Act) và đưa ra lớp bằng chứng giải thích lý do chọn món đồ.
* **Kịch bản 4 (Sai sót - Recovery):** AI gợi ý sai "Đồ bơi" do hiểu nhầm bối cảnh. Người dùng xóa, AI cập nhật lại.
* **Kịch bản 5 (Agency - Don't Act):** Phát hiện thiếu sạc dự phòng, AI đề xuất link mua (Ask/Don't Act) thay vì tự mua.

---

## [cite_start]Giai đoạn 1: Nối vòng đời trải nghiệm - Flow Map (10 Phút) 
[cite_start]*Thao tác trên công cụ:* Dùng công cụ vẽ Flowchart vẽ các khối (Node) nối tiếp nhau đại diện cho hành trình[cite: 440].
* `Start` -> `Onboarding Screen` -> `Nhập điểm đến/Thời gian` -> `AI Phân tích (Loading)`.
* Từ `AI Phân tích` chia nhánh:
    * **Nhánh 1 (Thiếu dữ kiện):** -> `AI Hỏi thêm mục đích` -> `Người dùng trả lời` -> `Kết quả Checklist`.
    * **Nhánh 2 (Đủ dữ kiện):** -> `Kết quả Checklist` (kèm lớp Explainability).
* Từ `Kết quả Checklist` chia nhánh khôi phục:
    * **Nhánh Lỗi 1:** -> `Người dùng xóa đồ sai` -> `Hệ thống xác nhận đã hiểu & Xóa`.
    * **Nhánh Mua sắm:** -> `AI gợi ý mua đồ` -> `Người dùng từ chối (chọn "Đã có")` -> `Hệ thống cập nhật trạng thái`.
* Hội tụ lại -> `Lưu hành trang (Hoàn thành)`.

---

## [cite_start]Giai đoạn 2: Thiết kế Onboarding (15 Phút) 
[cite_start]*Mục tiêu:* Giúp người dùng hiểu AI hỗ trợ gì, không thể làm gì, cần quyền gì [cite: 111-114].
*Thao tác vẽ Màn hình (UI):*
* **Màn hình 1 (Welcome):** * *Copy:* "Trợ lý Hành trang thông minh. Tôi phân tích thời tiết và lịch trình để gợi ý đồ dùng."
    * *Ranh giới:* "Tôi có thể gợi ý đồ, nhưng bạn là người quyết định cuối cùng."
* **Màn hình 2 (Permissions):**
    * *UI:* 2 toggle switch cho "Truy cập Dự báo thời tiết" và "Đọc lịch trình chuyến đi".
    * *Nút bấm:* "Bắt đầu chuyến đi".
* **Màn hình 3 (Input):**
    * *UI:* Form nhập "Điểm đến" và "Ngày đi". Nút "Tạo Checklist".

---

## [cite_start]Giai đoạn 3: Luồng chính & Agency (20 Phút) 
[cite_start]*Mục tiêu:* Thể hiện rõ 3 mức độ tự chủ của AI (Act, Ask, Don't Act) [cite: 194-198].
*Thao tác vẽ Màn hình (UI):*
* **Màn hình 4 (AI Processing - Tương tác):** * *UI:* Màn hình chat/popup nổi lên. AI hỏi: "Đà Lạt mùa này có nhiều lựa chọn, bạn dự định đi Trekking hay Nghỉ dưỡng?". [cite_start](Mức độ: **Ask** vì thiếu bối cảnh [cite: 32]).
* **Màn hình 5 (Checklist Result - Act & Explainability):** * *UI:* Danh sách đồ dùng được chia nhóm (Quần áo, Thiết bị, Y tế). AI tự điền các món cơ bản (Mức độ: **Act** vì rủi ro thấp [cite: 198]).
    * *UI (Lớp bằng chứng):* Cạnh item "Áo khoác gió", làm một icon (i). [cite_start]Bấm vào hiện Tooltip: "Dự báo Đà Lạt có mưa 80% và lạnh 15 độ vào ngày thứ 2" [cite: 246-248].

---

## [cite_start]Giai đoạn 4: Thiết kế Sai sót & Khôi phục (30 Phút) 
[cite_start]*Mục tiêu:* Xử lý khi AI sai hoặc không chắc chắn, không chỉ có nút "báo lỗi" mà phải có đường đi tiếp[cite: 137].
*Thao tác vẽ Màn hình (UI):*
* **Màn hình 6 (Khôi phục lỗi ngữ cảnh):**
    * *Sự cố:* AI gợi ý "Đồ bơi".
    * *UI Thao tác:* Người dùng quẹt trái/bấm icon Thùng rác để xóa. Hệ thống hiện bảng chọn lý do: "Không có nhu cầu / Đi công tác".
    * [cite_start]*UI Khôi phục:* Toast message hiện lên: "Đã ghi nhớ bối cảnh công tác. Đã xóa đồ bơi." [cite: 142-150].
* **Màn hình 7 (Khôi phục đề xuất - Agency rủi ro cao):**
    * *Sự cố:* AI thấy thiếu "Sạc dự phòng".
    * *UI Thao tác:* Hiện thẻ "Gợi ý mua sắm sạc dự phòng - 200k" kèm nút "Mua ngay" và nút "Tôi đã có". [cite_start](Mức độ: **Don't Act tự mua / Ask xin phép** vì liên quan tiền bạc [cite: 198]).
    * *UI Khôi phục:* Người dùng bấm "Tôi đã có". Thẻ gợi ý biến mất, checklist tick xanh món đồ đó.

---

## [cite_start]Giai đoạn 5: Vòng Feedback hai chiều (20 Phút) 
*Mục tiêu:* Hoàn thiện ma trận 2x2. [cite_start]Rà soát lại các màn hình đã vẽ để gắn thẻ chú thích [cite: 206-207].
*Thao tác trên công cụ:* Kéo các thẻ Tag (màu sắc nổi bật) đặt cạnh các UI tương ứng:
* [cite_start]**Tag: User Explicit Feedback:** Trỏ vào nút "Xóa đồ bơi" và việc chọn lý do "Đi công tác"[cite: 207].
* [cite_start]**Tag: User Implicit Feedback:** Trỏ vào thời gian người dùng dừng lại đọc tooltip thời tiết, hoặc hành động bỏ qua không bấm vào link mua sạc dự phòng[cite: 207].
* [cite_start]**Tag: System Explicit Feedback:** Trỏ vào Toast message "Đã ghi nhớ bối cảnh công tác"[cite: 207].
* [cite_start]**Tag: System Implicit Feedback:** Trỏ vào UI checklist, nơi món đồ quan trọng (Áo khoác gió) được in đậm và đẩy lên đầu danh sách dựa theo thời tiết[cite: 207].

---

## [cite_start]Giai đoạn 6: Nối Prototype, Rationale và Demo (15 Phút) 
[cite_start]*Mục tiêu:* Chạy thử và chốt hạ tệp nộp bài [cite: 439-442].
*Thao tác:*
1.  [cite_start]**Nối tương tác (Prototyping):** Nối các nút bấm để tạo thành luồng có thể Click được từ màn 1 đến màn 7[cite: 81].
2.  **Gắn thẻ Rationale (Bắt buộc):** Tạo các khung chú thích ngắn đặt ngay cạnh các cụm màn hình, trả lời các câu hỏi: AI đang biết gì? AI chưa biết gì? Vì sao AI được Act/Ask? [cite_start]Rủi ro nếu AI sai là gì? [cite: 176-187].
    * [cite_start]*Ví dụ Rationale chỗ đề xuất mua sắm:* "Chi phí sai sót (mua nhầm) là mất tiền, rủi ro cao và khó hoàn tác. Vì vậy AI tuyệt đối không tự mua (Don't Act) mà phải hỏi ý kiến người dùng (Ask)" [cite: 190-192].
3.  [cite_start]**Soạn Demo Path:** Lên kịch bản nói 5 phút theo cấu trúc: Giới thiệu lát cắt -> Trình bày Flow Onboarding -> Demo luồng chính có bằng chứng thời tiết -> Demo tính năng tự động khôi phục khi xóa đồ -> Tổng kết Rationale[cite: 436].