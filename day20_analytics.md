# 📊 Báo Cáo Phân Tích Day 20: Retention, Engagement & Habit Loop
**Dự án:** AI Gợi ý hành trang theo thời tiết và hoạt động (Smart Packing & Prep)  
**Mã học viên:** 2A202600980 | **Học viên:** Nguyễn Ngọc Duy  

---

## BÀI 1 — HÀNH VI TỰ NHIÊN VÀ USE CASE
*(Customer Retention Canvas)*

### 1. The Problem (Vấn đề từ góc nhìn người dùng)
*   **Mô tả:** "Tôi mất quá nhiều thời gian để tra cứu thời tiết tại điểm đến, tự lên danh sách đồ dùng cần mang theo lịch trình, rồi lại phải lo lắng xem hành lý có quá cân xách tay của hãng bay hay mang nhầm vật dụng cấm hay không. Đôi khi thời tiết thay đổi đột ngột làm tôi không kịp xoay xở và bị thiếu đồ giữ ấm/chống mưa."
*   *Lưu ý:* Không mô tả bằng tính năng của sản phẩm.

### 2. The Persona (Minh họa đối tượng)
*   **Persona:** Nguyễn Minh Anh (26 tuổi), Nhân viên văn phòng tại TP.HCM.
*   **Hoàn cảnh:** Thích du lịch tự túc cuối tuần và thỉnh thoảng đi công tác kết hợp trekking nhẹ (Đà Lạt, Fansipan, Cát Tiên).
*   **Mục tiêu:** Muốn chuẩn bị hành lý cực nhanh, tối giản dưới 7kg xách tay nhưng phải đảm bảo an toàn, đúng quy định bay và phù hợp với thời tiết thực tế tại điểm đến.
*   **Điều kiện thay đổi hành vi:** Khi hãng bay kiểm soát cân nặng gắt gao hoặc khi đi du lịch vào mùa thời tiết biến động thất thường.

### 3. Anti-persona (Đối tượng không nhắm tới)
*   Bà Trần Thị Mai (55 tuổi), đi du lịch nghỉ dưỡng trọn gói theo đoàn. Có xe đưa đón tận nơi, hướng dẫn viên chuẩn bị sẵn lịch trình và hành lý ký gửi thoải mái. Không có nhu cầu tự tối ưu checklist hay lo lắng thời tiết biến đổi đột ngột.

### 4. The Why (Động lực cốt lõi)
*   **Outcome mong muốn:** Đóng gói hành lý nhanh chóng dưới 5 phút, tránh mất tiền phạt quá cân tại sân bay và an tâm tuyệt đối vì hành trang đã được tối ưu hóa theo thời tiết thực tế và quy định an toàn bay.

### 5. The Alternative (Giải pháp thay thế hiện tại)
*   Ghi chép thủ công trên ứng dụng Notes điện thoại.
*   Dùng bảng Excel template chuẩn bị hành lý tự chế.
*   Hỏi thăm kinh nghiệm từ bạn bè hoặc các hội nhóm du lịch trên mạng xã hội.
*   Chấp nhận đóng đồ theo quán tính và mua bổ sung tại điểm đến nếu thiếu.

### 6. The Frequency (Tần suất xuất hiện tự nhiên)
*   **Tần suất:** **Monthly** (Trung bình 1-2 lần/tháng trước mỗi chuyến đi chơi hoặc đi công tác).

---

## BÀI 2 — TỪ USE CASE TỚI RETENTION METRIC
*(Core Action, Active User & Retention Metric)*

### 1. Xác định Core Action (Nhóm phải mô tả)

| Câu hỏi | Câu trả lời |
| :--- | :--- |
| **Core job của use case là gì?** | Chuẩn bị hành lý tối ưu và an toàn nhất cho chuyến đi dựa trên thời tiết và lịch trình hoạt động thực tế. |
| **Core action là gì?** | Người dùng bấm **Xác nhận checklist cuối cùng** (để tải về, in ra hoặc đánh dấu hoàn tất việc kiểm tra đồ đạc). |
| **Vì sao action này cho thấy user nhận được value?** | Khi bấm xác nhận, người dùng đã đồng ý và chuyển đổi các gợi ý thông minh của AI thành hành động đóng gói hành lý thực tế để chuẩn bị đi du lịch. |
| **Khi nào action được tính là đã xảy ra?** | Khi người dùng click nút "Xác nhận hành lý" thành công trên giao diện và hệ thống ghi nhận sự kiện. |

