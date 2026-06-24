# 📊 Báo Cáo Phân Tích Day 20: Retention, Engagement & Habit Loop
**Dự án:** AI Gợi ý hành trang theo thời tiết và hoạt động (Smart Packing & Prep)  
**Mã học viên:** 2A202600980 | **Học viên:** Nguyễn Ngọc Duy  

---

## 01. Customer Retention Canvas — Use Case

### 1.1. The Problem (Vấn đề từ góc nhìn người dùng)
*   **Mô tả:** "Tôi mất quá nhiều thời gian để tra cứu thời tiết tại điểm đến, tự lên danh sách đồ dùng cần mang theo lịch trình, rồi lại phải lo lắng xem hành lý có quá cân xách tay của hãng bay hay mang nhầm vật dụng cấm hay không. Đôi khi thời tiết thay đổi đột ngột làm tôi không kịp xoay xở và bị thiếu đồ giữ ấm/chống mưa."
*   *Lưu ý:* Không mô tả bằng tính năng của sản phẩm.

### 1.2. The Persona (Minh họa đối tượng)
*   **Persona:** Nguyễn Minh Anh (26 tuổi), Nhân viên văn phòng tại TP.HCM.
*   **Hoàn cảnh:** Thích du lịch tự túc cuối tuần và thỉnh thoảng đi công tác kết hợp trekking nhẹ (Đà Lạt, Fansipan, Cát Tiên).
*   **Mục tiêu:** Muốn chuẩn bị hành lý cực nhanh, tối giản dưới 7kg xách tay nhưng phải đảm bảo an toàn, đúng quy định bay và phù hợp với thời tiết thực tế tại điểm đến.
*   **Điều kiện thay đổi hành vi:** Khi hãng bay kiểm soát cân nặng gắt gao hoặc khi đi du lịch vào mùa thời tiết biến động thất thường.

### 1.3. Anti-persona (Đối tượng không nhắm tới)
*   Bà Trần Thị Mai (55 tuổi), đi du lịch nghỉ dưỡng trọn gói theo đoàn. Có xe đưa đón tận nơi, hướng dẫn viên chuẩn bị sẵn lịch trình và hành lý ký gửi thoải mái. Không có nhu cầu tự tối ưu checklist hay lo lắng thời tiết biến đổi đột ngột.

### 1.4. The Why (Động lực cốt lõi)
*   **Outcome mong muốn:** Đóng gói hành lý nhanh chóng dưới 5 phút, tránh mất tiền phạt quá cân tại sân bay và an tâm tuyệt đối vì hành trang đã được tối ưu hóa theo thời tiết thực tế và quy định an toàn bay.

### 1.5. The Alternative (Giải pháp thay thế hiện tại)
*   Ghi chép thủ công trên ứng dụng Notes điện thoại.
*   Dùng bảng Excel template chuẩn bị hành lý tự chế.
*   Hỏi thăm kinh nghiệm từ bạn bè hoặc các hội nhóm du lịch trên mạng xã hội.
*   Chấp nhận đóng đồ theo quán tính và mua bổ sung tại điểm đến nếu thiếu.

### 1.6. The Frequency (Tần suất xuất hiện tự nhiên)
*   **Tần suất:** **Monthly** (Trung bình 1-2 lần/tháng trước mỗi chuyến đi chơi hoặc đi công tác).

---

## 02. Core Action & Active User

### 2.1. Core Job
*   Chuẩn bị hành lý tối ưu và an toàn nhất cho chuyến đi dựa trên thời tiết và lịch trình hoạt động thực tế.

### 2.2. Core Action
*   Người dùng bấm **Xác nhận checklist cuối cùng** (để tải về, in ra hoặc đánh dấu hoàn tất việc kiểm tra đồ đạc). Hành động này chứng minh người dùng đã tìm thấy và chấp nhận giá trị gợi ý từ AI.

### 2.3. Định nghĩa Active User
*   Một người dùng được tính là **Active User** khi:
    *   **Thực hiện hành động:** Hoàn tất xác nhận ít nhất 1 checklist hành lý.
    *   **Khoảng thời gian:** Trong vòng 30 ngày (Monthly cadence).
    *   *Công thức:* Một user được tính là active khi *finalized_checklist* $\ge 1$ trong *30 ngày*.

