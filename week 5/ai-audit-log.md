# AI Audit Log

## Template

| STT | Giai đoạn/Thành phần DTC | Nội dung Prompt (Câu lệnh) | AI Output | Phản hồi của AI & Quyết định của người học (Reflection) |
| --- | --- | --- | --- | --- |
| 1 | Abstraction | "Chúng tôi muốn thay thế đăng nhập Facebook bằng đăng nhập Google trong ứng dụng React + Vite + Node.js (Express). Chúng tôi nên sử dụng nút iframe chính thức của Google hay nút tự thiết kế (custom button) kết hợp với bộ thư viện Google Identity Services Client SDK (initTokenClient)?" | AI khuyên nên sử dụng nút Iframe chính thức của Google (google.accounts.id.renderButton) để đảm bảo tính bảo mật cao nhất (sử dụng luồng OIDC ID Token / JWT) và dễ dàng cài đặt tính năng tự động đăng nhập nhanh (Google One Tap). | Quyết định cuối cùng và Lý do: Quyết định sử dụng Nút tự thiết kế (Custom Button) + Luồng lấy Access Token (Implicit Flow). Giải pháp này vừa đáp ứng 100% yêu cầu về mặt thẩm mỹ vừa bảo mật tuyệt đối nhờ cơ chế xác thực Access Token trực tiếp từ Server của chúng ta tới máy chủ Google. |
| 2 | Algorithm | "Viết một biểu thức chính quy (regex) và một hàm kiểm tra để xác thực mật khẩu mạnh (tối thiểu 8 ký tự, 1 chữ viết hoa, 1 số, 1 ký tự đặc biệt) và kiểm tra mật khẩu mới không trùng với mật khẩu cũ." | AI đề xuất sử dụng một biểu thức chính quy duy nhất ^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$ và sử dụng hàm compare của thư viện bcrypt để so sánh trực tiếp mật khẩu mới với mã hash mật khẩu cũ trong controller của backend. | Quyết định cuối cùng và Lý do: Quyết định tách biệt logic xác thực: Giao diện (UI) xử lý checklist thời gian thực để định hướng tốt cho người dùng, Backend áp dụng Zod schema linh hoạt với tập ký tự đặc biệt mở rộng và so sánh bcrypt chống trùng lặp mật khẩu cũ. |
| 3 | Pattern Recognition | "Tại sao Mongoose lại trả về lỗi xác thực cho các tài liệu con (subdocuments) trống trong mảng 'addresses' khi cập nhật thông tin hồ sơ người dùng, mặc dù người dùng không hề chỉnh sửa địa chỉ của họ?" | AI trả lời rằng lỗi xảy ra vì trường addresses không được cấu hình required: false trong Mongoose schema, hoặc do request cập nhật đang gửi lên một đối tượng trống {}. AI khuyên nên sửa schema thành default: undefined cho mảng addresses. | Quyết định cuối cùng và Lý do: Quyết định áp dụng khai báo mảng tường minh kết hợp pre-validate hook làm sạch dữ liệu. Đây là giải pháp tối ưu giúp hệ thống tự phục hồi dữ liệu cũ mà không cần chạy migration database phức tạp hay làm mất cấu trúc mảng rỗng mặc định. |


## Register

*Trống (Empty)*


## Assignment 2

*Trống (Empty)*


## Assignment 3

*Trống (Empty)*


## Sheet1

*Trống (Empty)*


