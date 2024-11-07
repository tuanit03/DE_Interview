
### 1. **Khái niệm Cơ bản về Cơ sở Dữ liệu**
   - **Cơ sở dữ liệu (Database)**: Là tập hợp có cấu trúc của dữ liệu được lưu trữ để sử dụng, quản lý và truy xuất một cách hiệu quả. Được thiết kế để hỗ trợ việc lưu trữ và truy xuất thông tin theo một cách tối ưu, giảm thiểu dư thừa dữ liệu.
   - **Hệ quản trị cơ sở dữ liệu (DBMS)**: Phần mềm cho phép người dùng tương tác với cơ sở dữ liệu. Nó cung cấp các chức năng như lưu trữ, truy xuất, cập nhật và quản lý dữ liệu, đảm bảo tính toàn vẹn và bảo mật của dữ liệu.

### 2. **Các Loại Mô Hình Dữ Liệu**
   - **Mô hình phân cấp (Hierarchical Model)**: Sắp xếp dữ liệu theo cấu trúc cây với một gốc và các nhánh. Mỗi bản ghi có một bản ghi cha duy nhất, và một bản ghi cha có thể có nhiều bản ghi con.
   - **Mô hình mạng (Network Model)**: Cho phép các mối quan hệ nhiều-nhiều. Các bản ghi được kết nối theo một đồ thị, mỗi bản ghi có thể có nhiều bản ghi cha và nhiều bản ghi con.
   - **Mô hình quan hệ (Relational Model)**: Tổ chức dữ liệu dưới dạng các bảng (quan hệ) với các hàng (bản ghi) và cột (thuộc tính). Được hỗ trợ bởi SQL và phổ biến nhất hiện nay.
   - **Mô hình hướng đối tượng (Object-Oriented Model)**: Kết hợp các khái niệm của lập trình hướng đối tượng vào cơ sở dữ liệu, cho phép lưu trữ và quản lý các đối tượng phức tạp.
   - **Mô hình tài liệu (Document Model)**: Lưu trữ dữ liệu dưới dạng các tài liệu (document) có cấu trúc như JSON hoặc XML. Được dùng phổ biến trong các hệ cơ sở dữ liệu NoSQL.

### 3. **Các Khái niệm trong Cơ sở Dữ liệu Quan hệ**
   - **Quan hệ (Relation)**: Một bảng trong cơ sở dữ liệu, biểu diễn một tập hợp các thực thể có cùng kiểu.
   - **Khóa (Key)**:
      - **Khóa chính (Primary Key)**: Một thuộc tính hoặc tập hợp thuộc tính xác định duy nhất mỗi bản ghi trong bảng.
      - **Khóa ngoại (Foreign Key)**: Một thuộc tính hoặc tập hợp thuộc tính liên kết một bảng với bảng khác, thường là khóa chính của bảng được liên kết.
      - **Khóa duy nhất (Unique Key)**: Giống như khóa chính, nhưng cho phép một giá trị null.
   - **Phụ thuộc hàm (Functional Dependency)**: Biểu thị một thuộc tính phụ thuộc vào một hoặc nhiều thuộc tính khác. Ví dụ: nếu biết giá trị của `A`, có thể xác định duy nhất giá trị của `B`, ta nói `A -> B`.

### 4. **Ràng buộc Toàn vẹn (Integrity Constraints)**
   - **Ràng buộc toàn vẹn thực thể (Entity Integrity)**: Khóa chính không được chứa giá trị null và phải duy nhất.
   - **Ràng buộc toàn vẹn tham chiếu (Referential Integrity)**: Khóa ngoại trong một bảng phải trỏ đến một khóa chính hợp lệ trong bảng khác.
   - **Ràng buộc toàn vẹn miền giá trị (Domain Integrity)**: Các giá trị của một thuộc tính phải thuộc một miền giá trị xác định.