---

## 03. Natural Frequency & Retention Metric

*   **Tần suất tự nhiên (Natural Frequency):** **Monthly** (Hàng tháng) phù hợp với hành vi du lịch/đi xa tự nhiên của persona.
*   **Retention Metric lựa chọn:** **Monthly Cohort Retention (Tỷ lệ duy trì theo tháng)**.
    *   *Công thức tính:* 
        $$\text{Month 1 Retention Rate} = \frac{\text{Số user trong Cohort tháng } N \text{ có } \ge 1 \text{ core action ở tháng } N+1}{\text{Tổng số user trong Cohort tạo checklist lần đầu ở tháng } N} \times 100\%$$
*   **Lý do lựa chọn:** Việc ép buộc người dùng mở ứng dụng hàng ngày (Daily) là không thực tế vì họ không đi du lịch mỗi ngày. Đo lường theo tháng phản ánh đúng nhịp độ sử dụng tự nhiên của sản phẩm.

---

## 04. Onboarding Audit (Phân tích luồng cũ Ngày 18)

*   **Entry Point:** Mở ứng dụng.
*   **Các bước đi qua:**
    1.  Màn hình Welcome (Giải thích giới hạn hệ thống).
    2.  Yêu cầu cấp 2 quyền: Đọc thời tiết (Vị trí) và Đọc lịch trình cá nhân bằng Toggle.
    3.  Form nhập liệu gồm 5 trường: Điểm đến, Ngày bắt đầu, Ngày kết thúc, Phương tiện di chuyển, Phong cách đóng gói đồ.
    4.  Màn hình Loading phân tích.
    5.  Checklist kết quả hiển thị (First Core Action & Aha Moment nằm tại đây).
*   **Friction Audit (Các rào cản phát hiện):**
    *   **Cấp quyền quá sớm (Friction):** Bắt người dùng bật định vị và đọc lịch trình ngay ở bước 2 khi chưa thấy giá trị sản phẩm. $\rightarrow$ **DELAY** (Chỉ xin quyền thời tiết cục bộ theo điểm đến, quyền GPS và lịch trình sẽ xin sau khi người dùng muốn đồng bộ tự động).
    *   **Form nhập liệu quá dài (Friction):** Điền 5 trường liên tục gây nản lòng. $\rightarrow$ **SIMPLIFY & DELAY** (Chỉ giữ lại Điểm đến và Thời gian. Phương tiện và Phong cách đóng đồ sẽ để mặc định, cho phép tùy chỉnh sau trên checklist).

---

## 05. Redesigned Onboarding (Luồng tối ưu)

### 5.1. Các bước trong luồng thiết kế lại
1.  **Bước 1: Value Proposition rõ ràng:** Màn hình giới thiệu lợi ích 1 chạm: "Tạo checklist hành lý tối ưu trong 10 giây". Nút bấm rõ ràng **[Bắt đầu ngay]**.
2.  **Bước 2: Form nhập tối giản (Minimum Setup):** Chỉ nhập **Điểm đến** và **Thời gian đi**. Các tùy chọn phụ được tối giản hóa bằng việc chọn thẻ tag hoặc để mặc định.
3.  **Bước 3: Aha Moment lập tức (Evidence of Value):** AI hiển thị ngay checklist nháp (Draft Checklist) dựa trên thông tin tối giản mà không cần cấp quyền hệ thống.
4.  **Bước 4: Xin quyền theo ngữ cảnh (Contextual Permission):** Khi người dùng muốn xem dự báo thời tiết chi tiết để AI tinh chỉnh đồ ấm, họ click nút *[Đồng bộ thời tiết]* $\rightarrow$ Lúc này mới hiện yêu cầu cấp quyền định vị.

