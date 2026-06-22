# AI Gợi ý hành trang theo thời tiết và hoạt động  
## Smart Packing & Prep

## 1. Tổng quan lát cắt tính năng

### Ngữ cảnh
Người dùng đang chuẩn bị hành lý trước chuyến đi nhưng không chắc cần mang theo những gì. Danh sách đồ cần thiết phụ thuộc vào:

- Điểm đến.
- Thời gian chuyến đi.
- Dự báo thời tiết.
- Các hoạt động trong lịch trình.
- Phương tiện di chuyển.
- Sở thích mang hành lý gọn nhẹ hay đầy đủ.
- Những vật dụng người dùng đã có.

### Tính năng AI
AI phân tích điểm đến, thời gian, dự báo thời tiết và lịch trình để tạo checklist hành lý cá nhân hóa.

AI có thể:

- Phân loại vật dụng theo mức độ cần thiết.
- Giải thích lý do đề xuất từng món đồ.
- Hỏi thêm khi thiếu thông tin quan trọng.
- Cập nhật checklist khi lịch trình thay đổi.
- Gợi ý món đồ cần chuẩn bị hoặc mua.
- Cho phép người dùng sửa, bỏ, xác nhận hoặc hoàn tác.

AI không được:

- Tự mua hàng.
- Tự thêm sản phẩm vào giỏ hàng.
- Tự thanh toán.
- Tự đặt dịch vụ.
- Ghi nhớ thông tin cá nhân lâu dài khi chưa được người dùng cho phép.

---

# 2. Kịch bản tương tác 1  
## AI hỏi thêm trước khi tạo checklist hành lý

### 2.1. Bối cảnh ban đầu

Người dùng nhập:

> Tôi đi Đà Lạt từ ngày 10 đến 12/7. Hãy chuẩn bị danh sách hành lý cho tôi.

AI đã biết:

- Điểm đến: Đà Lạt.
- Thời gian: 3 ngày 2 đêm.
- Dự báo: trời mát, có khả năng mưa.
- Lịch trình: tham quan thành phố, đi Langbiang và chợ đêm.

AI chưa biết:

- Người dùng đi xe máy, ô tô hay phương tiện công cộng.
- Người dùng sẽ trekking hay đi xe lên Langbiang.
- Người dùng muốn mang hành lý gọn nhẹ hay đầy đủ.
- Người dùng đã có áo mưa, giày chống trượt hoặc sạc dự phòng hay chưa.

---

## 2.2. Flow tương tác

### Màn hình 1 — AI đang phân tích

Hệ thống hiển thị:

> **Đang tạo hành trang cá nhân hóa...**  
> ✓ Đã kiểm tra thời tiết  
> ✓ Đã đọc các hoạt động trong lịch trình  
> ! Còn 2 thông tin ảnh hưởng lớn đến danh sách

Người dùng có thể:

- Chờ AI phân tích.
- Bấm **Dừng**.
- Bấm **Tạo bản nháp ngay**.

### Trạng thái AI
AI đang xử lý dữ liệu và thông báo rõ phần nào đã hoàn thành, phần nào còn thiếu.

### Loại feedback
Đây là **explicit system feedback** vì AI nói trực tiếp trạng thái, tiến độ và bước tiếp theo.

---

### Màn hình 2 — AI hỏi thông tin quan trọng

AI hỏi:

> Trong lịch trình có hoạt động tại Langbiang. Bạn dự định di chuyển theo cách nào?

Các lựa chọn:

- Đi bộ hoặc trekking.
- Đi xe Jeep hoặc cáp treo.
- Tôi chưa quyết định.
- Bỏ hoạt động này.

Người dùng chọn:

> Đi bộ hoặc trekking.

AI hỏi tiếp:

> Bạn muốn chuẩn bị hành lý theo phong cách nào?

Các lựa chọn:

- Gọn nhẹ.
- Cân bằng.
- Đầy đủ và có đồ dự phòng.
- Bỏ qua và tạo bản nháp.

### Quyền kiểm soát
Người dùng không bị buộc phải trả lời toàn bộ câu hỏi. Họ có thể bỏ qua và nhận một checklist bản nháp.

### Mức độ tự chủ
**Ask** — AI phải hỏi vì lựa chọn trekking hay đi xe ảnh hưởng đáng kể đến giày, nước uống và đồ chống mưa.

---

