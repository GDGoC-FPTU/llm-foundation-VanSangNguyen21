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
> Khi temperature tăng từ 0.0 lên 1.5, độ đa dạng và tính ngẫu nhiên của phản hồi tăng lên. Ở temperature 0.0, mô hình cho ra phản hồi giống nhất (xác định), trong khi ở temperature 1.5, phản hồi trở nên sáng tạo hơn nhưng kém ổn định. Temperature 0.5-1.0 đạt được cân bằng giữa tính nhất quán và tính đa dạng.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Nên đặt temperature khoảng 0.3-0.5 cho chatbot hỗ trợ khách hàng. Lý do là cần độ nhất quán cao và phản hồi có thể dự đoán được, để tránh cung cấp thông tin mâu thuẫn hoặc gây nhầm lẫn cho khách hàng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Giả định mỗi lần gọi có ~175 token input và ~175 token output. Chi phí GPT-4o: (175 × 5 + 175 × 20) / 1M = $0.004375 per call; Chi phí GPT-4o-mini: (175 × 0.15 + 175 × 0.6) / 1M = $0.00013125 per call. GPT-4o đắt hơn khoảng **33 lần**. Tổng chi phí hàng ngày: GPT-4o = $131,250; GPT-4o-mini = $3,937.50.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng cho những ứng dụng yêu cầu suy luận phức tạp, phân tích chuyên sâu, hoặc xử lý văn bản pháp lý/y tế (độ chính xác cao là tối cần thiết). GPT-4o-mini tốt hơn cho những tác vụ đơn giản như phân loại văn bản, trích xuất thông tin cơ bản, hoặc chatbot thường dùng (đủ khả năng nhưng tiết kiệm chi phí).

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming rất quan trọng khi người dùng cần phản hồi tức thì, như trong các chatbot tương tác, trợ lý AI real-time, hoặc ứng dụng truyền thống nhân chat. Streaming tạo cảm giác phản hồi nhanh hơn vì người dùng thấy được nội dung từng chút một, thay vì chờ đợi toàn bộ phản hồi. Ngược lại, non-streaming phù hợp hơn cho xử lý batch (phân tích file lớn, email), các tác vụ backend không cần phản hồi tức thì, hoặc khi cần toàn bộ nội dung trước khi xử lý tiếp (ví dụ: phân tích hoàn chỉnh, tạo báo cáo).


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