### 5.2. Bảng so sánh Before/After của Onboarding
| Tiêu chí | Before (Ngày 18) | After (Day 20) | Vì sao thay đổi? |
| :--- | :--- | :--- | :--- |
| **Số bước tới core action** | 5 bước | 3 bước | Giảm số lượng màn hình chuyển tiếp trung gian để user chạm giá trị nhanh hơn. |
| **Số trường phải nhập** | 5 trường | 2 trường | Tránh quá tải nhận thức (Cognitive overload) khi bắt đầu. |
| **Permission trước core action** | 2 permissions (GPS, Lịch trình) | 0 permissions | Trì hoãn việc xin quyền đến khi thực sự cần thiết theo ngữ cảnh (Contextual authorization). |
| **Time to First Core Action** | ~90 giây | ~20 giây | Tối giản hóa biểu mẫu giúp tương tác nhanh gấp 4 lần. |
| **Time to Value (Aha Moment)** | ~100 giây | ~25 giây | Đưa thẳng người dùng đến màn hình checklist nháp để thấy giá trị trước khi bắt cấu hình sâu. |
| **Điểm drop-off chính** | Màn hình xin quyền ngay sau khi mở app | Màn hình nhập điểm đến (nếu user chưa có lịch trình) | Loại bỏ được tỷ lệ từ chối app do lo ngại quyền riêng tư quá sớm. |
| **Evidence of value** | Checklist đầy đủ sau loading | Draft checklist hiển thị tức thì, cập nhật real-time | Chứng minh năng lực của AI ngay lập tức. |
| **Recovery path** | 2 luồng khôi phục lỗi (Vietjet & Fansipan) | Giữ nguyên và tối ưu hóa trải nghiệm tương tác một chạm | Bảo toàn trải nghiệm khắc phục sự cố thông minh của Ngày 18. |

---

## 07. Measurement Ladder & North Star Metric

### 7.1. North Star Metric
*   **North Star Metric:** **Tổng số checklist hành lý được hoàn tất (Finalized Checklists) mỗi tháng**.
    *   *Ý nghĩa:* Thể hiện việc người dùng thực sự tin tưởng và sử dụng checklist để đi du lịch thành công.

### 7.2. Input Metrics
1.  **Activation Rate:** Tỷ lệ người dùng mới hoàn thành Onboarding và lưu checklist nháp đầu tiên trong vòng 7 ngày đầu. (Tác động đến quy mô đầu phễu).
2.  **Checklist Engagement Rate:** Số lượng vật phẩm trung bình được tương tác (Thêm mới, xóa, tick chọn) trên mỗi checklist. (Thể hiện mức độ sâu của tương tác).
3.  **Recovery Click-Through Rate (CTR):** Tỷ lệ người dùng nhấn chọn các giải pháp khôi phục một chạm (ví dụ: "Tối ưu hóa theo luật bay" hoặc "Cập nhật thời tiết Fansipan"). (Minh chứng cho tính hữu ích của HCAI).

### 7.3. Leading và Lagging Indicators
*   **Leading Indicators (Chỉ số dẫn dắt):** Activation Rate, Checklist Engagement Rate, Recovery CTR. (Có thể can thiệp cải thiện trực tiếp qua giao diện).
*   **Lagging Indicators (Chỉ số kết quả):** North Star Metric (Tổng số checklist hoàn tất), Monthly Cohort Retention. (Cần thời gian để đo lường).

### 7.4. Trade-off cần theo dõi
*   **Trade-off:** Đưa liên kết quảng cáo mua/thuê đồ dùng ngoài app (như sạc dự phòng, lều trại) để tăng **Doanh thu đối tác (Revenue)** $\leftrightarrow$ Có thể làm tăng **Friction** khiến người dùng khó chịu, dẫn đến giảm **Checklist Engagement Rate** và **Retention**.

---

## 09. Nature vs Nurture

*   **Nature (Nhịp tự nhiên):** Nhu cầu đóng gói hành lý xuất hiện trước chuyến đi từ 3 đến 7 ngày.
*   **Nurture (Hoạt động nuôi dưỡng):**
    *   *Hoạt động:* Gửi thông báo đẩy (Push Notification) cập nhật thời tiết tại điểm đến trước ngày khởi hành 3 ngày và gợi ý kiểm tra lại hành lý.
    *   *Tần suất nurture:* Tối đa 2 thông báo cho mỗi chuyến đi đã tạo. Không gửi spam hàng ngày vì sẽ gây gỡ cài đặt app (Uninstall rate tăng).
    *   *Metric theo dõi:* Tỷ lệ mở thông báo (Push Open Rate) và tỷ lệ chuyển đổi thành việc mở lại checklist để hoàn tất (`nurture_conversion_rate`).