### Màn hình 3 — AI tạo checklist bản nháp

Hệ thống hiển thị:

> **Checklist đề xuất — Chưa có món đồ nào được mua hoặc đặt**

#### A. Vật dụng bắt buộc

- [ ] Giấy tờ tùy thân.
- [ ] Quần áo cho 3 ngày.
- [ ] Thuốc và vật dụng cá nhân.
- [ ] Điện thoại và bộ sạc.
- [ ] Tiền mặt hoặc phương thức thanh toán.

#### B. Vật dụng do thời tiết

- [ ] Áo khoác giữ ấm.
- [ ] Áo mưa gọn nhẹ.
- [ ] Túi chống nước cho điện thoại.
- [ ] Một đôi tất dự phòng.

#### C. Vật dụng do hoạt động trekking

- [ ] Giày có độ bám tốt.
- [ ] Bình nước cá nhân.
- [ ] Ba lô nhỏ.
- [ ] Mũ hoặc nón.
- [ ] Kem chống nắng.

Mỗi vật dụng có các lựa chọn:

- **Đã có**
- **Cần chuẩn bị**
- **Không cần**
- **Vì sao AI đề xuất?**

---

### Màn hình 4 — Người dùng xem lý do đề xuất

Người dùng bấm **Vì sao AI đề xuất?** tại mục “Giày có độ bám tốt”.

AI hiển thị:

> Giày có độ bám tốt được đề xuất vì lịch trình có hoạt động đi bộ tại Langbiang và dự báo có khả năng mưa. Thông tin thời tiết được kiểm tra gần nhất vào lúc 09:30 ngày 8/7.

Người dùng có thể:

- Chấp nhận đề xuất.
- Bỏ món đồ.
- Xem nguồn thời tiết.
- Thay đổi hoạt động.
- Báo thông tin không chính xác.

### Explainability
AI hiển thị:

- Dữ liệu thời tiết đã sử dụng.
- Hoạt động dẫn tới đề xuất.
- Thời điểm dữ liệu được cập nhật.
- Phần nào là dữ kiện và phần nào là suy luận.

---

### Màn hình 5 — Người dùng chỉnh sửa checklist

Người dùng chọn:

- Áo mưa: **Đã có**.
- Giày trekking: **Không cần**.
- Bình nước: **Cần chuẩn bị**.

Khi người dùng bỏ giày trekking, AI hỏi:

> Bạn bỏ giày trekking vì lý do nào?

Các lựa chọn:

- Tôi sẽ đi xe Jeep.
- Tôi đã có giày phù hợp.
- Tôi không muốn mang thêm.
- Không cần ghi nhớ lý do.

Người dùng chọn:

> Tôi sẽ đi xe Jeep.

AI xác nhận:

> Đã hiểu: bạn sẽ đi xe Jeep nên tôi đã bỏ các vật dụng dành riêng cho trekking. Thay đổi này chỉ áp dụng cho chuyến Đà Lạt.

### Feedback hai chiều

**User → System, explicit:**

- Người dùng chọn lý do bỏ món đồ.
- Người dùng sửa phương thức tham gia hoạt động.

**System → User, explicit:**

- AI xác nhận đã hiểu thay đổi nào.
- AI nói rõ thay đổi chỉ áp dụng cho chuyến hiện tại.

**User → System, implicit:**

- Hệ thống ghi nhận người dùng thường xuyên chọn chế độ hành lý gọn nhẹ.
- Tín hiệu này không được xem là sở thích lâu dài nếu chưa có xác nhận.

**System → User, implicit:**

- Các món bắt buộc được đặt ở đầu danh sách.
- Các món chưa chắc chắn có biểu tượng cảnh báo.
- Các món do AI suy luận không được đánh dấu mặc định là đã chọn.

---

## 2.3. Trạng thái kết thúc

AI hiển thị:

> **Checklist Đà Lạt đã được cập nhật**
>
> - 8 món đã có.
> - 4 món cần chuẩn bị.
> - 3 món đã bỏ.
> - Không có giao dịch mua sắm nào được thực hiện.

Các nút:

- **Xác nhận checklist**
- **Chỉnh sửa tiếp**
- **Hoàn tác thay đổi**
- **Xuất checklist**
- **Báo đề xuất chưa đúng**

---

## 2.4. Design rationale

### AI đang biết gì?
AI biết điểm đến, thời gian, dự báo thời tiết và các hoạt động hiện có trong lịch trình.

