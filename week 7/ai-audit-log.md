# AI Audit Log

## Week 7

| STT | Giai đoạn/Thành phần DTC | Nội dung Prompt (Câu lệnh) | AI Output | Phản hồi của AI & Quyết định của người học (Reflection) |
| --- | --- | --- | --- | --- |
| 1 | Abstraction | "Tôi muốn xây dựng tính năng để Admin dùng AI tạo chiến dịch khuyến mãi cho hệ thống food ordering. AI nên hỗ trợ phần nào và phần nào vẫn phải do Admin quyết định?" | AI đề xuất để AI đóng vai trò trợ lý gợi ý nội dung chiến dịch: tên chiến dịch, mô tả, thông điệp truyền thông, nhóm khách hàng mục tiêu, thời gian gợi ý và ý tưởng ưu đãi. Các quyết định có ảnh hưởng trực tiếp đến tiền như mức giảm giá, ngân sách, điều kiện áp dụng và trạng thái xuất bản vẫn cần Admin kiểm duyệt trước khi lưu. | Quyết định cuối cùng và Lý do: Chọn mô hình AI tạo bản nháp chiến dịch, không tự động publish. Cách này tận dụng AI để tăng tốc viết nội dung và lên ý tưởng, nhưng vẫn giữ Admin là người chịu trách nhiệm cuối cùng với dữ liệu kinh doanh và rủi ro khuyến mãi. |
| 2 | Decomposition | "Tính năng AI tạo chiến dịch cho Admin nên được chia thành những bước nhỏ nào để dễ triển khai trên frontend và backend?" | AI đề xuất chia flow thành: Admin nhập mục tiêu chiến dịch, frontend gửi prompt có cấu trúc, backend gọi AI provider, backend validate output, frontend hiển thị bản nháp, Admin chỉnh sửa, sau đó mới gọi API tạo chiến dịch chính thức. AI cũng khuyên tách API generate draft khỏi API save campaign. | Quyết định cuối cùng và Lý do: Tách rõ hai bước generate và save. Generate chỉ tạo dữ liệu nháp, còn save dùng validator và quyền Admin như form tạo chiến dịch bình thường. Thiết kế này giúp giảm blast radius nếu AI trả về dữ liệu sai hoặc thiếu. |
| 3 | Algorithm | "AI output cho chiến dịch nên có cấu trúc dữ liệu như thế nào để backend dễ validate và frontend dễ render form chỉnh sửa?" | AI đề xuất trả về JSON có các trường rõ ràng như title, description, targetAudience, campaignGoal, suggestedStartDate, suggestedEndDate, discountType, discountValue, conditions và products. Backend nên validate bằng schema trước khi dùng, giới hạn độ dài text và kiểm tra discountValue nằm trong ngưỡng hợp lệ. | Quyết định cuối cùng và Lý do: Chỉ chấp nhận AI output dạng structured data, không dùng text tự do để ghi thẳng vào database. Output phải qua schema validation và sau đó được Admin xem lại trong form. Điều này giúp dữ liệu campaign nhất quán và giảm lỗi khi render UI. |
| 4 | Pattern Recognition | "Những rủi ro thường gặp khi để AI đề xuất chiến dịch khuyến mãi là gì?" | AI chỉ ra các rủi ro như đề xuất mức giảm quá cao, điều kiện mơ hồ, thời gian không hợp lệ, mô tả gây hiểu nhầm, chọn sai nhóm khách hàng hoặc sản phẩm không còn bán. AI khuyên không gửi dữ liệu nhạy cảm cho AI provider và không để AI tự sửa giá, đơn hàng, payment hoặc quyền người dùng. | Quyết định cuối cùng và Lý do: Giới hạn AI ở mức đề xuất nội dung và ý tưởng chiến dịch. Các giá trị liên quan đến giảm giá, sản phẩm áp dụng, thời gian hiệu lực và điều kiện sử dụng phải được kiểm tra bằng rule hệ thống và xác nhận bởi Admin. |
| 5 | Evaluation | "Làm sao kiểm tra tính năng AI tạo chiến dịch cho Admin hoạt động đúng trước khi bàn giao?" | AI đề xuất kiểm thử các trường hợp: prompt đầy đủ, prompt thiếu thông tin, AI trả JSON sai schema, discount vượt giới hạn, ngày kết thúc trước ngày bắt đầu, sản phẩm không tồn tại và lỗi provider timeout. Frontend cần có loading, error state và cho phép Admin chỉnh sửa bản nháp trước khi lưu. | Quyết định cuối cùng và Lý do: Dùng checklist kiểm thử cả happy path và failure path. Chỉ xem tính năng hoàn thành khi AI draft được validate, form Admin chỉnh sửa được, API save vẫn áp dụng rule campaign hiện có và lỗi AI không làm hỏng luồng tạo chiến dịch thủ công. |

## Register

*Trống (Empty)*

## Assignment 2

*Trống (Empty)*

## Assignment 3

*Trống (Empty)*

## Sheet1

*Trống (Empty)*