### 2. Định nghĩa Active User (Nhóm phải trả lời)

*   **Chỉ mở app có được tính active không?** Không. Việc mở app chỉ tính là session truy cập bình thường (Visitor), người dùng chưa tương tác để nhận được giá trị thực tế của sản phẩm.
*   **User phải thực hiện core action nào?** Nhấn nút "Xác nhận checklist cuối cùng" (Finalize Checklist).
*   **Cần thực hiện bao nhiêu lần?** Ít nhất 1 lần.
*   **Trong khoảng thời gian nào?** Trong vòng 30 ngày (Monthly cadence).
*   **Hoàn thành câu:**
    > Một user được tính là active khi **hoàn thành xác nhận ít nhất 1 checklist hành lý** trong **30 ngày**.

### 3. Bảng tổng hợp các thành phần (Nhóm phải ghi đầy đủ)

| Thành phần | Câu trả lời |
| :--- | :--- |
| **Persona và use case** | **Nguyễn Minh Anh (26 tuổi)**. Use case: gợi ý và chuẩn bị hành lý tối giản dưới 7kg xách tay, phù hợp thời tiết và hoạt động chuyến đi. |
| **Natural frequency** | **Monthly** (1-2 lần/tháng trước mỗi chuyến đi chơi hoặc đi công tác xa). |
| **Core action** | Bấm **Xác nhận checklist cuối cùng** để lưu hành lý. |
| **Active user definition** | Một user được tính là active khi hoàn thành xác nhận ít nhất 1 checklist hành lý trong vòng 30 ngày. |
| **Retention metric** | **Monthly Cohort Retention** (Tỷ lệ quay lại tạo checklist ở tháng thứ N+1). |
| **Vì sao metric phù hợp với frequency?** | Vì nhịp độ đi du lịch/đi xa tự nhiên là hàng tháng. Đo lường theo tháng phản ánh đúng giá trị thực tế mà không làm phiền người dùng bằng các thông báo spam hàng ngày để tăng chỉ số ảo (DAU). |


---

## BÀI 3 — ONBOARDING TỚI FIRST CORE ACTION
*(Audit & Redesigned Journey)*

### 1. Audit Prototype Ngày 18 (Trước khi tối ưu)
*   **Entry Point:** Mở ứng dụng.
*   **Các bước:** Welcome $\rightarrow$ Cấp 2 quyền (GPS & Lịch trình) $\rightarrow$ Form 5 trường $\rightarrow$ Loading $\rightarrow$ Checklist (Aha Moment).
*   **Điểm ma sát lớn (Friction):**
    *   *Yêu cầu cấp quyền ngay lúc đầu (Step 2)*: **DELAY**. Bắt xin quyền GPS/Lịch trình khi user chưa biết app mang lại giá trị gì.
    *   *Form nhập quá dài (Step 3)*: **SIMPLIFY**. Yêu cầu nhập 5 trường (Điểm đến, Ngày đi/về, Phương tiện, Kiểu đồ) làm tăng thời gian hoàn thành.

### 2. Thiết kế lại hành trình (Sau khi tối ưu)
*   **Bước 1: Value Proposition rõ ràng:** Màn hình giới thiệu lợi ích 1 chạm: "Tạo checklist hành lý tối ưu trong 10 giây".
*   **Bước 2: Form nhập tối giản (Minimum Setup):** Chỉ nhập **Điểm đến** và **Thời gian đi**.
*   **Bước 3: Aha Moment lập tức (Evidence of Value):** AI hiển thị ngay checklist nháp (Draft Checklist) dựa trên thông tin tối giản mà không cần cấp quyền hệ thống.
*   **Bước 4: Xin quyền theo ngữ cảnh (Contextual Permission):** Chỉ khi người dùng click *[Đồng bộ thời tiết]* để AI tinh chỉnh đồ ấm, họ mới cần cấp quyền định vị.

