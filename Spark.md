
### 1. **Kiến trúc của Apache Spark**

   - **Spark Driver**: Điều phối việc thực thi các tác vụ bằng cách phân tích và lên kế hoạch cho các công việc. Đây là nơi chứa **Spark Context** để quản lý các tài nguyên trong quá trình chạy.
   - **Cluster Manager**: Spark có thể làm việc với các hệ thống quản lý cluster như **Standalone** (Spark Cluster riêng), **YARN** (Hadoop), và **Mesos** để quản lý tài nguyên và phân bổ công việc.
   - **Workers/Executors**: Mỗi worker trên Spark cluster là một quá trình thực thi các tác vụ trên dữ liệu. Executor là nơi lưu trữ dữ liệu và thực hiện các phép tính.

### 2. **Rộng về Spark RDD, DataFrame, và Dataset**

   - **RDD (Resilient Distributed Dataset)**: Là cấu trúc dữ liệu cơ bản nhất của Spark, cho phép thao tác trên các tập dữ liệu phân tán. RDD hỗ trợ **immutable** (bất biến) và **lazy evaluation** (tính toán trì hoãn).
     - **Transformations**: Chuyển đổi RDD (như `map`, `filter`, `flatMap`) không thực thi ngay mà tạo ra các RDD mới.
     - **Actions**: Các hành động (như `collect`, `count`, `reduce`) sẽ thực thi các phép tính trên RDD.
     - **Fault Tolerance**: Spark tự động tạo lại RDD từ các phép toán đã áp dụng nếu có lỗi.

   - **DataFrame**: Là một API cấp cao của Spark trên dữ liệu dạng bảng (có cột và hàng), giống như DataFrame trong Pandas hay SQL Table. DataFrame tối ưu hóa hiệu năng hơn RDD nhờ **Catalyst Optimizer**.
   - **Dataset**: Là một API nâng cấp của DataFrame, hỗ trợ các đối tượng kiểu dữ liệu mạnh (strongly-typed). Dataset kết hợp lợi ích của RDD và DataFrame.

### 3. **Spark SQL và Catalyst Optimizer**

   - **Spark SQL**: Cung cấp một giao diện để thực thi các câu lệnh SQL và xử lý dữ liệu có cấu trúc. Bạn có thể tạo các `DataFrame` từ các nguồn dữ liệu khác nhau như JSON, CSV, và cơ sở dữ liệu.
   - **Catalyst Optimizer**: Là bộ tối ưu hóa bên trong của Spark SQL giúp chuyển đổi các truy vấn SQL thành các kế hoạch thực thi tối ưu, giảm thời gian xử lý và tăng hiệu suất.

### 4. **Lập trình Song Song với Spark**

   - **Partitions**: Mỗi RDD hoặc DataFrame được chia thành nhiều phần nhỏ (partition) giúp Spark xử lý song song trên các máy trong cluster.
   - **Transformations và Actions**: Để thực hiện tính toán, các **Transformations** tạo ra một chuỗi các thay đổi cho dữ liệu, trong khi **Actions** kích hoạt Spark thực hiện các tính toán và trả về kết quả.

### 5. **Lazy Evaluation và DAG (Directed Acyclic Graph)**

   - **Lazy Evaluation**: Spark trì hoãn việc tính toán cho đến khi gặp một Action, từ đó giúp tối ưu hóa toàn bộ quá trình xử lý.
   - **DAG Scheduler**: Sau khi có một action, Spark xây dựng DAG từ chuỗi transformations và phân chia thành các giai đoạn (stage). Mỗi stage là một tập hợp các task song song thực thi trên một partition của dữ liệu.

### 6. **Spark Core APIs**

   - **Transformation APIs**: `map`, `filter`, `flatMap`, `groupByKey`, `reduceByKey`, `union`, `join`.
   - **Action APIs**: `collect`, `count`, `take`, `reduce`, `saveAsTextFile`.

### 7. **Spark Streaming**

   - **Spark Streaming**: Cho phép xử lý dữ liệu streaming (dữ liệu cập nhật liên tục) bằng cách chuyển đổi các batch nhỏ (micro-batch) từ nguồn dữ liệu như Kafka hoặc HDFS.
   - **DStreams (Discretized Streams)**: Là tập hợp các RDD, mỗi RDD chứa dữ liệu trong một khoảng thời gian ngắn.

### 8. **Mlib (Machine Learning Library)**

   - **MLlib**: Thư viện machine learning tích hợp cho phép triển khai các mô hình như hồi quy tuyến tính, phân loại, phân cụm, PCA.
   - **Machine Learning Pipelines**: Spark hỗ trợ xây dựng các pipelines từ bước tiền xử lý đến huấn luyện và đánh giá mô hình. Các transformer và estimator giúp chuẩn hóa, chọn đặc trưng, và đánh giá mô hình.

### 9. **GraphX và Xử lý đồ thị**

   - **GraphX**: Là thư viện đồ thị của Spark, cung cấp các thuật toán như PageRank, Connected Components, và Shortest Path trên các đồ thị phân tán.

### 10. **Tối ưu hóa Spark**

   - **BroadCast Variables**: Truyền dữ liệu nhỏ (như biến toàn cục) đến tất cả các executor giúp giảm thời gian tải dữ liệu trong các tác vụ.
   - **Accumulator**: Cho phép chia sẻ biến tích lũy trong các task (như bộ đếm).
   - **Partitioning**: Tối ưu hóa hiệu năng bằng cách điều chỉnh số lượng partition, giúp dữ liệu được phân bố đều.
   - **Caché và Persist**: Lưu trữ RDD hoặc DataFrame trong bộ nhớ hoặc đĩa để tăng tốc độ truy xuất trong các tác vụ kế tiếp.

### 11. **Spark trên các Cluster Managers**

   - **Standalone Cluster**: Spark có sẵn một cluster manager tích hợp, được sử dụng chủ yếu để kiểm thử.
   - **YARN**: Là manager của Hadoop, hỗ trợ việc triển khai Spark trên môi trường Hadoop.
   - **Mesos**: Là hệ thống quản lý tài nguyên được thiết kế để hỗ trợ các ứng dụng lớn trong các datacenter.

### 12. **Triển khai Spark trên Cloud (AWS, Azure, GCP)**

   - **AWS EMR (Elastic MapReduce)**: Dịch vụ triển khai Spark nhanh chóng trên AWS với tính năng autoscaling.
   - **Azure Databricks**: Nền tảng triển khai Spark và DataBricks hợp tác giữa Azure và Databricks.
   - **Google Dataproc**: Dịch vụ triển khai Hadoop/Spark trên Google Cloud.

### 13. **Các mô hình xử lý dữ liệu**

   - **Batch Processing**: Phân tích dữ liệu lớn có cấu trúc bằng Spark SQL, DataFrames.
   - **Real-Time Processing**: Sử dụng Spark Streaming để phân tích dữ liệu liên tục.
   - **Lambda Architecture**: Kết hợp cả xử lý batch và stream trong kiến trúc dữ liệu.
