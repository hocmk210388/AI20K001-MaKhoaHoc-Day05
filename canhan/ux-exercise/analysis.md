# Bài tập UX: phân tích sản phẩm AI thật

Thời gian: 40 phút | Cá nhân | Output: sketch giấy, nộp cuối bài

---

## Chọn 1 sản phẩm

| Sản phẩm | AI feature | Truy cập |
|---|---|---|
| Vietnam Airlines — Chatbot NEO | Chatbot hỗ trợ hỏi đáp, tra cứu chuyến bay | Website + Zalo |

---

## Phần 1 — Khám phá (15 phút)

Trước khi dùng: tìm hiểu sản phẩm marketing AI feature này thế nào — website, app store, bài PR. Sản phẩm hứa gì?

Rồi dùng thử: tải app / mở web, thử các tính năng AI. Quan sát kỹ: AI phản ứng thế nào? UI thay đổi gì? Có nút gì xuất hiện / biến mất?

### AI feature (theo marketing)
- Chatbot NEO hỗ trợ:
  - Hỏi đáp chuyến bay
  - Tra cứu vé
  - Hỗ trợ đặt vé
- Truy cập: website + Zalo

### Trải nghiệm thực tế
- Khi hỏi:
  - “Chuyến bay Hà Nội → Đà Nẵng ngày mai”
    → Bot trả về danh sách chuyến bay (OK)
- Khi hỏi phức tạp:
  - “Vé rẻ nhất + giờ đẹp + hành lý 20kg”
    → Bot không hiểu rõ context, trả lời chung chung

###  Nhận xét
- AI hoạt động tốt với query đơn giản
- Kém với multi-intent / ngữ cảnh phức tạp
- UI: giống chatbot FAQ hơn là AI “thông minh”

---

## Phần 2 — Phân tích 4 paths (10 phút)

Dùng framework 4 paths để mở sản phẩm:

| Path | Câu hỏi |
|---|---|
| 1. Khi AI đúng | User thấy gì? Hệ thống confirm thế nào? |
| 2. Khi AI không chắc | Hệ thống xử lý thế nào? Im lặng? Hỏi lại? Show alternatives? |
| 3. Khi AI sai | User biết bằng cách nào? Sửa bằng cách nào? Bao nhiêu bước? |
| 4. Khi user mất tin | Có exit không? Có fallback (con người, manual)? Dễ tìm không? |

### Áp dụng cho Chatbot NEO

#### 1. Khi AI đúng
- Hiển thị danh sách chuyến bay rõ ràng
- Có nút CTA (đặt vé)

 Confirm tốt, dễ hiểu

---

#### 2. Khi AI không chắc
- Trả lời kiểu:
  “Bạn vui lòng cung cấp thêm thông tin”
- Không gợi ý cụ thể cần gì

 UX chưa tốt:
- Không có suggestion (ngày, điểm đi…)
- User phải đoán

---

#### 3. Khi AI sai
- Ví dụ: hỏi combo (giờ + giá + hành lý)
- Bot trả về info không liên quan

 Vấn đề:
- Không báo “tôi không hiểu”
- Không có cách sửa nhanh

---

#### 4. Khi user mất niềm tin
- Không có human fallback rõ ràng ngay
- Không có escalation (chuyển người thật nhanh)

 UX yếu:
- User dễ bỏ cuộc
- Không có “trust recovery”

---

### Tự phân tích
-  Path tốt nhất: Path 1 (AI đúng) → flow rõ ràng, có action ngay
-  Path yếu nhất: Path 3 + 4 → sai nhưng không nhận sai, không cứu user

###  Marketing vs thực tế
- Marketing: “AI chatbot thông minh”
- Thực tế: gần giống rule-based bot + search

---

## Phần 3 — Sketch “làm tốt hơn” (10 phút)

Chọn 1 path yếu nhất mà mình tìm được. Sketch trên giấy:

- As-is (bên trái): user journey hiện tại → đánh dấu chỗ gây bực
- To-be (bên phải): user journey đề xuất → vẽ kế bên
- Ghi rõ: thêm gì? Bớt gì? Đổi gì?

---

###  Chọn path yếu nhất: Khi AI sai

####  As-is (hiện tại)
User: “Vé rẻ nhất + giờ đẹp + hành lý 20kg”  
↓  
Bot: trả info chung chung  
↓  
User: bối rối → bỏ  

---

####  To-be (đề xuất)

User: “Vé rẻ nhất + giờ đẹp + hành lý 20kg”  
↓  
Bot:
“Mình hiểu bạn muốn tìm vé tối ưu  
Bạn chọn giúp mình
- Ngày bay
- Điểm đi/đến
- Ưu tiên: rẻ nhất / giờ đẹp”

↓  
User chọn nhanh (button UI)  
↓  
Bot trả kết quả chuẩn + highlight:
- Vé rẻ nhất 
- Giờ đẹp 
- Có hành lý 

---

###  Cải tiến chính
- Detect multi-intent
- Gợi ý input thay vì hỏi chung chung
- Button thay vì text
- Explain “tôi hiểu gì”

---

###  Bonus cải tiến
- “Bạn muốn mình chọn giúp không?” (AI recommendation)
- “Chuyển sang nhân viên” (1 click)

---

###  Kết luận nhanh
- NEO hiện tại = Automation (FAQ bot)
- Chưa phải Augmentation AI thật
- Muốn tốt hơn → cần:
  - hiểu ngữ cảnh
  - gợi ý thông minh
  - fallback rõ ràng