### 3. Bảng so sánh Before/After
| Tiêu chí | Before (Ngày 18) | After (Day 20) | Vì sao thay đổi? |
| :--- | :--- | :--- | :--- |
| **Số bước tới core action** | 5 bước | 3 bước | Giảm số lượng màn hình trung gian để user chạm giá trị nhanh hơn. |
| **Số trường phải nhập** | 5 trường | 2 trường | Tránh quá tải nhận thức khi bắt đầu. |
| **Permission trước core action** | 2 permissions (GPS, Lịch trình) | 0 permissions | Trì hoãn việc xin quyền đến khi thực sự cần thiết theo ngữ cảnh. |
| **Time to First Core Action** | ~90 giây | ~20 giây | Tối giản hóa biểu mẫu giúp tương tác nhanh gấp 4 lần. |
| **Time to Value (Aha Moment)** | ~100 giây | ~25 giây | Đưa thẳng người dùng đến màn hình checklist nháp để thấy giá trị trước. |
| **Điểm drop-off chính** | Màn hình xin quyền ngay sau khi mở app | Màn hình nhập điểm đến (nếu user chưa có lịch trình) | Loại bỏ được tỷ lệ từ chối app do lo ngại quyền riêng tư quá sớm. |
| **Evidence of value** | Checklist đầy đủ sau loading | Draft checklist hiển thị tức thì, cập nhật real-time | Chứng minh năng lực của AI ngay lập tức. |
| **Recovery path** | 2 luồng khôi phục lỗi (Vietjet & Fansipan) | Giữ nguyên và tối ưu hóa trải nghiệm tương tác một chạm | Bảo toàn trải nghiệm khắc phục sự cố thông minh của Ngày 18. |

---

## BÀI 4 — MEASUREMENT LADDER VÀ NORTH STAR METRIC
*(Ladder, North Star & Trade-off)*

### 1. Đặt metric vào Measurement Ladder
*   **Nấc 6: Revenue (Doanh thu):** Doanh thu hoa hồng từ dịch vụ liên kết (thuê đồ trekking, lều trại).
*   **Nấc 5: Retention (Duy trì):** Monthly Cohort Retention (Tỷ lệ quay lại ở tháng N+1).
*   **Nấc 4: Core Action (Hành động cốt lõi):** Bấm xác nhận checklist cuối cùng.
*   **Nấc 3: Activation (Kích hoạt):** Hoàn thành Onboarding và nhìn thấy checklist nháp.
*   **Nấc 2: Visitor (Khách truy cập):** User truy cập màn hình chào mừng.
*   **Nấc 1: Traffic (Lưu lượng):** Tiếp cận qua quảng cáo, hội nhóm du lịch tự túc.

### 2. North Star Metric và Input Metrics
*   **North Star Metric:** **Tổng số checklist hành lý được hoàn tất (Finalized Checklists) mỗi tháng**.
*   **Input Metrics:**
    1.  *Activation Rate:* Tỷ lệ người dùng mới hoàn thành Onboarding và tạo checklist nháp.
    2.  *Checklist Engagement:* Số lượng vật phẩm trung bình được tương tác trên mỗi checklist.
    3.  *Recovery CTR:* Tỷ lệ người dùng nhấn chọn giải pháp khôi phục một chạm.
*   **Leading vs Lagging:** Input metrics là leading, North Star và Retention là lagging.
*   **Trade-off:** Chèn link liên kết mua/thuê trang bị ngoài app tăng *Revenue* nhưng nếu chèn quá nhiều sẽ làm tăng *Friction* gây giảm *Checklist Engagement* và *Retention*.

---

## BÀI 5 — NATURE, NURTURE VÀ HABIT LOOP
*(Nature vs Nurture & Hook Model)*

### 1. Nature vs Nurture
| Nội dung | Câu trả lời |
| :--- | :--- |
| **Natural frequency của use case** | **Monthly** (Trung bình 1-2 lần/tháng trước mỗi chuyến đi chơi hoặc đi công tác). |
| **Internal trigger** | Sự lo lắng trước chuyến đi: "Liệu mình có quên mang gì quan trọng không?", "Thời tiết ở đó thế nào?". |
| **External trigger hiện có** | Thông báo đẩy từ app: "Dự báo thời tiết Đà Lạt có mưa giông lớn vào cuối tuần này. Cập nhật ngay áo mưa và túi chống nước cho hành lý!". |
| **Một hoạt động nurture phù hợp** | Gửi thông báo đẩy cập nhật thời tiết tại điểm đến trước ngày đi 3 ngày và gợi ý kiểm tra lại hành lý. |
| **Vì sao nurture không quá dày hoặc quá thưa?** | Tần suất tối đa 2 thông báo/chuyến đi. Nurture phải tôn trọng và bám sát nhịp tự nhiên của chuyến đi. Không spam hàng ngày tránh gỡ cài đặt app. |
| **Metric dùng để theo dõi tác động** | Tỷ lệ mở thông báo (Push Open Rate) và tỷ lệ chuyển đổi mở checklist để hoàn thành (`nurture_conversion_rate`). |