---

## 10. Hook Model Review

*   **Why Habit?** Giúp ứng dụng trở thành phản xạ tự nhiên của du khách mỗi khi họ chuẩn bị đi xa, thay vì họ phải tự tìm kiếm file Excel hay note tay.
*   **Intended Behavior:** Mở ứng dụng để xem gợi ý hành trang tối ưu trước mỗi chuyến đi.
*   **Frequency & Utility:** Tần suất sử dụng trung bình (1-2 lần/tháng), nhưng tiện ích cực kỳ cao (Perceived Utility lớn do giúp giải quyết nỗi lo phạt tiền quá cân và thiếu đồ).
*   **Hook Loop:**
    1.  **Internal Trigger (Tác nhân bên trong):** Sự lo lắng trước chuyến đi ("Thời tiết ở đó thế nào?", "Liệu mình có quên mang gì quan trọng không?").
    2.  **External Trigger (Tác nhân bên ngoài):** Thông báo đẩy: *"Đà Lạt dự báo có mưa giông lớn vào cuối tuần này. Cập nhật ngay áo mưa và túi chống nước cho hành lý của bạn!"*.
    3.  **Action (Hành động):** Click thông báo mở ứng dụng, thực hiện tick/untick đồ đạc trên checklist được AI gợi ý sẵn.
    4.  **Variable Reward (Phần thưởng thay đổi):** 
        *   *The Hunt (Tìm kiếm):* Khám phá ra các món đồ thông minh mà mình chưa nghĩ tới (ví dụ: tất chống vắt khi đi Cát Tiên) hoặc các điểm cho thuê lều giá rẻ tại Đà Lạt.
        *   *The Self (Bản thân):* Thanh đo trọng lượng chuyển sang màu xanh lá báo an toàn, tạo cảm giác hoàn thành và kiểm soát tốt chuyến đi.
    5.  **Investment (Sự đầu tư):** Người dùng lưu thói quen cá nhân (ví dụ: "Tôi không say tàu xe, bỏ thuốc say xe"), AI tự động học để không bao giờ gợi ý thuốc này cho Minh Anh nữa.
*   **User Impact:** Giúp cải thiện chất lượng chuẩn bị chuyến đi, giảm thiểu căng thẳng trước khi bay và tiết kiệm chi phí phát sinh. Hoàn toàn không gây nghiện tiêu cực.

---

## 11. Metric Tracking Requirement

### 11.1. Bảng định nghĩa metric
| Tên metric | Câu hỏi cần trả lời | Định nghĩa | Công thức | Khoảng thời gian | Segment | Event cần có |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Activation Rate** | Bao nhiêu user mới nhận được giá trị trong tuần đầu? | Tỷ lệ user mới mở app và tạo ít nhất 1 checklist nháp. | $\frac{\text{Số user tạo checklist}}{\text{Tổng số user mới tải app}} \times 100\%$ | Weekly | Theo loại thiết bị (iOS/Android) | `onboarding_started`, `draft_checklist_created` |
| **Finalized Checklist Count** | Quy mô sử dụng cốt lõi của ứng dụng là bao nhiêu? | Tổng số lượt người dùng bấm hoàn tất checklist hành lý. | Tổng số event `checklist_finalized` ghi nhận được. | Monthly | Theo điểm đến (Trong nước / Quốc tế) | `checklist_finalized` |
| **Monthly Retention Rate** | Người dùng có quay lại sử dụng ở chuyến đi tiếp theo? | Tỷ lệ user của tháng $N$ quay lại tạo checklist ở tháng $N+1$. | $\frac{\text{Số user active ở tháng } N+1 \text{ thuộc cohort tháng } N}{\text{Tổng số user của cohort tháng } N}$ | Monthly | Theo Persona (Minh Anh / Khách công tác) | `checklist_finalized`, `app_opened` |
| **Recovery Flow Engagement** | Tính năng giải quyết lỗi HCAI có hữu dụng không? | Tỷ lệ checklist quá cân hoặc đổi thời tiết được tối ưu thành công. | $\frac{\text{Số event recovery\_clicked}}{\text{Tổng số event cảnh báo đỏ hiển thị}} \times 100\%$ | Weekly | Theo loại cảnh báo (Thời tiết / Quá cân) | `warning_displayed`, `recovery_clicked` |

