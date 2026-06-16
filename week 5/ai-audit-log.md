# AI Audit Log

## Template

| STT | Giai đoạn/Thành phần DTC | Nội dung Prompt (Câu lệnh) | AI Output | Phản hồi của AI & Quyết định của người học (Reflection) |
| --- | --- | --- | --- | --- |
| 1 | Ví dụ: Abstraction | “Tôi cần quản lý thông tin sinh viên cho app quản lý điểm. Hãy liệt kê các thuộc tính cần thiết." | - | Phản hồi: AI liệt kê 20 thuộc tính.<br>Quyết định: Tôi chỉ chọn 10 thuộc tính liên quan đến chức năng đang được yêu cầu từ ứng dụng (CCCD, địa chỉ...) và lược bỏ 10 thuộc tính học thuật vì phù hợp với yêu cầu của ứng dụng |
| 2 | Ví dụ: Process/Algorithm | "Viết hàm C sắp xếp mảng sinh viên theo điểm số bằng Selection Sort." | - | Phản hồi: AI cung cấp code mẫu.<br>Kiểm chứng: Tôi nhận thấy code AI chưa xử lý trường hợp mảng rỗng (Oversimplification). Tôi đã yêu cầu AI tối ưu lại và tự tay bổ sung điều kiện kiểm tra lỗi. |
| 3 | Ví dụ: Pattern Recognition | “So sánh các giải thuật CPU scheduling: FCFS, SJF, Round Robin, Priority. Giải thuật nào tốt nhất?” | - | Phản hồi: AI response Round Robin là “tốt nhất” vì cân bằng giữa throughput và fairness.<br>Kiểm chứng: AI đưa kết luận sai – không có giải thuật “tốt nhất” tuyệt đối (Hallucination). Mỗi giải thuật phù hợp với tình huống/context khác nhau. |
| 4 | Ví dụ: Pattern Recognition + Literature Review | “Tóm tắt 5 bài báo gần đây nhất về anomaly detection trong IoT sensor data.” | - | Phản hồi: AI tóm tắt 5 papers với tên tác giả, năm xuất bản và tóm tắt nội dung.<br>Kiểm chứng: Tìm trên Google Scholar: 2/5 papers AI nêu là không tồn tại (fabrication). Tôi đã thay bằng 2 papers mà tôi đã tìm kiếm trên research gates và đã kiểm chứng trên google scholar. |


## Register

*Trống (Empty)*


## Assignment 2

*Trống (Empty)*


## Assignment 3

*Trống (Empty)*


## Sheet1

*Trống (Empty)*


