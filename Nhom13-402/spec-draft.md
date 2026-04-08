# SPEC — AI Product Hackathon

**Nhóm:** ___
**Track:** ☐ VinFast · ☑ Vinmec · ☐ VinUni-VinSchool · ☐ XanhSM · ☐ Open

**Problem statement (1 câu):** 
*Bệnh nhân thường gặp khó khăn khi hiểu kết quả khám, đặt lịch tái khám và chuẩn bị trước khi đến bệnh viện; AI giúp giải thích thông tin y khoa, nhắc lịch và hướng dẫn bệnh nhân rõ ràng hơn.*

---

# 1. AI Product Canvas *(Nguyễn Tuấn Kiệt - 2A202600232)*

|             | Value                                                                                                                                                | Trust                                                                                                                           | Feasibility                                                                        |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Câu hỏi** | User nào? Pain gì? AI giải gì?                                                                                                                       | Khi AI sai thì sao? User sửa bằng cách nào?                                                                                     | Cost/latency bao nhiêu? Risk chính?                                                |
| **Trả lời** | *Bệnh nhân. Pain: Không hiểu kết quả khám, quên lịch tái khám, không biết chuẩn bị gì. AI: Giải thích kết quả, nhắc lịch, hướng dẫn trước khi khám.* | *AI sai → Bệnh nhân xem nguồn từ tài liệu chính thức của Vinmec hoặc hỏi lại bác sĩ. Có cảnh báo "AI chỉ mang tính tham khảo".* | *~$0.02/user, latency < 3s. Risk: Giải thích sai thông tin y khoa, gây hiểu nhầm.* |

**Automation hay augmentation?**
☐ Automation · ☑ Augmentation

**Justify:**
*AI hỗ trợ bệnh nhân hiểu thông tin, nhưng quyết định y khoa vẫn thuộc về bác sĩ.*

---

### Learning signal

**1. User correction đi vào đâu?**
___ Feedback của bệnh nhân lưu vào database để cải thiện model giải thích.

**2. Product thu signal gì để biết tốt lên hay tệ đi?**
___ Tỷ lệ bệnh nhân đọc xong hiểu (thumb up/down), số lần hỏi lại cùng một câu hỏi.

**3. Data thuộc loại nào?**
☐ User-specific · ☑ Domain-specific · ☑ Human-judgment · ☐ Real-time · ☐ Khác: ___

**Có marginal value không?**
___ Có. Feedback từ bệnh nhân giúp AI hiểu cách diễn đạt dễ hiểu hơn với người không chuyên.

---

# 2. User Stories — 4 paths *(Mã Khoa Học - 2A202600474)*

### Feature: *AI Patient Assistant (Trợ lý bệnh nhân)*

**Trigger:**
*Bệnh nhân mở app Vinmec và nhấn "Hỏi AI"*

| Path                           | Câu hỏi thiết kế                                           | Mô tả                                                                    |
| ------------------------------ | ---------------------------------------------------------- | ------------------------------------------------------------------------ |
| Happy — AI đúng, tự tin        | User thấy gì? Flow kết thúc ra sao?                        | *AI giải thích kết quả xét nghiệm rõ ràng. Bệnh nhân hiểu và yên tâm.*   |
| Low-confidence — AI không chắc | System báo "không chắc" bằng cách nào? User quyết thế nào? | *AI hiển thị cảnh báo "Thông tin cần bác sĩ xác nhận".*                  |
| Failure — AI sai               | User biết AI sai bằng cách nào? Recover ra sao?            | *AI giải thích sai chỉ số. Bệnh nhân xem link nguồn và hỏi lại bác sĩ.*  |
| Correction — user sửa          | User sửa bằng cách nào? Data đó đi vào đâu?                | *Bệnh nhân chọn "Thông tin không chính xác". Feedback lưu vào hệ thống.* |

---

# 3. Eval metrics + threshold *(Hà Việt Khánh - 2A202600055)*

**Optimize precision hay recall?**
☑ Precision · ☐ Recall

**Tại sao?**
*Trong y tế, thông tin sai có thể gây hoang mang cho bệnh nhân.*

| Metric                       | Threshold | Red flag (dừng khi) |
| ---------------------------- | --------- | ------------------- |
| *Accuracy (giải thích đúng)* | *≥90%*    | *< 80%*             |
| *User satisfaction*          | *≥80%*    | *< 60%*             |
| *Latency*                    | *< 3s*    | *> 8s*              |

---

# 4. Top 3 failure modes *(Trần Ngô Hồng Hà - 2A202600428)*

| # | Trigger                                | Hậu quả                               | Mitigation                         |
| - | -------------------------------------- | ------------------------------------- | ---------------------------------- |
| 1 | *AI giải thích sai kết quả xét nghiệm* | *Bệnh nhân hiểu nhầm tình trạng bệnh* | *Luôn hiển thị nguồn tài liệu gốc* |
| 2 | *Ngôn ngữ y khoa quá phức tạp*         | *Bệnh nhân không hiểu*                | *AI chuyển sang ngôn ngữ đơn giản* |
| 3 | *AI trả lời ngoài phạm vi chuyên môn*  | *Thông tin không đáng tin*            | *Giới hạn domain trả lời*          |

---

# 5. ROI 3 kịch bản *(Nguyễn Việt Trung - 2A202600244)*

|                | Conservative         | Realistic                  | Optimistic                        |
| -------------- | -------------------- | -------------------------- | --------------------------------- |
| **Assumption** | *100 bệnh nhân/ngày* | *500 bệnh nhân/ngày*       | *Toàn bộ Vinmec*                  |
| **Cost**       | *$10/ngày*           | *$50/ngày*                 | *$200/ngày*                       |
| **Benefit**    | *Giảm tải CSKH*      | *Giảm 20% cuộc gọi hỗ trợ* | *Cải thiện trải nghiệm bệnh nhân* |
| **Net**        | *Hòa vốn*            | *ROI 2x*                   | *ROI 5x*                          |

**Kill criteria:**
*Dừng dự án nếu bệnh nhân đánh giá tiêu cực > 40%*

---

# 6. Mini AI spec (1 trang) *(Trần Ngô Hồng Hà - 2A202600428)*

Sản phẩm: Vinmec Patient AI Assistant

Đối tượng: Bệnh nhân sử dụng dịch vụ tại Vinmec

Cơ chế:
AI sử dụng LLM kết hợp RAG để giải thích kết quả khám bệnh, nhắc lịch tái khám và hướng dẫn chuẩn bị trước khi khám.

Hệ thống thuộc dạng Augmentation — AI hỗ trợ bệnh nhân nhưng không thay thế bác sĩ.

Chiến lược dữ liệu:
Xây dựng data flywheel — mỗi lần bệnh nhân phản hồi, dữ liệu được dùng để cải thiện mô hình.

Rủi ro cao nhất:
AI giải thích sai thông tin y khoa.

Giải pháp:
Luôn có link dẫn nguồn để bệnh nhân kiểm tra nhanh.