### 11.2. Bảng yêu cầu tracking event
| Event name | Event được ghi khi nào? | User identity | Properties | Metric sử dụng event | Tránh ghi trùng |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`onboarding_started`** | Khi user bắt đầu màn hình Welcome của onboarding. | `anonymous_id` | `source` (tự nhiên, quảng cáo) | Activation Rate | Chỉ ghi nhận 1 lần duy nhất trên mỗi cài đặt ứng dụng. |
| **`draft_checklist_created`** | Khi màn hình checklist nháp đầu tiên được hiển thị. | `anonymous_id` hoặc `user_id` | `destination`, `duration` | Activation Rate | Không ghi lại khi user xoay màn hình hoặc tải lại trang hiện tại. |
| **`item_toggled`** | Khi user check hoặc uncheck một món đồ trong checklist. | `user_id` | `item_name`, `category`, `action` (check/uncheck) | Checklist Engagement Rate | Ghi nhận theo tương tác nhấp chuột thực tế của người dùng. |
| **`recovery_clicked`** | Khi user nhấn chọn giải pháp khôi phục (Cập nhật thời tiết/Tối ưu cân nặng). | `user_id` | `recovery_type` (weather, weight), `action_taken` | Recovery Flow Engagement | Chỉ ghi nhận khi bấm thành công nút hành động, không ghi khi tắt banner cảnh báo. |
| **`checklist_finalized`** | Khi user nhấn nút xác nhận hoàn tất checklist để tải về/in. | `user_id` | `destination`, `total_items`, `total_weight` | Finalized Checklist Count, Retention Rate | Chỉ gửi event khi nút bấm được kích hoạt và trả về kết quả thành công. Khóa nút bấm sau khi nhấn để tránh double click. |

---

### 11.3. Gắn event lên luồng hành trình (Event Flow Mapping)

```text
Onboarding bắt đầu 
   ↓ [Event: onboarding_started]
Nhập Điểm đến & Thời gian
   ↓
Tạo checklist nháp (Aha Moment)
   ↓ [Event: draft_checklist_created]
Người dùng kiểm tra & thay đổi hành lý
   ↓ [Event: item_toggled]
Xuất hiện cảnh báo đỏ (Quá cân / Đổi thời tiết)
   ↓
Người dùng click tối ưu hóa một chạm
   ↓ [Event: recovery_clicked]
Người dùng bấm xác nhận hoàn tất checklist
   ↓ [Event: checklist_finalized] (Core Action - Đạt Activation)
```

### 11.4. Tiêu chí nghiệm thu tracking (Acceptance Criteria)
1.  **Độ chính xác của Core Action:** Event `checklist_finalized` chỉ được kích hoạt một lần duy nhất khi hành động lưu/hoàn thành thành công. Nếu người dùng quay lại sửa checklist và bấm hoàn tất lại trong cùng một phiên làm việc (Session) trong vòng 10 phút, chỉ tính là 1 lần hoàn tất duy nhất để tránh nhiễu dữ liệu.
2.  **Nhất quán dữ liệu:** Mọi event gửi lên máy chủ tracking phải đính kèm cấu trúc chuẩn: `timestamp` định dạng UTC ISO 8601, `user_id` (hoặc `anonymous_id` nếu chưa đăng nhập), và thông tin môi trường thiết bị (`device_type`, `os_version`).
3.  **Khử trùng lặp (Deduplication):** Tải lại trang (Refresh) hoặc tự động lưu (Autosave) trạng thái checklist không được gửi thêm event `draft_checklist_created` hoặc `checklist_finalized`.
4.  **Bảo vệ quyền riêng tư:** Tuyệt đối không gửi các thông tin nhạy cảm của người dùng (như vị trí GPS vĩ độ/kinh độ chính xác, lịch trình cá nhân chi tiết ngoài ứng dụng) trong thuộc tính (Properties) của event.
