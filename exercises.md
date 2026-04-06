# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature tăng từ 0.0 lên 1.5, câu trả lời chuyển từ ổn định, an toàn sang đa dạng và sáng tạo hơn. Ở mức thấp (0.0–0.5), nội dung thường nhất quán và ít biến thể; ở mức cao (1.0–1.5), mô hình dễ đưa thêm chi tiết bất ngờ hoặc cách diễn đạt phong phú hơn. Đổi lại, temperature cao cũng làm câu trả lời kém đồng nhất giữa các lần chạy.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Mình sẽ đặt khoảng 0.2–0.4 (ưu tiên 0.3) để câu trả lời ổn định, đúng chính sách và dễ kiểm soát. Chatbot hỗ trợ khách hàng cần độ chính xác và nhất quán cao hơn là sáng tạo, nên temperature thấp là phù hợp.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Tổng token mỗi ngày: 10,000 x 3 x 350 = 10,500,000 token (tức 10,500 đơn vị 1K token). Chi phí GPT-4o: 10,500 x 0.010 = 105 USD/ngày; GPT-4o-mini: 10,500 x 0.0006 = 6.3 USD/ngày. Vậy GPT-4o đắt hơn khoảng 105 / 6.3 = 16.67 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi xử lý tác vụ đòi hỏi chất lượng lập luận cao và rủi ro sai sót lớn, ví dụ trợ lý phân tích hợp đồng hoặc tổng hợp báo cáo chiến lược cho quản lý. GPT-4o-mini phù hợp cho workload lớn, lặp lại, yêu cầu phản hồi nhanh và chi phí thấp như FAQ chăm sóc khách hàng, phân loại ticket cơ bản, hoặc gợi ý nội dung ngắn.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các trải nghiệm hội thoại thời gian thực (chatbot, trợ lý hỗ trợ trực tiếp) vì người dùng thấy phản hồi xuất hiện ngay, giảm cảm giác chờ đợi và tăng độ mượt UX. Ngược lại, non-streaming phù hợp khi hệ thống cần toàn bộ kết quả hoàn chỉnh trước khi xử lý tiếp, ví dụ lưu log cuối cùng, kiểm duyệt nội dung, xuất báo cáo định dạng cố định, hoặc khi frontend chỉ hiển thị kết quả sau cùng thay vì từng phần.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
