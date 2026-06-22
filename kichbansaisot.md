# Kịch Bản Sai Sót, Không Chắc Chắn và Khôi Phục (Failure, Uncertainty & Recovery Scenarios)
**Chủ đề:** AI Gợi ý hành trang theo thời tiết và hoạt động (Smart Packing & Prep)
*Bài thực hành Ngày 18 — Human-Centered AI Design*

Tài liệu này thiết kế chi tiết 3 kịch bản xử lý khi AI gặp sai sót, không chắc chắn hoặc cần khôi phục trải nghiệm cho tính năng **Smart Packing & Prep**. Các kịch bản được xây dựng bám sát theo cấu trúc yêu cầu của bài thực hành: mô tả luồng giao diện trực quan và giải trình thiết kế (Design Rationale) trả lời đầy đủ 10 câu hỏi cốt lõi về HCAI (Human-Centered AI).

---

## 📑 MỤC LỤC
1. [Kịch bản 1: Thời tiết thay đổi đột ngột làm lệch danh sách trang phục đề xuất (Sai sót & Khôi phục)](#kịch-bản-1-thời-tiết-thay-đổi-đột-ngột-làm-lệch-danh-sách-trang-phục-đề-xuất-sai-sót-&-khôi-phục)
2. [Kịch bản 2: Hành trang đề xuất vượt quá giới hạn cân nặng hoặc vi phạm quy định bay (Không chắc chắn & Sai sót)](#kịch-bản-2-hành-trang-đề-xuất-vượt-quá-giới-hạn-cân-nặng-hoặc-vi-phạm-quy-định-bay-không-chắc-chắn-&-sai-sót)
3. [Kịch bản 3: Thiếu thông tin về mức độ kinh nghiệm/thể trạng của người dùng đối với hoạt động độ khó cao (Không chắc chắn & Thu thập bối cảnh)](#kịch-bản-3-thiếu-thông-tin-về-mức-độ-kinh-nghiệmthể-trạng-của-người-dùng-đối-với-hoạt-động-độ-khó-cao-không-chắc-chắn-&-thu-thập-bối-cảnh)

---

## ⛅ KỊCH BẢN 1: Thời tiết thay đổi đột ngột làm lệch danh sách trang phục đề xuất (Sai sót & Khôi phục)

### 1. Flow và Giao diện trực quan (Flow & UI States)
*   **Bối cảnh ban đầu:** Người dùng lập kế hoạch leo núi Fansipan 3 ngày vào tuần sau. Ban đầu, dự báo thời tiết là nắng ráo ($20^\circ\text{C} - 25^\circ\text{C}$). AI đề xuất danh sách hành trang gọn nhẹ: quần áo thể thao mỏng, kem chống nắng, mũ rộng vành.
*   **Trạng thái AI:** 2 ngày trước chuyến đi, dự báo thời tiết tại Fansipan cập nhật đột ngột: nhiệt độ giảm sâu xuống $8^\circ\text{C}$ kèm mưa phùn và gió mùa. Danh sách hành lý đã đề xuất trước đó trở nên hoàn toàn sai lệch và gây nguy hiểm cho người dùng.
*   **Điều người dùng nhìn thấy:** Khi mở ứng dụng, màn hình chuẩn bị hành lý (Packing List) hiển thị một biểu ngữ cảnh báo màu đỏ nổi bật ở trên cùng: 
    > ⚠️ **Thời tiết tại Fansipan đã thay đổi đột ngột!**
    > Nhiệt độ thực tế giảm từ $22^\circ\text{C}$ xuống còn $8^\circ\text{C}$ và có khả năng mưa 80%. Danh sách hành lý hiện tại của bạn không còn phù hợp.
*   **Lựa chọn kiểm soát (User Control):** Kèm theo cảnh báo là một nút bấm nổi bật: **[Cập nhật hành lý theo thời tiết mới]** và một nút nhỏ hơn: **[Giữ nguyên danh sách cũ]**.
*   **Đường khôi phục (Recovery path):**
    *   Khi người dùng nhấn **[Cập nhật hành lý theo thời tiết mới]**, giao diện hiển thị trạng thái chuyển đổi rõ rệt giữa hai danh sách (So sánh Trước/Sau):
        *   *Loại bỏ/Giảm bớt:* Kem chống nắng, áo thun ngắn tay, quần shorts (chuyển sang phần "Đồ dùng dự phòng").
        *   *Thêm mới:* Áo phao giữ nhiệt, áo gió chống nước (gore-tex), găng tay len, áo mưa tiện lợi, và túi sưởi ấm.
    *   Người dùng có thể tick chọn nhanh hoặc bỏ chọn từng món đồ mới thêm trước khi xác nhận lưu danh sách cuối cùng.

### 2. Design Rationale (Giải trình Thiết kế)
1.  **AI đang biết gì?** AI biết địa điểm (Fansipan), thời gian chuyến đi, hoạt động (leo núi), danh sách đồ cũ đã lưu, và dữ liệu thời tiết cập nhật thời gian thực từ API.
2.  **AI chưa biết gì hoặc đang không chắc điều gì?** AI chưa biết người dùng đã đóng gói (pack) xong đồ theo danh sách cũ hay chưa, và liệu người dùng có khả năng chịu lạnh tốt hay không.
3.  **AI đang đưa ra giả định nào?** AI giả định người dùng chưa khởi hành và cần thay đổi hoàn toàn trang phục sang đồ giữ ấm/chống nước để đảm bảo an toàn sức khỏe.
4.  **Điều gì có thể sai?** AI đề xuất đồ quá dày gây nặng hành lý không cần thiết, hoặc người dùng đã lên đường và không kịp mua sắm thêm những món đồ mới được đề xuất.
5.  **Nếu AI sai, hậu quả là gì và ai chịu ảnh hưởng?** Hậu quả cực kỳ nghiêm trọng (người dùng bị cảm lạnh, hạ thân nhiệt trên núi, ảnh hưởng đến tính mạng và sức khỏe). Người dùng chịu toàn bộ ảnh hưởng.
6.  **Sai sót có dễ phát hiện và dễ hoàn tác không?** Cực kỳ dễ phát hiện nhờ cảnh báo thời tiết trực quan trên đầu app. Hoàn tác dễ dàng bằng cách bấm chọn lại các món đồ cũ.
7.  **AI nên Act, Ask hay Don't Act? Vì sao?** AI nên **Ask (Hỏi trước)**. Vì việc thay đổi hành lý đã chuẩn bị đòi hỏi công sức sắp xếp lại của người dùng, AI không được tự ý xóa/thay đổi danh sách cũ khi chưa được cho phép mà phải đưa ra cảnh báo và xin xác nhận cập nhật.
8.  **Người dùng kiểm tra, sửa, từ chối hoặc hoàn tác ở đâu?** Người dùng kiểm tra bảng so sánh đồ dùng trước/sau cập nhật ngay trên màn hình chuẩn bị đồ và bấm nút hoàn tác ở cuối màn hình nếu muốn quay lại danh sách cũ.
9.  **Phản hồi nào được thu thập hoặc trả lại?**
    *   *Explicit User Feedback:* Bấm nút xác nhận cập nhật thời tiết hoặc từ chối.
    *   *Implicit User Feedback:* Người dùng giữ lại một số áo thun ngắn tay dù thời tiết lạnh (tín hiệu ngầm định họ muốn mặc nhiều lớp hoặc dùng làm đồ ngủ trong lều có sưởi).
10. **Flow giúp người dùng tiếp tục hoàn thành mục tiêu như thế nào?** Giúp người dùng nhanh chóng điều chỉnh hành lý theo thực tế thời tiết chỉ với một chạm, tránh thiếu hụt đồ bảo hộ quan trọng khi leo núi dưới mưa lạnh.

---

## ✈️ KỊCH BẢN 2: Hành trang đề xuất vượt quá giới hạn cân nặng hoặc vi phạm quy định bay (Không chắc chắn & Sai sót)

### 1. Flow và Giao diện trực quan (Flow & UI States)
*   **Bối cảnh ban đầu:** Người dùng chuẩn bị đi cắm trại (Camping) kết hợp quay phim bằng flycam tại Đà Lạt. Họ đặt vé máy bay hạng phổ thông của Vietjet Air (chỉ bao gồm 7kg hành lý xách tay, không ký gửi).
*   **Trạng thái AI:** AI gợi ý một danh sách chuẩn bị đầy đủ cho hoạt động cắm trại gồm: Lều dã ngoại, túi ngủ, flycam + 3 viên pin dự phòng, chân máy ảnh (tripod), gậy leo núi, và một bộ dụng cụ đa năng (chứa dao nhỏ kéo nhỏ). Tổng cân nặng ước tính của danh sách này là 12kg, vượt quá 7kg xách tay và chứa các vật dụng bị cấm mang lên cabin máy bay.
*   **Điều người dùng nhìn thấy:** Trên màn hình Packing List, hệ thống hiển thị một thanh đo cân nặng (Weight Tracker) ở trạng thái quá tải màu đỏ: `12kg / 7kg xách tay` kèm theo cảnh báo:
    > ⚠️ **Hành lý vượt quá giới hạn xách tay (7kg) của Vietjet Air!**
    > Một số vật dụng trong danh sách của bạn có nguy cơ bị tịch thu tại cửa an ninh sân bay.
*   **Lựa chọn kiểm soát (User Control):** Bên cạnh các vật dụng vi phạm quy chế bay, hệ thống gắn nhãn cảnh báo đỏ:
    *   *Gậy leo núi & Bộ dao đa năng:* `🚫 Cấm mang lên cabin (xách tay)`
    *   *Pin Flycam (Lithium):* `⚠️ Bắt buộc xách tay, không được ký gửi`
    *   Người dùng có nút bấm: **[Tối ưu hóa theo quy định bay]** hoặc **[Tôi sẽ mua thêm ký gửi]**.
*   **Đường khôi phục (Recovery path):**
    *   Nếu chọn **[Tối ưu hóa theo quy định bay]**, AI sẽ:
        1. Gợi ý chuyển Lều và Túi ngủ sang danh sách "Thuê tại điểm đến" (đồng thời hiển thị gợi ý 3 cửa hàng cho thuê đồ cắm trại uy tín tại Đà Lạt).
        2. Gợi ý loại bỏ gậy leo núi và dao đa năng để thuê hoặc mua sau khi hạ cánh.
        3. Tự động tính toán lại cân nặng về mức an toàn (dưới 7kg).
    *   Nếu chọn **[Tôi sẽ mua thêm ký gửi]**, hệ thống tự động cập nhật lại hạn mức cân nặng lên 20kg và chuyển hướng người dùng đến trang mua thêm hành lý của hãng bay.

### 2. Design Rationale (Giải trình Thiết kế)
1.  **AI đang biết gì?** AI biết hãng hàng không (Vietjet Air), hạng vé (phổ thông - 7kg xách tay), danh sách vật dụng gợi ý và trọng lượng ước tính của từng món đồ, quy định an ninh hàng không quốc gia.
2.  **AI chưa biết gì hoặc đang không chắc điều gì?** AI không chắc chắn người dùng có đi cùng người khác để chia bớt cân nặng hành lý hay không, hoặc họ có sẵn sàng chi thêm tiền để mua hành lý ký gửi hay không.
3.  **AI đang đưa ra giả định nào?** AI giả định người dùng muốn mang tất cả đồ dùng cá nhân từ nhà đi và không nắm rõ luật an ninh sân bay.
4.  **Điều gì có thể sai?** Người dùng bị phạt tiền nặng tại sân bay vì quá cân xách tay, hoặc bị tịch thu các thiết bị đắt tiền (gậy leo núi, dụng cụ đa năng) tại cửa kiểm soát an ninh.
5.  **Nếu AI sai, hậu quả là gì và ai chịu ảnh hưởng?** Hậu quả trung bình-cao (thiệt hại tài chính do bị tịch thu đồ, phạt tiền hoặc trễ chuyến bay). Người dùng chịu ảnh hưởng trực tiếp.
6.  **Sai sót có dễ phát hiện và dễ hoàn tác không?** Dễ phát hiện thông qua các nhãn cảnh báo đỏ bên cạnh từng món đồ trên màn hình. Hoàn tác dễ dàng bằng cách thêm lại các món đồ bị loại bỏ nếu người dùng chọn phương án đi bằng đường bộ/ô tô thay vì máy bay.
7.  **AI nên Act, Ask hay Don't Act? Vì sao?** AI nên áp dụng mức **Ask (Hỏi trước)** và **Don't Act**. AI tuyệt đối không được tự ý xóa các món đồ cấm ra khỏi danh sách chuẩn bị (vì người dùng vẫn cần dùng chúng khi đến nơi), mà phải đưa ra cảnh báo luật bay và hỏi người dùng phương án xử lý (thuê ngoài hay ký gửi).
8.  **Người dùng kiểm tra, sửa, từ chối hoặc hoàn tác ở đâu?** Người dùng kiểm tra trực tiếp trên thanh cân nặng hành lý và các nhãn cảnh báo gắn cạnh tên vật dụng, bấm chọn cách xử lý ngay trên các nút gợi ý nhanh.
9.  **Phản hồi nào được thu thập hoặc trả lại?**
    *   *Explicit User Feedback:* Bấm chọn "Thuê đồ tại điểm đến" hoặc "Mua thêm ký gửi".
    *   *Implicit User Feedback:* Người dùng phớt lờ cảnh báo cấm xách tay và vẫn giữ gậy leo núi (hệ thống ghi nhận và dự đoán người dùng có thể đi bằng phương tiện khác hoặc đã mua ký gửi ngoài app).
10. **Flow giúp người dùng tiếp tục hoàn thành mục tiêu như thế nào?** Giúp người dùng thông qua cửa an ninh sân bay thuận lợi mà không bị phạt tiền hay mất mát tài sản, đồng thời đảm bảo vẫn có đủ trang thiết bị cắm trại bằng giải pháp thuê đồ tại chỗ.

---

## ⛰️ KỊCH BẢN 3: Thiếu thông tin về mức độ kinh nghiệm/thể trạng của người dùng đối với hoạt động độ khó cao (Không chắc chắn & Thu thập bối cảnh)

### 1. Flow và Giao diện trực quan (Flow & UI States)
*   **Bối cảnh ban đầu:** Người dùng thêm hoạt động *"Trekking rừng quốc gia Cát Tiên 2 ngày"* vào lịch trình du lịch của mình.
*   **Trạng thái AI:** Địa hình rừng Cát Tiên mùa mưa có nhiều vắt, độ ẩm cao và đường sình lầy nguy hiểm. AI cần gợi ý đồ bảo hộ chuyên dụng (thuốc chống vắt, tất chống vắt, giày bám địa hình, thuốc men đặc trị) nhưng chưa biết người dùng là người mới bắt đầu (beginner) hay dân trekking chuyên nghiệp, cũng như không biết họ có tiền sử dị ứng côn trùng hay không.
*   **Điều người dùng nhìn thấy:** Khi người dùng mở tab Packing List cho hoạt động này, thay vì hiển thị ngay một danh sách đồ áp đặt, hệ thống hiển thị một bảng hỏi ngắn gọn được thiết kế thân thiện:
    > 🌲 **Bạn đã sẵn sàng cho chuyến đi rừng Cát Tiên?**
    > Để gợi ý hành lý an toàn và tiết kiệm nhất cho bạn, hãy cho tôi biết:
    > * Mức độ kinh nghiệm trekking của bạn?
    > * Bạn có cần chuẩn bị thêm đồ chống vắt/côn trùng chuyên dụng không?
*   **Lựa chọn kiểm soát (User Control):** Dưới câu hỏi là các nút chọn nhanh (Quick Tags):
    *   *Kinh nghiệm:* **[Lần đầu đi]** | **[Đã đi vài lần]** | **[Chuyên nghiệp]**
    *   *Đồ chống côn trùng:* **[Có, da tôi nhạy cảm]** | **[Không cần thiết]**
*   **Đường khôi phục (Recovery path):**
    *   Sau khi người dùng chọn (ví dụ: **[Lần đầu đi]** và **[Da nhạy cảm]**), AI lập tức tạo ra danh sách chuẩn bị cá nhân hóa cao:
        *   Thêm vào danh sách: Tất chống vắt cao cổ, xịt chống muỗi DEET > 30% (dành cho da nhạy cảm), giày leo núi có gai bám sâu, và bộ sơ cứu cá nhân (băng gạc, cồn đỏ).
        *   Hiển thị một lớp giải thích (Explainability) ngắn cạnh các món đồ: *"Đồ bảo hộ này được khuyên dùng để tránh vắt rừng Cát Tiên cắn gây nhiễm trùng cho người mới"* kèm hình ảnh minh họa cách đeo tất chống vắt đúng cách.
    *   Người dùng có thể bấm nút **[Thay đổi tùy chọn bối cảnh]** bất cứ lúc nào để chọn lại mức kinh nghiệm khác.

### 2. Design Rationale (Giải trình Thiết kế)
1.  **AI đang biết gì?** AI biết địa điểm (Rừng Cát Tiên), hoạt động (Trekking 2 ngày), thời gian đi (mùa mưa).
2.  **AI chưa biết gì hoặc đang không chắc điều gì?** AI chưa biết thể lực, mức độ kinh nghiệm đi rừng và độ nhạy cảm của da người dùng đối với vết cắn côn trùng.
3.  **AI đang đưa ra giả định nào?** AI giả định người dùng chưa có đồ bảo hộ chuyên dụng và cần được cảnh báo về mối nguy hiểm từ vắt rừng mùa mưa.
4.  **Điều gì có thể sai?** Gợi ý đồ quá sơ sài khiến người dùng gặp nguy hiểm (bị vắt cắn, trượt ngã do giày không bám), hoặc gợi ý đồ quá chuyên nghiệp đắt tiền gây lãng phí cho người đi lần đầu.
5.  **Nếu AI sai, hậu quả là gì và ai chịu ảnh hưởng?** Hậu quả trung bình-cao (người dùng bị thương, nhiễm trùng, dị ứng hoặc lãng phí tiền mua đồ không dùng đến). Người dùng chịu ảnh hưởng trực tiếp.
6.  **Sai sót có dễ phát hiện và dễ hoàn tác không?** Dễ phát hiện vì danh sách đồ hiển thị trực quan trước chuyến đi. Hoàn tác/thay đổi danh sách thực hiện bằng cách chọn lại thẻ kinh nghiệm.
7.  **AI nên Act, Ask hay Don't Act? Vì sao?** AI nên **Ask (Hỏi trước)**. Do thiếu thông tin cá nhân cốt lõi ảnh hưởng trực tiếp đến an toàn sức khỏe, AI không được tự ý hành động áp đặt danh sách (Act) mà phải dừng lại hỏi ý kiến để thu thập thêm bối cảnh.
8.  **Người dùng kiểm tra, sửa, từ chối hoặc hoàn tác ở đâu?** Người dùng trả lời câu hỏi khảo sát nhanh ngay trên màn hình chuẩn bị hành lý và chỉnh sửa danh sách đồ bằng cách check/uncheck các ô vuông.
9.  **Phản hồi nào được thu thập hoặc trả lại?**
    *   *Explicit User Feedback:* Các tag lựa chọn về kinh nghiệm và loại da.
    *   *Implicit User Feedback:* Người dùng xóa bỏ xịt côn trùng khỏi danh sách (tín hiệu ngầm định họ tự mang đi hoặc đã có sẵn ở nhà).
10. **Flow giúp người dùng tiếp tục hoàn thành mục tiêu như thế nào?** Đảm bảo người dùng có đầy đủ trang thiết bị bảo hộ sinh tồn phù hợp nhất với thể trạng và kinh nghiệm của mình, giảm thiểu rủi ro tai nạn trong chuyến đi rừng.

---

## 📊 MA TRẬN FEEDBACK 2X2 CHO SMART PACKING & PREP
*(Đáp ứng yêu cầu bắt buộc của bài thực hành)*

| Chiều tương tác | Explicit (Tường minh) | Implicit (Ngầm định) |
| :--- | :--- | :--- |
| **User $\rightarrow$ System** | Người dùng bấm nút báo cáo sai lệch thông tin thời tiết hoặc hãng bay; check/uncheck để thêm/xóa đồ khỏi danh sách. | Người dùng giữ lại đồ ấm dù thời tiết báo nắng ấm (hệ thống ghi nhận thói quen mặc ấm của cá nhân để cá nhân hóa sau này). |
| **System $\rightarrow$ User** | Hiển thị biểu ngữ cảnh báo thời tiết thay đổi đột ngột; hiển thị nhãn `🚫 Cấm mang lên cabin` cạnh các vật dụng sắc nhọn. | Thanh cân nặng chuyển từ Xanh lá (An toàn) sang Đỏ (Quá tải) để người dùng tự hiểu cần bớt đồ mà không cần thông báo dạng pop-up làm phiền. |
