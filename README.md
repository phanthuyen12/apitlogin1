# ThuyenKlogin API

API quản lý profile cho ứng dụng WPF.

## Base URL

http://localhost:5000

yaml
Copy
Edit

---

## Endpoints

### 1. Tạo Profile mới

**POST** `/api/test/create-profile`

**Mô tả:** Tạo profile với thông tin proxy và tên profile.

**Request Body (JSON):**
```json
{
  "ProfileName": "Thuyendev4344n3gay24",
  "ListProxy": "nova.tunproxy.net:35313",
  "HostProxy": "nova.tunproxy.net",
  "PortProxy": 35313,
  "UsernameProxy": "adVAYF",
  "PasswordProxy": "jBVLyIZC"
}
Response (200 OK):

json
Copy
Edit
{
  "message": "Profile 'Thuyendev4344n3gay24' đã tạo thành công!",
  "profileId": "98d06c79-0e7b-4871-b24c-43299223dffe",
  "createdAt": "24-08-2025 17:00:37"
}
Ví dụ curl:

bash
Copy
Edit
curl -X POST http://localhost:5000/api/test/create-profile \
-H "Content-Type: application/json" \
-d '{"ProfileName":"Thuyendev4344n3gay24","ListProxy":"nova.tunproxy.net:35313","HostProxy":"nova.tunproxy.net","PortProxy":35313,"UsernameProxy":"adVAYF","PasswordProxy":"jBVLyIZC"}'
2. Khởi động Profile
POST /api/test/start-profile

Mô tả: Bắt đầu profile dựa trên ProfileId.

Request Body (JSON):

json
Copy
Edit
{
  "ProfileId": "98d06c79-0e7b-4871-b24c-43299223dffe"
}
Response (200 OK):

json
Copy
Edit
{
  "status": "success",
  "profileId": "98d06c79-0e7b-4871-b24c-43299223dffe",
  "result": "http://localhost:54005/json/version"
}
Ví dụ curl:

bash
Copy
Edit
curl -X POST http://localhost:5000/api/test/start-profile \
-H "Content-Type: application/json" \
-d '{"ProfileId":"98d06c79-0e7b-4871-b24c-43299223dffe"}'
3. Dừng Profile
POST /api/test/stop-profile

Mô tả: Dừng profile đang chạy dựa trên ProfileId.

Request Body (JSON):

json
Copy
Edit
{
  "ProfileId": "98d06c79-0e7b-4871-b24c-43299223dffe"
}
Response (200 OK):

json
Copy
Edit
{
  "status": "success",
  "profileId": "98d06c79-0e7b-4871-b24c-43299223dffe"
}
Ví dụ curl:

bash
Copy
Edit
curl -X POST http://localhost:5000/api/test/stop-profile \
-H "Content-Type: application/json" \
-d '{"ProfileId":"98d06c79-0e7b-4871-b24c-43299223dffe"}'
