

### 1. **MongoDB là gì?**
   - MongoDB là một hệ quản trị cơ sở dữ liệu NoSQL mã nguồn mở, hướng tài liệu (document-oriented database), lưu trữ dữ liệu dưới dạng BSON (Binary JSON).
   - MongoDB thường được sử dụng trong các hệ thống có yêu cầu về hiệu suất, linh hoạt về schema và khả năng mở rộng (scalability).

### 2. **Kiến trúc của MongoDB**
   - **Database**: Là nơi chứa các collections (tương tự như một schema trong SQL).
   - **Collection**: Tập hợp các tài liệu, tương tự như bảng trong SQL nhưng không bắt buộc phải có cấu trúc cố định.
   - **Document**: Là đơn vị cơ bản của MongoDB, lưu trữ dữ liệu dưới dạng BSON và tương đương với một hàng (row) trong SQL.
   - **Fields**: Là các thuộc tính trong một document, tương tự như cột trong SQL.

### 3. **Các thao tác CRUD (Create, Read, Update, Delete) trong MongoDB**
   - **Create**: Sử dụng lệnh `insertOne()` hoặc `insertMany()` để thêm một hoặc nhiều documents vào collection.
   - **Read**: Sử dụng lệnh `find()`, `findOne()` để truy vấn dữ liệu, có thể kết hợp với các điều kiện lọc.
   - **Update**: Sử dụng lệnh `updateOne()`, `updateMany()`, hoặc `replaceOne()` để cập nhật documents.
   - **Delete**: Sử dụng `deleteOne()` và `deleteMany()` để xóa documents.

### 4. **Query trong MongoDB**
   - **Basic Query**: Truy vấn đơn giản bằng `find()`, có thể lọc với các toán tử như `$gt`, `$lt`, `$in`, `$and`, `$or`.
   - **Aggregation**: Sử dụng Aggregation Pipeline để thực hiện các thao tác phức tạp như `match`, `group`, `project`, `sort`, `limit`.
   - **Indexing**: Tạo các chỉ mục để tăng tốc truy vấn với các lệnh như `createIndex()` và các loại chỉ mục như Single Field Index, Compound Index, Multikey Index.

### 5. **Replication (Nhân bản dữ liệu)**
   - **Replica Set**: Là một nhóm các mongod instances chứa cùng một dataset. Các thành viên của replica set bao gồm một **Primary** (đảm nhận ghi) và nhiều **Secondaries** (chỉ đọc).
   - **Primary và Secondary**: Primary node ghi dữ liệu, sau đó các Secondary nodes sẽ sao chép (replicate) dữ liệu này để có bản sao dự phòng.
   - **Failover**: Trong trường hợp Primary node gặp sự cố, một Secondary node sẽ được bầu lên làm Primary mới để đảm bảo tính sẵn sàng của dữ liệu.

### 6. **Sharding (Phân mảnh dữ liệu)**
   - **Shard**: Là một instance mongod lưu trữ một phần dữ liệu trong MongoDB sharded cluster.
   - **Config Server**: Lưu metadata của cluster, bao gồm thông tin về cách dữ liệu được phân phối.
   - **Mongos**: Là router điều phối các yêu cầu từ client đến các shard đúng.
   - **Range-based và Hash-based Sharding**: MongoDB hỗ trợ phân mảnh dữ liệu dựa trên giá trị (range-based) hoặc băm (hash-based) của khóa phân mảnh.

### 7. **Transactions (Giao dịch)**
   - MongoDB hỗ trợ **ACID transactions** để đảm bảo tính toàn vẹn của dữ liệu khi thực hiện nhiều thao tác ghi phức tạp.
   - Transactions trong MongoDB có thể thực hiện trên một hoặc nhiều tài liệu trong một collection hoặc nhiều collections (bắt đầu từ phiên bản 4.0).

### 8. **Data Model Design (Thiết kế mô hình dữ liệu)**
   - **Embedding**: Lưu trữ dữ liệu có liên quan trong cùng một document để giảm số lần truy vấn.
   - **Referencing**: Sử dụng tham chiếu giữa các documents khi dữ liệu lớn và cần tối ưu dung lượng lưu trữ.
   - **Normalization vs. Denormalization**: MongoDB khuyến khích denormalization (nhúng dữ liệu vào trong tài liệu) cho tốc độ truy vấn nhanh hơn, nhưng có thể cân nhắc normalization trong một số trường hợp.

### 9. **Các phương thức tối ưu hóa trong MongoDB**
   - **Indexes**: Sử dụng các loại indexes phù hợp để cải thiện hiệu năng truy vấn.
   - **Schema Design**: Thiết kế schema hợp lý dựa trên yêu cầu về truy vấn và khối lượng dữ liệu.
   - **Aggregation Pipelines**: Sử dụng các giai đoạn (stages) trong aggregation để xử lý dữ liệu tại database thay vì ở ứng dụng.
   - **Data Partitioning**: Sử dụng sharding để phân tán dữ liệu khi khối lượng dữ liệu lớn, giảm tải cho một node duy nhất.

### 10. **Backup và Restore**
   - **Mongodump và Mongorestore**: Sử dụng `mongodump` để backup dữ liệu và `mongorestore` để phục hồi.
   - **Automated Backup**: Cấu hình các backup tự động cho replica set và sharded cluster để đảm bảo tính toàn vẹn và phục hồi dữ liệu nhanh chóng.

### 11. **Các công cụ giám sát và quản lý MongoDB**
   - **MongoDB Atlas**: Dịch vụ MongoDB trên nền tảng đám mây, cung cấp các tính năng quản lý và giám sát nâng cao.
   - **MongoDB Compass**: Công cụ GUI chính thức của MongoDB để truy vấn, quản lý dữ liệu, và tối ưu hóa hiệu năng.
   - **MMS (MongoDB Management Service)**: Dịch vụ giám sát và sao lưu trực tuyến.

