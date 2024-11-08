

### 1. **Khái niệm cơ bản về AWS EC2**
   - **Instance**: Máy ảo chạy trên nền tảng EC2. Người dùng có thể chọn cấu hình phần cứng và phần mềm, từ CPU, RAM, ổ đĩa, đến hệ điều hành (OS).
   - **AMI (Amazon Machine Image)**: AMI là bản sao mẫu của một hệ điều hành cùng với các ứng dụng và cấu hình đã cài đặt sẵn. AMI giúp khởi tạo nhanh các instances với cấu hình sẵn.
   - **Regions và Availability Zones**: AWS EC2 có nhiều khu vực địa lý (Regions) và các khu vực sẵn sàng (Availability Zones - AZs). AZs là các trung tâm dữ liệu độc lập trong một region, giúp đảm bảo tính sẵn sàng cao của hệ thống.

### 2. **Loại Instance và Tối ưu hóa Hiệu năng**
   - **Loại Instance**: AWS cung cấp các loại instance với mục đích tối ưu hóa cho các nhu cầu khác nhau, bao gồm:
      - **General Purpose** (T3, T4g, M5, M6i): Phù hợp cho các ứng dụng với khối lượng công việc đa dạng như máy chủ web, môi trường phát triển.
      - **Compute Optimized** (C5, C6g): Tối ưu cho các ứng dụng yêu cầu CPU cao như xử lý hình ảnh, chơi game, và xử lý tính toán song song.
      - **Memory Optimized** (R5, X1e, z1d): Phù hợp cho các ứng dụng sử dụng nhiều bộ nhớ như cơ sở dữ liệu lớn, caching.
      - **Storage Optimized** (I3, D2): Tối ưu cho các ứng dụng yêu cầu truy cập và xử lý dữ liệu nhanh như phân tích dữ liệu lớn.
      - **Accelerated Computing** (P3, F1): Dành cho các ứng dụng yêu cầu tăng tốc phần cứng, như GPU cho machine learning hoặc FPGA cho tính toán đặc biệt.
   - **Tối ưu hóa Chi phí**: AWS cung cấp các lựa chọn để giảm chi phí, như Reserved Instances (RI) cho thuê dài hạn, Spot Instances để tận dụng phần cứng thừa với chi phí thấp, và Savings Plans.

### 3. **Quản lý Instances**
   - **Lifecycle của Instance**: Một instance trong AWS EC2 có thể ở các trạng thái như `pending`, `running`, `stopped`, và `terminated`. Người dùng có thể khởi tạo, khởi động lại, dừng, và xóa các instance.
   - **Elastic IP Address**: Là địa chỉ IP tĩnh có thể gán cho instance để có thể truy cập ổn định từ internet ngay cả khi instance được khởi động lại hoặc thay thế.
   - **Auto Scaling**: Dịch vụ tự động thêm hoặc giảm số lượng instances dựa trên nhu cầu sử dụng. Auto Scaling giúp tối ưu chi phí và tăng tính sẵn sàng của hệ thống.

### 4. **Bảo mật trong EC2**
   - **Security Groups**: Là lớp bảo mật mạng cho phép kiểm soát luồng truy cập vào và ra cho các instances. Security Groups đóng vai trò như một tường lửa ảo, kiểm soát các cổng và IP được phép truy cập.
   - **IAM Roles**: Phân quyền cho các instance để có thể truy cập các dịch vụ AWS khác mà không cần lưu trữ thông tin bảo mật trong mã nguồn. 
   - **Key Pairs**: AWS EC2 sử dụng key pairs (cặp khóa công khai và bí mật) để bảo mật truy cập vào instance thông qua SSH. Khóa bí mật sẽ được lưu trên máy người dùng, và khóa công khai sẽ được lưu trên instance.
   - **Network ACLs (Access Control Lists)**: Kiểm soát truy cập ở cấp độ subnet, thường được sử dụng để bảo mật các subnet trong Virtual Private Cloud (VPC).