### 2. Hook Model (Hook Review)
| Thành phần | Câu hỏi | Câu trả lời |
| :--- | :--- | :--- |
| **Why Habit?** | Vì sao user hoặc business cần hành vi này trở thành habit? | Giúp ứng dụng trở thành phản xạ tự nhiên của du khách mỗi khi họ chuẩn bị đi xa, thay vì dùng Excel hay ghi chép thủ công. |
| **Intended Behavior** | Hành vi cụ thể nào cần được lặp lại? | Mở ứng dụng, kiểm tra các món đồ trên checklist gợi ý và xác nhận đóng gói hành lý trước chuyến đi. |
| **Frequency & Utility** | Hành vi có đủ thường xuyên hoặc đủ hữu ích để hình thành habit không? | Tần suất sử dụng trung bình (1-2 lần/tháng), tần suất thấp nhưng tiện ích cực kỳ cao (Perceived Utility lớn giúp tránh phạt quá cân, thiếu đồ sinh tồn). |
| **Internal Trigger** | Nhu cầu hoặc cảm xúc nào xuất hiện thường xuyên nhất? | Cảm giác lo lắng, bồn chồn trước khi đi xa sợ chuẩn bị thiếu đồ hoặc mang nhầm đồ cấm bay. |
| **External Trigger** | Trigger nào xuất hiện đúng nơi và đúng thời điểm? | Thông báo đẩy trước chuyến đi 3 ngày cảnh báo thời tiết biến động hoặc cảnh báo quá hạn cân khi bay. |
| **Action** | Hành vi đơn giản nhất để nhận reward là gì? | Click thông báo mở ứng dụng và click tick/untick hành lý trên checklist được AI chuẩn bị sẵn. |
| **Motivation** | User muốn thực hiện action vì điều gì? | Tìm kiếm sự an tâm, an toàn và tự tin trước khi bắt đầu hành trình (Motivation: Pleasure/Pain, Hope/Fear). |
| **Ability** | Rào cản nào cần được loại bỏ để action dễ hơn? | Đã rút gọn Onboarding từ 5 bước xuống 3 bước, giảm nhập liệu từ 5 trường xuống 2 trường, trì hoãn xin quyền GPS để giảm thiểu tối đa rào cản thời gian và nhận thức (Time and Brain cycles). |
| **Variable Reward** | The Tribe, The Hunt hay The Self? | **The Hunt** (khám phá đồ dùng trekking chuyên dụng độc đáo, địa điểm thuê đồ giá rẻ) và **The Self** (hoàn thành checklist, thanh đo hành lý báo màu xanh an toàn). |
| **Investment** | User bỏ lại content, data, reputation, skill hoặc công sức gì? | Nhập thói quen cá nhân (ví dụ: "Tôi đi xe Jeep, bỏ giày leo núi") và đồng ý lưu lâu dài để AI học thói quen. |
| **Next Trigger** | Investment dẫn tới trigger tiếp theo như thế nào? | Hệ thống lưu cấu hình và tự động đặt lịch nhắc nhở "Kiểm tra lại hành lý trước khi bay 4 tiếng" để user hoàn tất lần cuối. |
| **User Impact** | Habit này có thực sự có lợi cho user không? | Có lợi. Giúp chuẩn bị hành lý chu đáo, giảm stress trước chuyến đi, tiết kiệm chi phí quá cước và đảm bảo an toàn sinh tồn khi thời tiết đổi đột ngột. |

---

## BÀI 6 — METRIC TRACKING REQUIREMENT
*(Tracking Plan & Acceptance Criteria)*

