
### 1. **Giới thiệu AWS Lambda**

   - **Khái niệm**: AWS Lambda là một dịch vụ "event-driven" và không cần quản lý hạ tầng. Lambda cho phép bạn chạy mã dựa trên sự kiện (events) mà không cần cấu hình hoặc duy trì các máy chủ.
   - **Tính không máy chủ**: Bạn chỉ cần viết mã và triển khai, không phải lo về việc phân bổ, vận hành hay mở rộng quy mô của máy chủ.

### 2. **Nguyên lý Hoạt động**

   - Lambda thực thi mã của bạn để phản hồi các sự kiện từ các dịch vụ AWS khác như S3, DynamoDB, API Gateway, hoặc từ sự kiện tùy chỉnh.
   - Khi sự kiện xảy ra, Lambda tự động kích hoạt và thực hiện mã trong một container, và sau khi hoàn thành, container này sẽ tự động bị đóng.

### 3. **Kiến trúc AWS Lambda**

   - **Event Source**: Sự kiện có thể đến từ các dịch vụ như S3 (thay đổi đối tượng), DynamoDB (thay đổi bảng), API Gateway (yêu cầu HTTP), hoặc các dịch vụ khác như SNS, SQS.
   - **Function**: Đây là mã thực thi của bạn, thường được viết bằng các ngôn ngữ như Python, Node.js, Java, hoặc Go.
   - **Execution Environment**: Môi trường mà AWS Lambda chạy mã của bạn. Môi trường này bao gồm cấu hình hệ điều hành, các thư viện cần thiết và runtime.
   - **Handler**: Là điểm bắt đầu của mã, thường là một hàm thực hiện các nhiệm vụ chính của Lambda function khi nhận được sự kiện.
   - **Permissions (IAM Roles)**: Lambda sử dụng IAM role để xác định quyền truy cập của function vào các tài nguyên AWS khác.
   - **Layers**: Tầng cho phép bạn chia sẻ mã và thư viện giữa nhiều Lambda function, giảm bớt sự trùng lặp và kích thước của mã.

### 4. **Cách thức Triển khai Lambda Function**

   - **Viết Code**: Bạn có thể viết mã trực tiếp trong giao diện AWS Lambda Console hoặc chuẩn bị và tải lên các file nén (.zip) hoặc file chứa mã (JAR cho Java).
   - **Quản lý Bản Cập Nhật**: Lambda hỗ trợ cập nhật các version, cho phép bạn triển khai từng phiên bản và sử dụng "aliases" để quản lý dễ dàng.
   - **Triển khai qua các công cụ CI/CD**: Lambda tích hợp với các công cụ như AWS CodePipeline, CodeDeploy, và các công cụ CI/CD khác để tự động hóa việc triển khai.

### 5. **Cấu hình AWS Lambda**

   - **Memory Allocation**: AWS Lambda cho phép bạn cấu hình lượng RAM cần thiết, từ 128 MB đến 10 GB. CPU và dung lượng lưu trữ tạm thời sẽ được tự động điều chỉnh dựa trên RAM.
   - **Timeout**: Thời gian tối đa mà Lambda function có thể chạy, từ 1 giây đến 15 phút.
   - **Concurrency**: Số lượng phiên bản của Lambda có thể chạy đồng thời. Có thể thiết lập "reserved concurrency" để hạn chế số phiên bản chạy cùng lúc cho một function.
   - **Environment Variables**: Lambda cho phép bạn thiết lập các biến môi trường để lưu thông tin cấu hình.

### 6. **Các Ngôn Ngữ và Runtime Hỗ Trợ**

   - **Ngôn ngữ**: Lambda hỗ trợ nhiều ngôn ngữ như Python, Node.js, Java, Go, Ruby, .NET Core.
   - **Custom Runtime**: Lambda cũng cho phép bạn tạo custom runtime, giúp chạy các ngôn ngữ không chính thức hỗ trợ như PHP, Rust.

