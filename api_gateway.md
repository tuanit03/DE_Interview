
### 1. **Khái niệm và Vai trò của API Gateway**
   - **API Gateway** là một dịch vụ quản lý API, cho phép bạn thiết kế các API để kết nối ứng dụng frontend (như ứng dụng web và mobile) với backend (như Lambda, EC2, hay các dịch vụ khác).
   - Nó đóng vai trò là một "cổng vào" (entry point), xử lý các yêu cầu từ người dùng và chuyển tiếp đến các dịch vụ backend. Đồng thời, API Gateway có thể đảm bảo tính bảo mật, kiểm soát truy cập, và quản lý lưu lượng truy cập.

### 2. **Các loại API trong API Gateway**
   - **RESTful API**: Phù hợp cho ứng dụng có nhu cầu giao tiếp HTTP truyền thống. REST API có thể được thiết kế theo các phương pháp RESTful để sử dụng HTTP verbs (GET, POST, PUT, DELETE).
   - **HTTP API**: Một loại REST API nhưng có phí thấp hơn và hiệu suất tốt hơn, chủ yếu dành cho các ứng dụng serverless với nhu cầu HTTP cơ bản.
   - **WebSocket API**: Dùng để hỗ trợ các ứng dụng cần kết nối lâu dài, chẳng hạn như chat, live feed, hoặc các hệ thống phản hồi thời gian thực.

### 3. **Cấu trúc của API trong API Gateway**
   - **API**: Tập hợp các endpoint và các phương thức HTTP cho phép giao tiếp với các dịch vụ backend.
   - **Stage**: Một phiên bản của API được triển khai để phục vụ các môi trường khác nhau (dev, staging, production).
   - **Resource**: Đại diện cho một endpoint URL; có thể là một URI cụ thể (e.g., `/users`, `/items/{itemId}`).
   - **Method**: Tương ứng với các phương thức HTTP (GET, POST, PUT, DELETE, PATCH), mỗi method có thể định tuyến tới một backend cụ thể (AWS Lambda, HTTP endpoint, AWS service proxy).
   - **Integration**: Xác định cách API Gateway kết nối tới backend (có thể là AWS Lambda, HTTP Proxy, hoặc VPC Link).

### 4. **Quy trình Request và Response trong API Gateway**
   - **Request Flow**:
     1. **Client Request**: Client gửi yêu cầu HTTP hoặc WebSocket tới API Gateway.
     2. **Mapping Template**: Chuyển đổi request từ client để phù hợp với định dạng yêu cầu của backend, sử dụng Velocity Template Language (VTL).
     3. **Authorization và Validation**: Yêu cầu có thể qua các bước kiểm tra bảo mật như xác thực (Authorization) và xác thực input (Validation).
     4. **Integration Request**: API Gateway sẽ chuyển request tới backend như AWS Lambda hoặc một endpoint HTTP khác.
   - **Response Flow**:
     1. **Backend Response**: Backend trả về response tới API Gateway.
     2. **Mapping Template**: API Gateway có thể áp dụng một Mapping Template để định dạng lại response.
     3. **Client Response**: Response cuối cùng được gửi về client.

### 5. **Quản lý API với API Gateway**
   - **Authorization (Xác thực và phân quyền)**:
     - **IAM**: Sử dụng các chính sách AWS Identity and Access Management (IAM) để kiểm soát quyền truy cập API.
     - **Lambda Authorizer**: Xác thực bằng cách sử dụng một function AWS Lambda để kiểm tra token hay thông tin xác thực khác.
     - **Cognito User Pools**: Sử dụng Amazon Cognito để quản lý xác thực người dùng với các API yêu cầu thông tin từ người dùng.
   - **Caching**: API Gateway hỗ trợ caching response ở mức Stage để giảm tải cho backend, cải thiện hiệu suất.
   - **Rate Limiting và Throttling**: API Gateway cho phép giới hạn số lượng yêu cầu để bảo vệ backend khỏi quá tải.

### 6. **Tích hợp với Backend (Integrations)**
   - **AWS Lambda**: Xây dựng các API serverless, nơi các function Lambda xử lý request từ client mà không cần server.
   - **HTTP**: Kết nối tới các endpoint HTTP hoặc HTTPS bên ngoài AWS.
   - **AWS Service Proxy**: Tạo API để truy cập trực tiếp các dịch vụ AWS (như S3, DynamoDB) mà không cần qua một server trung gian.
   - **VPC Link**: Cho phép API Gateway kết nối tới các dịch vụ backend trong Amazon VPC mà không cần phơi bày VPC ra internet.

### 7. **Security (Bảo mật)**
   - **API Keys**: Cung cấp cho khách hàng các API keys để quản lý truy cập và định tuyến.
   - **Custom Domain Names**: Định cấu hình tên miền tùy chỉnh cho API thay vì sử dụng domain mặc định của AWS.
   - **TLS/SSL Certificates**: Sử dụng SSL/TLS để mã hóa kết nối từ client tới API Gateway.

### 8. **Monitoring và Logging**
   - **Amazon CloudWatch Logs và Metrics**: API Gateway cung cấp log và metrics thông qua CloudWatch, bao gồm request counts, latencies, error rates để giám sát hiệu suất và xử lý sự cố.
   - **Access Logs**: Ghi lại thông tin chi tiết của mỗi yêu cầu đến API, bao gồm headers, body, và các thông tin khác.

### 9. **Deployment (Triển khai)**
   - **Stage Variables**: Sử dụng biến cho từng stage (như dev, staging, production) để cấu hình linh hoạt cho API, có thể thay đổi backend mà không cần sửa code.
   - **Canary Release**: Cho phép triển khai API mới với tỷ lệ người dùng nhất định để thử nghiệm và kiểm tra trước khi áp dụng rộng rãi.

### 10. **Thực tiễn tốt khi sử dụng API Gateway**
   - **Thiết kế API**: Đảm bảo RESTful và dễ bảo trì, tận dụng HTTP verbs đúng cách.
   - **Thử nghiệm API**: Sử dụng các công cụ như Postman để kiểm tra API, đặc biệt là các mapping template và authorizer.
   - **Tối ưu hóa Caching và Rate Limiting**: Giảm tải backend và cải thiện tốc độ phản hồi.
   - **Documenting API**: Sử dụng Swagger hoặc các công cụ khác để tự động tạo tài liệu API, giúp người dùng và các developer dễ dàng hiểu và sử dụng API.