### 5. **Amazon EC2 Storage Options**
   - **EBS (Elastic Block Store)**: EBS là dịch vụ lưu trữ dạng block storage được gắn vào instance. Mỗi volume có thể được thiết kế với các tùy chọn như General Purpose (gp3), Provisioned IOPS (io2) cho ứng dụng yêu cầu tốc độ truy cập nhanh.
   - **Instance Store**: Dạng lưu trữ tạm thời trên chính ổ đĩa vật lý của instance. Dữ liệu sẽ bị mất khi instance bị dừng hoặc khởi động lại.
   - **EFS (Elastic File System)**: Hệ thống file lưu trữ hỗ trợ lưu trữ chia sẻ trên nhiều instance, thường được dùng cho các ứng dụng yêu cầu lưu trữ phân tán và ổn định.
   - **S3 (Simple Storage Service)**: Không phải là một dịch vụ lưu trữ trực tiếp gắn với EC2, nhưng S3 thường được sử dụng để lưu trữ dữ liệu lớn như bản sao lưu, log files, và tài liệu, với khả năng mở rộng và chi phí thấp.

### 6. **Networking trên EC2**
   - **Virtual Private Cloud (VPC)**: Tạo mạng riêng ảo cho các instances. VPC giúp cấu hình các subnet, bảng định tuyến và tường lửa cho hệ thống.
   - **Subnet**: Phân chia mạng trong VPC, có thể là public subnet (cho các instance cần truy cập từ internet) hoặc private subnet (cho các instance nội bộ).
   - **Load Balancing**: AWS cung cấp dịch vụ Elastic Load Balancing (ELB) để phân phối lưu lượng mạng đến các instances, hỗ trợ cân bằng tải và tăng cường tính sẵn sàng.
   - **NAT Gateway**: Cho phép các instance trong private subnet truy cập internet để cập nhật phần mềm hoặc tải dữ liệu, mà không cần gán IP công khai.

### 7. **Monitoring và Logging**
   - **Amazon CloudWatch**: Dịch vụ giám sát hệ thống, cho phép theo dõi các thông số như CPU, bộ nhớ, lưu lượng mạng của instances. CloudWatch cũng hỗ trợ thiết lập cảnh báo và phản ứng tự động.
   - **AWS CloudTrail**: Ghi lại các hoạt động và thay đổi cấu hình của người dùng với các dịch vụ AWS, giúp kiểm tra và audit các thay đổi, đảm bảo tính bảo mật.

### 8. **Các tính năng Khả dụng Cao và Khôi phục**
   - **Multi-AZ Deployment**: AWS cung cấp khả năng triển khai các instance qua nhiều Availability Zones để đảm bảo tính sẵn sàng cao trong trường hợp một AZ bị gián đoạn.
   - **Snapshots**: AWS EBS cho phép người dùng tạo snapshots (bản sao lưu) của volumes để khôi phục lại trạng thái dữ liệu khi cần.
   - **Elastic Load Balancing và Auto Scaling**: Kết hợp để tăng cường khả năng mở rộng và đảm bảo hệ thống luôn hoạt động ổn định.

### 9. **Sử dụng EC2 trong Thực tiễn**
   - **Triển khai ứng dụng Web**: EC2 thường được sử dụng để triển khai các máy chủ web, ứng dụng web, hoặc backend cho ứng dụng di động.
   - **Machine Learning và Big Data**: Các instances tối ưu cho tính toán như P3, G4, hoặc F1 có thể hỗ trợ chạy các mô hình machine learning, xử lý big data với Apache Spark hoặc Hadoop.
   - **Containers và Kubernetes**: AWS EC2 cung cấp môi trường để triển khai container với Docker hoặc Kubernetes. Người dùng cũng có thể dùng EKS (Elastic Kubernetes Service) để quản lý Kubernetes dễ dàng hơn.