### 7. **Tính năng Event-driven**

   Lambda hoạt động dựa trên sự kiện, kích hoạt mã khi có sự kiện từ các nguồn khác nhau:
   
   - **API Gateway**: Xử lý các yêu cầu HTTP/HTTPS và trả về phản hồi.
   - **S3 Events**: Thực thi khi có thay đổi trong các bucket của S3, như upload file mới.
   - **DynamoDB Streams**: Kích hoạt khi có thay đổi trong bảng DynamoDB.
   - **Scheduled Events**: Sử dụng CloudWatch Events để định lịch, ví dụ chạy mã mỗi giờ.

### 8. **Bảo mật và Quyền Hạn**

   - **IAM Role**: Lambda function cần IAM role để quản lý quyền truy cập vào các tài nguyên AWS khác, như S3 hoặc DynamoDB.
   - **VPC (Virtual Private Cloud)**: Lambda có thể cấu hình để chạy bên trong VPC, cho phép kết nối với tài nguyên trong mạng riêng ảo nhưng vẫn an toàn.

### 9. **Giá cả (Pricing)**

   - **Execution Time**: Chi phí tính theo thời gian chạy của mỗi request và số lượng RAM được cấp phát, tính bằng giây.
   - **Requests**: Lambda miễn phí cho 1 triệu yêu cầu đầu tiên hàng tháng và tính phí cho các yêu cầu vượt quá.
   - **Duration**: Lambda tính phí dựa trên thời gian thực thi (tối thiểu là 1ms), với các yếu tố khác như số lần gọi và RAM cấp phát.

### 10. **Các Trường hợp Sử dụng AWS Lambda**

   - **Web API**: Dùng với API Gateway để xây dựng REST API mà không cần máy chủ.
   - **Xử lý Tệp tin và Dữ liệu**: Chạy các tác vụ xử lý ảnh, video, hoặc dữ liệu khi có file mới tải lên S3.
   - **Tự động hóa IT**: Tự động hóa các tác vụ bảo trì và quản lý hệ thống.
   - **IoT**: Xử lý dữ liệu từ các thiết bị IoT và phân tích thời gian thực.
   - **Xử lý Dữ liệu Thời gian Thực**: Xử lý stream dữ liệu, logs, hoặc dữ liệu analytics từ Kinesis hoặc DynamoDB Streams.

### 11. **Tối ưu hóa Lambda Function**

   - **Reduce Cold Start Time**: Cải thiện thời gian phản hồi bằng cách giảm kích thước gói cài đặt và chỉ load các thư viện cần thiết.
   - **Optimize Memory and Timeout**: Tối ưu hóa bộ nhớ cấp phát và timeout để giảm chi phí và cải thiện hiệu suất.
   - **Provisioned Concurrency**: Đảm bảo có sẵn các instance "ấm" của Lambda function để xử lý các yêu cầu tức thời.
   - **Use Layers**: Sử dụng Lambda Layers để quản lý và chia sẻ thư viện giữa các function, giảm thời gian deploy và kích thước package.

### 12. **Giới hạn của AWS Lambda**

   - **Execution Time**: Giới hạn tối đa 15 phút cho mỗi function.
   - **Deployment Package Size**: Tối đa 50 MB khi upload trực tiếp, và 250 MB khi sử dụng S3.
   - **Environment Variables**: Giới hạn 4 KB cho biến môi trường.
   - **Concurrent Execution**: Có giới hạn số lượng instance chạy đồng thời, phải quản lý để tránh vượt quá.

### 13. **Một số Thực hành Tốt khi Sử dụng AWS Lambda**

   - **Sử dụng các IAM Role tối thiểu**: Đảm bảo chỉ cung cấp các quyền cần thiết cho Lambda để tăng tính bảo mật.
   - **Tránh lưu trữ dữ liệu trong /tmp**: Thư mục tạm `/tmp` sẽ bị xóa khi Lambda kết thúc.
   - **Kết hợp với CloudWatch Logs**: Sử dụng CloudWatch để giám sát và debug các Lambda function.
   - **Thiết lập các Biến Môi Trường bảo mật**: Đảm bảo các thông tin nhạy cảm được mã hóa và lưu trong các biến môi trường.
