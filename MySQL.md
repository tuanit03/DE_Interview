
### 1. **Tổng quan về MySQL**
   - **MySQL là gì?**: MySQL là hệ quản trị cơ sở dữ liệu quan hệ mã nguồn mở, thường được sử dụng để lưu trữ và quản lý dữ liệu. Nó hỗ trợ các câu truy vấn SQL để thao tác với dữ liệu và phù hợp với các ứng dụng web và phân tích dữ liệu.
   - **Kiến trúc MySQL**: Bao gồm các thành phần như Server, Storage Engine (InnoDB, MyISAM, v.v.), Query Cache, và Query Optimizer.

### 2. **Các Kiểu Dữ Liệu Trong MySQL**
   - **Numeric Types**: INT, TINYINT, SMALLINT, MEDIUMINT, BIGINT, FLOAT, DOUBLE, DECIMAL.
   - **String Types**: CHAR, VARCHAR, TEXT, BLOB, ENUM, SET.
   - **Date and Time Types**: DATE, TIME, DATETIME, TIMESTAMP, YEAR.
   - **Other Types**: JSON, ENUM, SET. JSON đặc biệt hữu ích cho việc lưu trữ dữ liệu không theo cấu trúc.

### 3. **Cấu Trúc và Quản Lý Cơ Sở Dữ Liệu**
   - **Database và Schema**: Cách tạo, xóa, và quản lý database.
   - **Table Structure**: Cách tạo bảng, chọn kiểu dữ liệu, sử dụng các constraints như PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, và DEFAULT.
   - **Normalization**: Các cấp độ chuẩn hóa (1NF, 2NF, 3NF, BCNF), giúp loại bỏ các bất cập trong dữ liệu và cải thiện tính nhất quán.
   - **Indexes**: Indexing là cách tối ưu hóa truy vấn, giúp tăng tốc truy vấn dữ liệu. Các loại index bao gồm B-Tree và Hash Index.
   - **Views**: Views là các bảng ảo, giúp đơn giản hóa truy vấn và tăng tính bảo mật.

### 4. **Các Câu Lệnh SQL Quan Trọng**
   - **Data Definition Language (DDL)**: 
     - `CREATE`, `ALTER`, `DROP` để tạo, sửa đổi, và xóa các thành phần như database, tables, indexes.
   - **Data Manipulation Language (DML)**:
     - `SELECT`, `INSERT`, `UPDATE`, `DELETE` để truy xuất và thay đổi dữ liệu.
     - `WHERE`, `JOIN`, `GROUP BY`, `ORDER BY`, `HAVING` để lọc, nhóm và sắp xếp dữ liệu.
   - **Data Control Language (DCL)**:
     - `GRANT`, `REVOKE` để cấp và thu hồi quyền truy cập.
   - **Transaction Control Language (TCL)**:
     - `COMMIT`, `ROLLBACK`, `SAVEPOINT` để quản lý giao dịch, giúp duy trì tính toàn vẹn dữ liệu.

### 5. **Các Kỹ Thuật Tối Ưu Hóa Truy Vấn**
   - **Indexes**: Sử dụng index phù hợp để tối ưu tốc độ truy vấn.
   - **Query Optimization**:
     - **Explain Plan** (`EXPLAIN`): Phân tích câu truy vấn để hiểu cách MySQL thực hiện.
     - **JOIN Optimization**: Tối ưu hóa việc sử dụng các loại JOIN (INNER, LEFT, RIGHT).
     - **Subqueries và Joins**: Khi nào nên dùng subqueries và khi nào nên sử dụng JOIN.
   - **Caching**: Sử dụng query cache để tăng hiệu suất khi truy vấn dữ liệu lặp lại.
   - **Batch Processing**: Chạy truy vấn theo lô để giảm thời gian chờ và tối ưu hiệu suất.

### 6. **MySQL Transactions và ACID**
   - **Transactions**: Tạo transaction với các câu lệnh như `START TRANSACTION`, `COMMIT`, `ROLLBACK`.
   - **ACID Properties**: 
     - **Atomicity**: Đảm bảo rằng tất cả các thao tác trong một transaction phải hoàn tất hoặc không thao tác nào được thực hiện.
     - **Consistency**: Đảm bảo tính toàn vẹn dữ liệu sau mỗi transaction.
     - **Isolation**: Tránh xung đột giữa các transaction.
     - **Durability**: Đảm bảo dữ liệu được lưu trữ bền vững ngay cả khi hệ thống gặp sự cố.

### 7. **Storage Engines Trong MySQL**
   - **InnoDB**: Hỗ trợ ACID, dùng cho transaction và hỗ trợ FOREIGN KEY. Thích hợp với hầu hết các ứng dụng.
   - **MyISAM**: Tốc độ cao hơn trong các tác vụ đọc, nhưng không hỗ trợ transaction và FOREIGN KEY.
   - **Memory**: Lưu trữ dữ liệu trong bộ nhớ RAM, tốc độ nhanh nhưng không bền vững.
   - **CSV, Archive, Blackhole, v.v.**: Các storage engines khác nhau phục vụ các trường hợp sử dụng đặc biệt.

### 8. **Stored Procedures, Functions, và Triggers**
   - **Stored Procedures**: Đoạn mã SQL lưu trữ trong database và có thể được gọi để thực hiện các tác vụ lặp lại.
   - **Functions**: Giống như stored procedures nhưng trả về một giá trị duy nhất.
   - **Triggers**: Đoạn mã tự động chạy khi có sự kiện (INSERT, UPDATE, DELETE) xảy ra trên bảng, giúp duy trì tính nhất quán dữ liệu.

### 9. **Replication và High Availability**
   - **Replication**: Nhân bản dữ liệu từ một server chính (master) sang một hoặc nhiều server phụ (slave) để đảm bảo tính sẵn sàng của dữ liệu.
   - **Master-Slave và Master-Master Replication**: Các cấu hình replication khác nhau.
   - **Failover và Backup**: Thiết lập hệ thống chịu lỗi và các kỹ thuật sao lưu để bảo vệ dữ liệu.

### 10. **Bảo Mật MySQL**
   - **Authentication và Authorization**: Quản lý người dùng và quyền truy cập với `GRANT` và `REVOKE`.
   - **Data Encryption**: Sử dụng SSL/TLS và mã hóa dữ liệu tại các mức độ khác nhau.
   - **Data Masking**: Che giấu thông tin nhạy cảm bằng cách mã hóa hoặc sử dụng hash.

### 11. **Quản Lý và Bảo Trì MySQL**
   - **Backup và Restore**: Sử dụng các công cụ như `mysqldump`, `mysqlpump`, và các bản sao lưu binary để sao lưu và khôi phục dữ liệu.
   - **Monitoring**: Theo dõi hiệu suất MySQL với các công cụ như MySQL Workbench, Percona Monitoring, hoặc các công cụ bên ngoài như Prometheus và Grafana.
   - **Logs**: Sử dụng các loại log như error log, general query log, và slow query log để theo dõi và khắc phục lỗi.

### 12. **Các Công Cụ Hỗ Trợ MySQL**
   - **MySQL Workbench**: Công cụ đồ họa để thiết kế, quản lý và tối ưu hóa database.
   - **phpMyAdmin**: Giao diện web để quản lý MySQL.
   - **Percona Tools**: Công cụ tối ưu hóa và giám sát hiệu suất MySQL.
