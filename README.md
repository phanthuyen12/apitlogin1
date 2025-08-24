ThuyenKlogin API Documentation
Chào mừng bạn đến với tài liệu API của ThuyenKlogin. API này cho phép bạn quản lý các profile trình duyệt cho ứng dụng WPF, bao gồm việc tạo, khởi chạy và dừng các profile một cách tự động.

Base URL
Tất cả các URL được tham chiếu trong tài liệu này đều có URL cơ sở là:

http://localhost:5000
Endpoints
1. Create a New Profile
Endpoint này tạo một profile trình duyệt mới với tên và cấu hình proxy được chỉ định.

POST /api/test/create-profile

Request Body
Parameter	Type	Description	Required
ProfileName	string	Tên định danh duy nhất cho profile.	Yes
ListProxy	string	Chuỗi proxy đầy đủ theo định dạng host:port.	Yes
HostProxy	string	Tên miền hoặc địa chỉ IP của proxy.	Yes
PortProxy	integer	Cổng của máy chủ proxy.	Yes
UsernameProxy	string	Tên người dùng để xác thực proxy.	Yes
PasswordProxy	string	Mật khẩu để xác thực proxy.	Yes

Xuất sang Trang tính
Example Request
Bash

curl -X POST http://localhost:5000/api/test/create-profile \
-H "Content-Type: application/json" \
-d '{
  "ProfileName": "Thuyendev4344n3gay24",
  "ListProxy": "nova.tunproxy.net:35313",
  "HostProxy": "nova.tunproxy.net",
  "PortProxy": 35313,
  "UsernameProxy": "adVAYF",
  "PasswordProxy": "jBVLyIZC"
}'
Success Response (200 OK)
Trả về một đối tượng JSON chứa thông báo thành công, ID của profile mới và dấu thời gian.

JSON

{
  "message": "Profile 'Thuyendev4344n3gay24' đã tạo thành công!",
  "profileId": "98d06c79-0e7b-4871-b24c-43299223dffe",
  "createdAt": "24-08-2025 17:00:37"
}
profileId: ID này rất quan trọng, hãy lưu lại để sử dụng cho các yêu cầu khởi động và dừng profile.

2. Start a Profile 🚀
Khởi chạy một profile đã được tạo trước đó bằng ProfileId của nó.

POST /api/test/start-profile

Request Body
Parameter	Type	Description	Required
ProfileId	string	ID của profile cần khởi động.	Yes

Xuất sang Trang tính
Example Request
Bash

curl -X POST http://localhost:5000/api/test/start-profile \
-H "Content-Type: application/json" \
-d '{
  "ProfileId": "98d06c79-0e7b-4871-b24c-43299223dffe"
}'
Success Response (200 OK)
Trả về trạng thái thành công và một URL gỡ lỗi (debugging URL) mà bạn có thể sử dụng để kết nối với phiên trình duyệt đang chạy.

JSON

{
  "status": "success",
  "profileId": "98d06c79-0e7b-4871-b24c-43299223dffe",
  "result": "http://localhost:54005/json/version"
}
3. Stop a Profile 🛑
Dừng một profile đang chạy dựa trên ProfileId của nó.

POST /api/test/stop-profile

Request Body
Parameter	Type	Description	Required
ProfileId	string	ID của profile cần dừng.	Yes

Xuất sang Trang tính
Example Request
Bash

curl -X POST http://localhost:5000/api/test/stop-profile \
-H "Content-Type: application/json" \
-d '{
  "ProfileId": "98d06c79-0e7b-4871-b24c-43299223dffe"
}'
Success Response (200 OK)
Trả về một thông báo xác nhận rằng profile đã được dừng thành công.

JSON

{
  "status": "success",
  "profileId": "98d06c79-0e7b-4871-b24c-43299223dffe"
}