### AI chưa biết gì?
AI chưa biết cách người dùng tham gia hoạt động, những món đồ đã có và mức độ ưu tiên hành lý.

### AI đang đưa ra giả định nào?
AI giả định hoạt động tại Langbiang có thể cần đi bộ và thời tiết mưa làm tăng nhu cầu sử dụng giày có độ bám.

### Điều gì có thể sai?
Dự báo thời tiết có thể thay đổi. Người dùng có thể đi xe thay vì trekking. Một số món đồ người dùng đã có sẵn.

### Hậu quả nếu AI sai
Người dùng có thể mang thừa đồ, quên vật dụng quan trọng hoặc chuẩn bị không phù hợp với hoạt động.

### Sai sót có dễ phát hiện và hoàn tác không?
Có. Người dùng có thể xem lý do, sửa trạng thái từng món và hoàn tác thay đổi.

### AI nên Act, Ask hay Don’t Act?
- **Act:** Tự tạo checklist bản nháp.
- **Ask:** Hỏi về hoạt động và phong cách hành lý.
- **Don’t Act:** Không tự mua đồ hoặc ghi nhớ thông tin lâu dài.

---

# 3. Kịch bản tương tác 2  
## Lịch trình thay đổi, AI cập nhật checklist và giải thích

### 3.1. Bối cảnh ban đầu

Người dùng đã có checklist cho chuyến Nha Trang 4 ngày 3 đêm.

Sau đó, người dùng thay đổi lịch trình:

> Thêm hoạt động lặn ngắm san hô vào sáng ngày 2 và đi đảo cả ngày.

AI phát hiện hoạt động mới có thể làm thay đổi hành trang.

AI đã biết:

- Điểm đến: Nha Trang.
- Thời gian: 4 ngày 3 đêm.
- Hoạt động mới: lặn ngắm san hô và đi đảo.
- Checklist hiện tại của người dùng.

AI chưa biết:

- Người dùng có biết bơi hay không.
- Người dùng muốn thuê hay tự mang dụng cụ.
- Đơn vị tổ chức có cung cấp áo phao, kính lặn và ống thở hay không.
- Người dùng có bị say tàu hay không.

---

## 3.2. Flow tương tác

### Màn hình 1 — AI phát hiện thay đổi

AI hiển thị thông báo:

> **Lịch trình vừa thay đổi**
>
> Tôi phát hiện hoạt động “lặn ngắm san hô” và “đi đảo cả ngày”. Việc này có thể cần thêm đồ bơi, đồ chống nước và phương án chống nắng.

Các lựa chọn:

- **Xem các thay đổi đề xuất**
- **Giữ checklist hiện tại**
- **Tự chỉnh checklist**
- **Bỏ qua lần này**

### Mức độ tự chủ
**Act** — AI được phép phát hiện thay đổi và tạo bản đề xuất vì đây là hành động rủi ro thấp, dễ xem lại và dễ hoàn tác.

AI không được tự đánh dấu rằng người dùng đã đồng ý mang hoặc mua các món mới.

---

### Màn hình 2 — So sánh checklist trước và sau

AI hiển thị hai cột:

| Checklist hiện tại | AI đề xuất thêm |
|---|---|
| Quần áo thường | Đồ bơi |
| Sạc điện thoại | Khăn nhanh khô |
| Kem chống nắng | Túi chống nước |
| Dép thông thường | Dép chống trượt |
| Thuốc cá nhân | Quần áo thay |
|  | Bình nước |
|  | Thuốc chống say tàu — chưa chắc chắn |

#### Dụng cụ có thể không cần mang

- Kính lặn.
- Ống thở.
- Áo phao.

AI giải thích:

> Các dụng cụ chuyên dụng thường có thể được đơn vị tổ chức cung cấp, nhưng tôi chưa xác minh gói dịch vụ của bạn.

### Trạng thái không chắc chắn
Các món chưa được xác minh có nhãn:

> **Cần kiểm tra**

Người dùng có thể bấm:

- **Kiểm tra với nhà cung cấp**
- **Tôi sẽ tự mang**
- **Tôi sẽ thuê**
- **Bỏ khỏi checklist**

---

### Màn hình 3 — AI hỏi lựa chọn mang, thuê hay mua

AI hỏi:

> Bạn muốn xử lý dụng cụ lặn theo cách nào?

Các lựa chọn:

- Tôi sẽ thuê tại điểm lặn.
- Tôi đã có dụng cụ cá nhân.
- Tôi muốn xem món cần mua.
- Tôi chưa quyết định.

#### Nhánh A — Người dùng chọn thuê

Người dùng chọn:

> Tôi sẽ thuê tại điểm lặn.

AI xác nhận:

> Đã bỏ kính lặn và ống thở khỏi danh sách cần mang. Tôi vẫn giữ đồ bơi, khăn và túi chống nước.

#### Nhánh B — Người dùng muốn xem món cần mua

Người dùng chọn:

> Tôi muốn xem món cần mua.

AI hiển thị:

> Tôi có thể mở danh sách tham khảo từ các trang mua sắm bên ngoài. Giá và tình trạng hàng có thể thay đổi. Tôi sẽ không tự thêm sản phẩm vào giỏ hoặc thanh toán.

Các nút:

- **Xem gợi ý mua sắm**
- **Chỉ lưu vào danh sách cần mua**
- **Không cần**

### Mức độ tự chủ
**Ask** — AI phải hỏi trước khi mở liên kết ngoài hoặc sử dụng dữ liệu mua sắm.

**Don’t Act** — AI không tự mua hàng, thanh toán hoặc đặt dịch vụ.

---

### Màn hình 4 — Người dùng phản hồi một đề xuất

Người dùng chọn **Không cần** đối với “Thuốc chống say tàu”.

AI hỏi:

> Lý do bạn không cần món này?

Các lựa chọn:

- Tôi không bị say tàu.
- Tôi đã có sẵn.
- Hoạt động đã thay đổi.
- Tôi không muốn dùng.
- Không muốn trả lời.

Người dùng chọn:

> Tôi không bị say tàu.

AI xác nhận:

> Đã bỏ thuốc chống say tàu khỏi chuyến này.

Sau đó AI hỏi riêng:

> Bạn có muốn ghi nhớ rằng bạn thường không bị say tàu cho các chuyến sau không?

Các lựa chọn:

- Có, ghi nhớ.
- Không, chỉ áp dụng lần này.
- Xem dữ liệu sẽ được lưu.

### Quyền riêng tư
Mặc định được chọn là:

> Không, chỉ áp dụng lần này.

AI chỉ ghi nhớ lâu dài khi người dùng chủ động đồng ý.

---

### Màn hình 5 — Checklist được cập nhật

AI hiển thị:

> **Checklist đã cập nhật**
>
> - Đã thêm 6 món do hoạt động đi đảo.
> - Đã bỏ 2 dụng cụ vì bạn chọn thuê tại điểm lặn.
> - Đã bỏ thuốc chống say tàu theo phản hồi của bạn.
> - Không có giao dịch mua sắm nào được thực hiện.
> - Có thể hoàn tác thay đổi trong 10 phút.

Các nút:

- **Hoàn tác cập nhật**
- **Xem lại thay đổi**
- **Xác nhận checklist**
- **Báo đề xuất chưa đúng**

---

## 3.3. Feedback hai chiều

### User → System, explicit

Người dùng:

- Chọn mang, thuê hay mua.
- Cung cấp lý do bỏ món đồ.
- Quyết định có cho phép ghi nhớ thông tin hay không.
- Báo đề xuất sai hoặc chưa phù hợp.

### User → System, implicit

Hệ thống có thể ghi nhận:

- Người dùng thường bỏ qua link mua sắm.
- Người dùng thường chọn thuê thay vì mang theo.
- Người dùng hoàn tác ngay sau khi checklist được cập nhật.

Tuy nhiên, hệ thống không được mặc định rằng hành vi này phản ánh sở thích lâu dài. Người dùng có thể chỉ thay đổi quyết định trong một chuyến cụ thể.

### System → User, explicit

AI nói rõ:

- Lịch trình nào làm checklist thay đổi.
- Những vật dụng nào được thêm hoặc bỏ.
- Thông tin nào chưa được xác minh.
- Hành động nào mới chỉ là đề xuất.
- Không có giao dịch nào được thực hiện.

### System → User, implicit

Giao diện sử dụng:

- Nhãn **Mới thêm** cho vật dụng mới.
- Nhãn **Cần kiểm tra** cho thông tin chưa chắc chắn.
- Nút **Hoàn tác** đặt gần thông báo cập nhật.
- Các món AI suy luận không được đánh dấu mặc định.
- Liên kết mua sắm có biểu tượng mở trang bên ngoài.

