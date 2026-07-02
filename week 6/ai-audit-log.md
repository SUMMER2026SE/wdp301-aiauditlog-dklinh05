# AI Audit Log

## Week 6

| STT | Giai đoạn/Thành phần DTC | Nội dung Prompt (Câu lệnh) | AI Output | Phản hồi của AI & Quyết định của người học (Reflection) |
| --- | --- | --- | --- | --- |
| 1 | Abstraction | "Trong trang checkout của ứng dụng food ordering, khi người dùng nhập địa chỉ giao hàng thì hệ thống nên gợi ý chi nhánh gần hơn như thế nào để không làm mất chi nhánh hiện tại đang chọn?" | AI đề xuất tách khái niệm chi nhánh đang chọn và chi nhánh gợi ý. Danh sách chi nhánh nên được sắp xếp theo khoảng cách, nhưng chi nhánh hiện tại vẫn được giữ ở đầu danh sách và có nhãn trạng thái riêng. Chi nhánh gần nhất được đánh dấu để người dùng dễ so sánh trước khi đổi. | Quyết định cuối cùng và Lý do: Áp dụng flow gợi ý chi nhánh gần hơn nhưng không tự động đổi chi nhánh. Cách này giữ quyền kiểm soát cho người dùng, giảm rủi ro giỏ hàng thay đổi bất ngờ, đồng thời vẫn giúp chọn chi nhánh tối ưu theo địa chỉ giao hàng. |
| 2 | Pattern Recognition | "Vì sao một món trong giỏ hàng bị đánh dấu hết hàng khi đổi sang chi nhánh khác, dù chi nhánh mới vẫn có cùng món đó đang bán?" | AI nhận diện nguyên nhân là cart item có thể đang lưu productId global hoặc productId override của chi nhánh cũ. Nếu chỉ kiểm tra đúng productId đã lưu, hệ thống sẽ bỏ sót bản ghi override đang active ở chi nhánh mới. AI khuyên match món bằng product identity ổn định như category + name sau khi normalize, rồi resolve sang product của chi nhánh hiện tại. | Quyết định cuối cùng và Lý do: Không dùng riêng productId cũ để kết luận availability. Frontend dùng danh sách sản phẩm visible của chi nhánh hiện tại để sync trạng thái giỏ hàng, còn backend resolve lại item theo store override trước khi validate giá và trạng thái. |
| 3 | Algorithm | "Khi có một số món hết tại chi nhánh checkout mới, thuật toán nên tính tổng tiền và tạo payload đặt hàng như thế nào?" | AI đề xuất chia cart item thành nhóm khả dụng và không khả dụng. Món không khả dụng vẫn hiển thị để người dùng biết ảnh hưởng khi đổi chi nhánh, nhưng bị grayscale, không tính vào subtotal/total và không được đưa vào payload tạo đơn. Nút đặt hàng chỉ enable khi còn ít nhất một món khả dụng. | Quyết định cuối cùng và Lý do: Giữ món hết hàng trong UI nhưng loại khỏi tổng tiền và payload checkout. Backend vẫn là nguồn sự thật, tiếp tục tự tính giá, phí giao hàng, discount, tổng thanh toán và reject nếu món hết/ngừng bán tại thời điểm tạo đơn. |
| 4 | Decomposition | "Làm thế nào để Staff chỉ được xem và thao tác đơn hàng, chat hỗ trợ trong đúng chi nhánh được gán, thay vì tin storeId client gửi lên?" | AI đề xuất tách bài toán thành middleware scope, service query, controller handler và route bảo vệ. Middleware lấy storeId thật từ authenticated user trong database, so sánh optional storeId từ client nếu có, sau đó gắn scope vào request. Service chỉ query order/chat theo storeId đã xác thực. | Quyết định cuối cùng và Lý do: Triển khai store scope phía backend cho Staff và cập nhật frontend để Staff lấy storeId từ auth context. Client không còn là nguồn tin cậy cho phạm vi chi nhánh; nếu storeId lệch thì trả 403. Cách này giảm rủi ro Staff xem nhầm dữ liệu chi nhánh khác. |
| 5 | Abstraction | "Cần thiết kế tính năng quản lý cửa hàng như thế nào để Admin quản lý toàn hệ thống còn Manager chỉ cập nhật chi nhánh của mình?" | AI đề xuất phân quyền rõ: Admin có API/page quản lý toàn bộ store với danh sách, tạo, sửa, activate/deactivate; Manager chỉ có form cập nhật thông tin cơ bản của store được gán. Backend cần validator riêng cho create/update store và route riêng theo role. | Quyết định cuối cùng và Lý do: Tách usecase Admin Store Management và Manager Store Settings. Admin được quản trị toàn cục, Manager chỉ thao tác trên store scope của chính mình. Thiết kế này giữ đúng ranh giới quyền và tránh mở rộng quyền Manager quá mức. |

## Register

*Trống (Empty)*

## Assignment 2

*Trống (Empty)*

## Assignment 3

*Trống (Empty)*

## Sheet1

*Trống (Empty)*
