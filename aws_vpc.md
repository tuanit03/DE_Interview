
### 1. **Khái niệm cơ bản về VPC**
   - **VPC (Virtual Private Cloud)**: Một mạng riêng ảo mà bạn có thể thiết lập trên AWS. Nó cho phép bạn kiểm soát toàn bộ cấu trúc mạng như việc xác định phạm vi địa chỉ IP, subnet, routing tables, và gateway.
   - **Private và Public Cloud**: Trong VPC, bạn có thể tạo các subnet riêng tư (Private Subnet) hoặc công khai (Public Subnet) để điều chỉnh mức độ truy cập cho các tài nguyên.

### 2. **Các thành phần cơ bản trong AWS VPC**
   - **CIDR Block (Classless Inter-Domain Routing)**: Khi tạo một VPC, bạn cần xác định phạm vi địa chỉ IP cho nó (ví dụ: 10.0.0.0/16). CIDR block này xác định không gian địa chỉ IP mà VPC có thể sử dụng.
   - **Subnets**: Là các phần nhỏ hơn của VPC, mỗi subnet sẽ nằm trong một vùng Availability Zone (AZ) và được sử dụng để tách các tài nguyên. Có thể tạo:
      - **Public Subnet**: Subnet kết nối với Internet Gateway, cho phép tài nguyên truy cập công khai.
      - **Private Subnet**: Subnet không kết nối trực tiếp với Internet Gateway, chỉ cho phép truy cập từ các tài nguyên khác trong VPC.
   - **Internet Gateway (IGW)**: Một thành phần giúp các tài nguyên trong VPC có thể truy cập Internet.
   - **NAT Gateway / NAT Instance**: Được sử dụng để cho phép các instance trong private subnet truy cập Internet mà không cần public IP.
   - **Route Tables**: Bảng định tuyến cho phép điều khiển lưu lượng mạng bên trong VPC. Mỗi subnet được liên kết với một bảng định tuyến.
   - **Network ACL (Access Control List)**: Là một lớp bảo mật bổ sung cho subnet, giúp kiểm soát lưu lượng vào/ra subnet dựa trên các quy tắc.
   - **Security Groups**: Một nhóm bảo mật cấp instance, giúp kiểm soát lưu lượng đến/từ instance.

### 3. **Cách thức hoạt động của AWS VPC**
   - **Kiểm soát địa chỉ IP**: Khi tạo VPC, bạn có thể chọn một dải địa chỉ IP để dùng trong VPC đó, và chia nhỏ thành các subnet với các địa chỉ IP con trong dải này.
   - **Kết nối nội bộ**: Các instance trong cùng VPC có thể giao tiếp với nhau, giúp bạn thiết lập môi trường microservices hoặc các hệ thống phụ thuộc lẫn nhau.
   - **Kết nối bên ngoài**: Để truy cập từ Internet, instance phải nằm trong public subnet, được gán public IP, và có cấu hình route table trỏ đến Internet Gateway.

### 4. **Kiến trúc mạng và bảo mật trong VPC**
   - **Thiết kế Public và Private Subnet**: Tạo cấu trúc kết hợp public và private subnet giúp kiểm soát và bảo vệ dữ liệu. Public subnet thường lưu các dịch vụ công khai như web servers, còn private subnet chứa cơ sở dữ liệu hoặc ứng dụng backend.
   - **Network ACLs và Security Groups**:
      - **Network ACL**: Áp dụng cho subnet, hỗ trợ các quy tắc chấp nhận (allow) và từ chối (deny) truy cập dựa trên địa chỉ IP và port.
      - **Security Group**: Áp dụng cho instance, chỉ hỗ trợ quy tắc chấp nhận truy cập. Thường dùng để bảo vệ các instance khỏi truy cập trái phép.

### 5. **Kết nối giữa VPC và các dịch vụ khác**
   - **VPC Peering**: Cho phép kết nối hai VPC lại với nhau (cùng hoặc khác tài khoản) để tài nguyên trong hai VPC có thể liên lạc.
   - **VPN Gateway**: Kết nối VPC với hệ thống on-premise qua mạng riêng ảo VPN, bảo mật dữ liệu truyền tải giữa các hệ thống.
   - **Direct Connect**: Giải pháp kết nối VPC với hệ thống on-premise qua đường truyền vật lý, thường được dùng khi cần truyền tải dữ liệu lớn và yêu cầu độ trễ thấp.
   - **VPC Endpoints**: Cho phép truy cập dịch vụ AWS (như S3, DynamoDB) mà không cần kết nối với Internet, giúp bảo mật và tiết kiệm chi phí.

### 6. **Routing trong VPC**
   - **Route Tables**: Mỗi subnet trong VPC cần có route table để xác định đường đi của lưu lượng mạng. Route table thường có các route đến Internet Gateway cho public subnet và route đến NAT Gateway hoặc NAT Instance cho private subnet.

### 7. **NAT Gateway và NAT Instance**
   - **NAT Gateway**: Dùng để cung cấp kết nối Internet cho các instance trong private subnet một cách dễ dàng, quản lý tự động và có tính khả dụng cao.
   - **NAT Instance**: Một instance chạy như một NAT Gateway, yêu cầu cấu hình thủ công hơn và ít được sử dụng hơn NAT Gateway.

### 8. **Kịch bản và Mô hình thiết kế VPC**
   - **Single-Tier Architecture**: Tất cả tài nguyên trong cùng một public subnet, phù hợp với ứng dụng nhỏ.
   - **Two-Tier Architecture**: Sử dụng public subnet cho web servers và private subnet cho database servers.
   - **Three-Tier Architecture**: Thiết lập các tầng subnet khác nhau cho web, application và database, giúp cô lập các lớp và tăng bảo mật.

### 9. **Các tính năng nâng cao của VPC**
   - **Elastic IP (EIP)**: Địa chỉ IP tĩnh có thể gán cho instance hoặc NAT Gateway trong VPC, giúp bảo đảm IP không thay đổi khi khởi động lại.
   - **Flow Logs**: Ghi lại thông tin lưu lượng ra vào các interface trong VPC, giúp quản trị viên theo dõi và phân tích các hoạt động mạng.
   - **Bảo mật và giám sát với CloudWatch**: Kết hợp với Amazon CloudWatch để theo dõi hiệu suất và cảnh báo các vấn đề tiềm ẩn trong VPC.

### 10. **Chi phí liên quan**
   - **Chi phí NAT Gateway**: Tính phí theo lưu lượng và thời gian sử dụng.
   - **Chi phí VPN và Direct Connect**: Tính phí dựa trên băng thông và khoảng cách địa lý giữa AWS và hệ thống on-premise.

### 11. **Quản lý và triển khai VPC**
   - **Thiết kế CIDR Block phù hợp**: Lựa chọn CIDR phù hợp để không gian địa chỉ IP không bị xung đột.
   - **Automation với Terraform hoặc CloudFormation**: Sử dụng các công cụ như Terraform hoặc CloudFormation để tạo, triển khai, và quản lý VPC một cách tự động.