---

## 3.4. Design rationale

### AI đang biết gì?
AI biết lịch trình vừa có thêm hoạt động lặn biển và đi đảo.

### AI chưa biết gì?
AI chưa biết nhà cung cấp có trang bị dụng cụ hay không, người dùng có bị say tàu không và muốn thuê hay mang dụng cụ.

### AI đang đưa ra giả định nào?
AI giả định hoạt động dưới nước cần thêm đồ bơi, đồ chống nước và quần áo thay.

### Điều gì có thể sai?
Nhà cung cấp có thể đã cung cấp toàn bộ dụng cụ. Người dùng có thể không xuống nước. Hoạt động có thể bị huỷ do thời tiết.

### Hậu quả nếu AI sai
Người dùng có thể mang thừa đồ, mua đồ không cần thiết hoặc thiếu vật dụng khi tham gia hoạt động.

### Sai sót có dễ phát hiện và hoàn tác không?
Có. Checklist được hiển thị dưới dạng so sánh trước và sau. Người dùng có thể bỏ từng món hoặc hoàn tác toàn bộ cập nhật.

### AI nên Act, Ask hay Don’t Act?
- **Act:** Phát hiện thay đổi và tạo bản đề xuất.
- **Ask:** Hỏi người dùng muốn mang, thuê hay mua.
- **Don’t Act:** Không tự đặt dịch vụ, mua hàng, thanh toán hoặc lưu dữ liệu lâu dài.

---

# 4. Tổng hợp Act / Ask / Don’t Act

| Mức độ | Hành động trong tính năng | Lý do |
|---|---|---|
| Act | Phân tích thời tiết và lịch trình | Rủi ro thấp, người dùng có thể kiểm tra |
| Act | Tạo checklist bản nháp | Dễ sửa và dễ hoàn tác |
| Act | Phân nhóm vật dụng | Không tạo giao dịch hoặc cam kết |
| Ask | Hỏi về hoạt động và phương tiện | Ảnh hưởng lớn đến vật dụng cần mang |
| Ask | Hỏi người dùng muốn thuê, mang hay mua | Liên quan đến quyết định và chi phí |
| Ask | Xin phép ghi nhớ sở thích | Liên quan đến dữ liệu cá nhân |
| Don’t Act | Tự thêm hàng vào giỏ | Có thể phát sinh chi phí |
| Don’t Act | Tự thanh toán | Rủi ro cao, khó hoàn tác |
| Don’t Act | Tự đặt tour hoặc dịch vụ | Liên quan đến cam kết và thông tin cá nhân |
| Don’t Act | Tự lưu thông tin sức khỏe | Dữ liệu nhạy cảm, cần sự đồng ý rõ ràng |

---

# 5. Các màn hình nên dựng trong prototype

1. Màn hình nhập điểm đến, thời gian và lịch trình.
2. Màn hình AI đang phân tích.
3. Màn hình AI hỏi thông tin còn thiếu.
4. Checklist bản nháp.
5. Lớp giải thích “Vì sao AI đề xuất?”.
6. Màn hình chỉnh sửa trạng thái từng vật dụng.
7. Thông báo lịch trình thay đổi.
8. Màn hình so sánh checklist trước và sau.
9. Hộp thoại lựa chọn mang, thuê hoặc mua.
10. Hộp thoại xin phép ghi nhớ thông tin.
11. Màn hình xác nhận cập nhật.
12. Trạng thái hoàn tác và khôi phục.

---

# 6. Kết quả mong đợi

Sau khi hoàn thành hai kịch bản, prototype cần chứng minh rằng:

- Người dùng hiểu AI đang sử dụng dữ liệu nào.
- Người dùng biết AI còn thiếu hoặc chưa chắc chắn thông tin nào.
- AI không trình bày suy luận như sự thật tuyệt đối.
- Người dùng có thể kiểm tra nguồn và lý do đề xuất.
- Người dùng có thể sửa, từ chối và hoàn tác.
- AI có đủ ba mức tự chủ: Act, Ask và Don’t Act.
- Có feedback hai chiều giữa người dùng và hệ thống.
- Khi AI thiếu thông tin hoặc đề xuất chưa đúng, người dùng vẫn tiếp tục hoàn thành mục tiêu chuẩn bị hành lý.