### 1. Bảng định nghĩa metric
| Tên metric | Câu hỏi cần trả lời | Định nghĩa | Công thức | Khoảng thời gian | Segment | Event cần có |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Activation Rate** | Bao nhiêu user mới nhận được giá trị trong tuần đầu? | Tỷ lệ user mới mở app và tạo ít nhất 1 checklist nháp. | $\frac{\text{Số user tạo checklist}}{\text{Tổng số user mới tải app}} \times 100\%$ | Weekly | Theo loại thiết bị (iOS/Android) | `onboarding_started`, `draft_checklist_created` |
| **Finalized Checklist Count** | Quy mô sử dụng cốt lõi của ứng dụng là bao nhiêu? | Tổng số lượt người dùng bấm hoàn tất checklist hành lý. | Tổng số event `checklist_finalized` ghi nhận được. | Monthly | Theo điểm đến (Trong nước / Quốc tế) | `checklist_finalized` |
| **Monthly Retention Rate** | Người dùng có quay lại sử dụng ở chuyến đi tiếp theo? | Tỷ lệ user của tháng $N$ quay lại tạo checklist ở tháng $N+1$. | $\frac{\text{Số user active ở tháng } N+1 \text{ thuộc cohort tháng } N}{\text{Tổng số user của cohort tháng } N}$ | Monthly | Theo Persona (Minh Anh / Khách công tác) | `checklist_finalized`, `app_opened` |
| **Recovery Flow Engagement** | Tính năng giải quyết lỗi HCAI có hữu dụng không? | Tỷ lệ checklist quá cân hoặc đổi thời tiết được tối ưu thành công. | $\frac{\text{Số event recovery\_clicked}}{\text{Tổng số event cảnh báo đỏ hiển thị}} \times 100\%$ | Weekly | Theo loại cảnh báo (Thời tiết / Quá cân) | `warning_displayed`, `recovery_clicked` |

### 2. Bảng yêu cầu tracking event
| Event name | Event được ghi khi nào? | User identity | Properties | Metric sử dụng event | Tránh ghi trùng |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`onboarding_started`** | Khi user bắt đầu màn hình Welcome của onboarding. | `anonymous_id` | `source` (tự nhiên, quảng cáo) | Activation Rate | Chỉ ghi nhận 1 lần duy nhất trên mỗi cài đặt ứng dụng. |
| **`draft_checklist_created`** | Khi màn hình checklist nháp đầu tiên được hiển thị. | `anonymous_id` hoặc `user_id` | `destination`, `duration` | Activation Rate | Không ghi lại khi user xoay màn hình hoặc tải lại trang hiện tại. |
| **`item_toggled`** | Khi user check hoặc uncheck một món đồ trong checklist. | `user_id` | `item_name`, `category`, `action` (check/uncheck) | Checklist Engagement Rate | Ghi nhận theo tương tác nhấp chuột thực tế của người dùng. |
| **`recovery_clicked`** | Khi user nhấn chọn giải pháp khôi phục (Cập nhật thời tiết/Tối ưu cân nặng). | `user_id` | `recovery_type` (weather, weight), `action_taken` | Recovery Flow Engagement | Chỉ ghi nhận khi bấm thành công nút hành động, không ghi khi tắt banner cảnh báo. |
| **`checklist_finalized`** | Khi user nhấn nút xác nhận hoàn tất checklist để tải về/in. | `user_id` | `destination`, `total_items`, `total_weight` | Finalized Checklist Count, Retention Rate | Chỉ gửi event khi nút bấm được kích hoạt và trả về kết quả thành công. Khóa nút bấm sau khi nhấn để tránh double click. |

### 3. Tiêu chí nghiệm thu tracking (Acceptance Criteria)
1.  **Độ chính xác của Core Action:** Event `checklist_finalized` chỉ được kích hoạt một lần duy nhất khi hành động lưu/hoàn thành thành công. Nếu người dùng quay lại sửa checklist và bấm hoàn tất lại trong cùng một phiên làm việc (Session) trong vòng 10 phút, chỉ tính là 1 lần hoàn tất duy nhất để tránh nhiễu dữ liệu.
2.  **Nhất quán dữ liệu:** Mọi event gửi lên máy chủ tracking phải đính kèm cấu trúc chuẩn: `timestamp` định dạng UTC ISO 8601, `user_id` (hoặc `anonymous_id` nếu chưa đăng nhập), và thông tin môi trường thiết bị (`device_type`, `os_version`).
3.  **Khử trùng lặp (Deduplication):** Tải lại trang (Refresh) hoặc tự động lưu (Autosave) trạng thái checklist không được gửi thêm event `draft_checklist_created` hoặc `checklist_finalized`.
4.  **Bảo vệ quyền riêng tư:** Tuyệt đối không gửi các thông tin nhạy cảm của người dùng (như vị trí GPS vĩ độ/kinh độ chính xác, lịch trình cá nhân chi tiết ngoài ứng dụng) trong thuộc tính (Properties) của event.
