

### 1. **Giới thiệu Scala**
   - **Scala là gì?**  
     Scala (Scalable Language) là một ngôn ngữ lập trình mạnh mẽ kết hợp tính năng của lập trình hướng đối tượng (OOP) và lập trình hàm (functional programming). Scala chạy trên JVM, có thể tương tác với Java, và thường được sử dụng trong các hệ thống Big Data với Apache Spark.

   - **Ưu điểm**  
     Scala có cú pháp ngắn gọn, hỗ trợ lập trình hàm, và khả năng mở rộng mạnh mẽ, thích hợp cho cả phát triển phần mềm và xử lý dữ liệu lớn. Cấu trúc cú pháp rõ ràng, dễ hiểu hơn so với Java trong các ứng dụng phức tạp.

### 2. **Cấu trúc cơ bản và cú pháp**
   - **Biến và hằng**  
     - `val` (immutable): dùng để khai báo hằng số.
     - `var` (mutable): dùng để khai báo biến có thể thay đổi.

     ```scala
     val x: Int = 5
     var y: String = "Hello"
     ```

   - **Kiểu dữ liệu**  
     Scala có các kiểu dữ liệu cơ bản như: `Int`, `Double`, `String`, `Boolean`, và `Char`, cũng như các kiểu dữ liệu nâng cao như `List`, `Map`, `Set`, `Tuple`, và `Option`.

   - **Điều kiện và vòng lặp**  
     Các câu lệnh điều kiện (`if`, `else if`, `else`) và các vòng lặp (`for`, `while`, `do-while`) có cú pháp tương tự các ngôn ngữ khác nhưng tích hợp với cú pháp hàm như `foreach`, `map`, `filter` để dễ xử lý các tập dữ liệu lớn.

     ```scala
     if (x > 0) println("Positive") else println("Negative")
     
     for (i <- 1 to 5) println(i)
     ```

### 3. **Lập trình hướng đối tượng trong Scala**
   - **Class và Object**  
     Trong Scala, mọi thứ đều là đối tượng. `class` được sử dụng để định nghĩa các lớp trong Scala, còn `object` là đơn thể của một lớp (singleton object).

     ```scala
     class Person(val name: String, val age: Int)

     object Test {
       def main(args: Array[String]): Unit = {
         val person = new Person("Alice", 25)
         println(person.name)
       }
     }
     ```

   - **Trait**  
     Trait giống như `interface` trong Java nhưng có thể chứa các phương thức có sẵn. Một lớp có thể mở rộng nhiều trait.

     ```scala
     trait Greet {
       def greet(name: String): Unit = println(s"Hello, $name!")
     }

     class Person(name: String) extends Greet {
       def showGreet(): Unit = greet(name)
     }
     ```

   - **Inheritance**  
     Scala hỗ trợ kế thừa đơn (single inheritance) nhưng có thể kết hợp nhiều `trait` để tạo đa kế thừa.

     ```scala
     class Animal {
       def eat(): Unit = println("Eating")
     }

     class Dog extends Animal {
       override def eat(): Unit = println("Dog eating")
     }
     ```

### 4. **Lập trình hàm trong Scala**
   - **Hàm và lambda**  
     Hàm có thể được định nghĩa độc lập hoặc dưới dạng biểu thức lambda (anonymous function).

     ```scala
     def add(x: Int, y: Int): Int = x + y

     val multiply = (x: Int, y: Int) => x * y
     ```

   - **Higher-order functions**  
     Hàm bậc cao là hàm nhận một hoặc nhiều hàm khác làm tham số hoặc trả về một hàm. Ví dụ `map`, `filter`, và `reduce` trong Scala.

     ```scala
     val numbers = List(1, 2, 3, 4, 5)
     val squaredNumbers = numbers.map(x => x * x)  // Kết quả: List(1, 4, 9, 16, 25)
     ```

   - **Closures**  
     Closure là một hàm mà có thể "nhớ" được các biến bên ngoài phạm vi của nó.

     ```scala
     var factor = 3
     val multiplier = (x: Int) => x * factor
     ```

   - **Currying**  
     Kỹ thuật chia một hàm có nhiều tham số thành các hàm đơn tham số.

     ```scala
     def add(x: Int)(y: Int): Int = x + y
     ```

### 5. **Collection trong Scala**
   - **Immutable Collection**  
     Các kiểu dữ liệu bất biến như `List`, `Set`, `Map`, `Tuple` là mặc định trong Scala để đảm bảo tính bất biến và an toàn.

     ```scala
     val list = List(1, 2, 3)
     val set = Set("a", "b", "c")
     ```

   - **Mutable Collection**  
     Được khai báo bằng cách sử dụng `scala.collection.mutable`. Ví dụ: `ArrayBuffer`, `ListBuffer`.

     ```scala
     import scala.collection.mutable.ArrayBuffer
     val arrBuffer = ArrayBuffer(1, 2, 3)
     arrBuffer += 4
     ```

   - **Option, Some, None**  
     Cung cấp một cách an toàn để xử lý các giá trị `null`.

     ```scala
     def findName(id: Int): Option[String] = {
       if (id == 1) Some("Alice") else None
     }
     ```

### 6. **Concurrency (Xử lý song song)**
   - **Futures và Promises**  
     Trong Scala, `Future` và `Promise` giúp xử lý các tác vụ không đồng bộ. `Future` sẽ xử lý tác vụ trong background và trả về kết quả sau khi hoàn thành.

     ```scala
     import scala.concurrent.Future
     import scala.concurrent.ExecutionContext.Implicits.global

     val future = Future {
       // Thực hiện tác vụ không đồng bộ
     }
     ```

   - **Akka**  
     Thư viện mạnh mẽ để xử lý concurrency theo mô hình Actor, phổ biến trong các hệ thống phân tán và xử lý song song.

### 7. **Scala và Big Data (Apache Spark)**
   - **Spark RDD (Resilient Distributed Dataset)**  
     RDD là cấu trúc dữ liệu phân tán của Spark, cho phép thực hiện các thao tác tính toán song song.

     ```scala
     val rdd = sc.parallelize(List(1, 2, 3, 4))
     ```

   - **DataFrame và Dataset**  
     Cấu trúc dữ liệu mạnh mẽ hơn RDD, giúp thao tác với dữ liệu có cấu trúc và không có cấu trúc hiệu quả.

     ```scala
     val df = spark.read.option("header", "true").csv("file.csv")
     df.show()
     ```

   - **SparkSQL**  
     Sử dụng SQL để thao tác và xử lý dữ liệu trong DataFrame.

     ```scala
     df.createOrReplaceTempView("table")
     spark.sql("SELECT * FROM table WHERE column = value")
     ```

### 8. **Công cụ và Framework bổ trợ**
   - **SBT (Scala Build Tool)**: Công cụ build chính của Scala, giúp quản lý phụ thuộc và build dự án Scala.
   - **REPL (Read-Eval-Print Loop)**: Scala REPL giúp thử nghiệm code nhanh chóng và hiệu quả.
   - **IntelliJ IDEA và VS Code**: Các IDE và trình biên tập hỗ trợ Scala.

### 9. **Best Practices (Thực hành tốt)**
   - **Immutability (Tính bất biến)**: Sử dụng `val` thay cho `var` bất cứ khi nào có thể để đảm bảo tính bất biến.
   - **Functional Programming Principles**: Viết code ngắn gọn, dễ đọc bằng cách sử dụng các hàm như `map`, `filter`, `reduce`.
   - **Error Handling**: Sử dụng `Option`, `Either`, và `Try` để xử lý lỗi một cách an toàn.

---