### 5. **Chuẩn Hóa (Normalization)**
   - **Mục đích**: Giảm thiểu dư thừa dữ liệu và ngăn chặn sự bất nhất (inconsistency) trong dữ liệu.
   - **Các dạng chuẩn (Normal Forms)**:
      - **1NF (First Normal Form)**: Các thuộc tính phải là các giá trị nguyên tử (không chia nhỏ được).
      - **2NF (Second Normal Form)**: Đáp ứng 1NF và không có phụ thuộc hàm từng phần (phụ thuộc một phần của khóa chính).
      - **3NF (Third Normal Form)**: Đáp ứng 2NF và không có phụ thuộc bắc cầu (các thuộc tính không khóa không phụ thuộc vào các thuộc tính không khóa khác).
      - **BCNF (Boyce-Codd Normal Form)**: Mạnh hơn 3NF, mọi phụ thuộc hàm không tầm thường đều có vế trái là siêu khóa.

### 6. **Nguyên Lý Giao Dịch (Transaction) và ACID**
   - **Giao dịch (Transaction)**: Một đơn vị công việc bao gồm một hoặc nhiều thao tác trên cơ sở dữ liệu. Giao dịch có thể thành công hoặc thất bại hoàn toàn.
   - **ACID Properties**:
      - **Atomicity**: Giao dịch phải được thực hiện toàn bộ hoặc không thực hiện gì cả.
      - **Consistency**: Giao dịch đưa cơ sở dữ liệu từ trạng thái nhất quán này sang trạng thái nhất quán khác.
      - **Isolation**: Giao dịch phải được thực hiện độc lập, không ảnh hưởng lẫn nhau.
      - **Durability**: Khi giao dịch hoàn tất, thay đổi phải được lưu trữ vĩnh viễn.

### 7. **Chỉ Mục (Indexing)**
   - **Khái niệm**: Cấu trúc dữ liệu hỗ trợ tăng tốc truy vấn trên các thuộc tính nhất định của bảng.
   - **Các loại chỉ mục**:
      - **Chỉ mục chính (Primary Index)**: Được tạo trên khóa chính, sắp xếp dữ liệu theo khóa.
      - **Chỉ mục phụ (Secondary Index)**: Được tạo trên các thuộc tính không phải là khóa.
   - **Cây B+ và Hashing**: Các kỹ thuật phổ biến trong cấu trúc chỉ mục để tối ưu truy xuất dữ liệu.

### 8. **Giao dịch Đồng thời và Điều khiển Truy cập Cạnh Tranh**
   - **Vấn đề đồng thời (Concurrency)**: Khi nhiều giao dịch diễn ra cùng lúc, dẫn đến các vấn đề như mất cập nhật, đọc dữ liệu không nhất quán.
   - **Điều khiển truy cập cạnh tranh (Concurrency Control)**: Các kỹ thuật như khóa (locking) và kiểm soát phiên bản để đảm bảo tính toàn vẹn dữ liệu khi có nhiều giao dịch.
   - **Cấp độ cô lập (Isolation Levels)**:
      - **Read Uncommitted**: Cho phép đọc dữ liệu chưa hoàn tất.
      - **Read Committed**: Chỉ đọc dữ liệu đã hoàn tất.
      - **Repeatable Read**: Đảm bảo đọc dữ liệu cố định trong giao dịch.
      - **Serializable**: Cô lập hoàn toàn, tránh hoàn toàn các xung đột.

### 9. **Phục hồi Dữ liệu (Data Recovery)**
   - **Checkpoint**: Điểm phục hồi giúp giảm thiểu thời gian khôi phục sau sự cố.
   - **Redo/Undo Logging**: Lưu trữ các bản ghi giao dịch để có thể hoàn tác hoặc làm lại các giao dịch khi cần thiết.

### 10. **Các Kỹ thuật Lưu trữ và Tối ưu hóa**
   - **Partitioning**: Phân chia bảng lớn thành các phần nhỏ hơn để tối ưu hóa truy vấn.
   - **Sharding**: Chia nhỏ dữ liệu thành các tập dữ liệu con (shard) lưu trên các máy khác nhau, thường dùng cho hệ thống phân tán lớn.
   - **Caching**: Lưu trữ các kết quả truy vấn thường xuyên sử dụng trong bộ nhớ đệm để tăng tốc độ truy xuất.
