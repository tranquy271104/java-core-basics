Để biến file Markdown này thành một tài liệu chuyên nghiệp, chuẩn cấu trúc của các kỹ sư phần mềm trên GitHub, chúng ta cần loại bỏ toàn bộ các câu từ mang tính chất "văn nói", xóa sạch các ký tự trích dẫn thừa, đồng thời tổ chức lại mã nguồn theo chuẩn phân cấp thư mục.

Dưới đây là toàn bộ nội dung file ghi chú đã được chuẩn hóa ở mức độ cao nhất (Enterprise-ready), chia bố cục rõ ràng để bạn lưu trữ lâu dài.

---

# ☕ Java Development Foundations: Architecture, Data Types & Operators

## 1. Environment Setup & Project Architecture

### IDE Selection

* 
**Production Environment:** IntelliJ IDEA, Eclipse, NetBeans, VS Code.


* 
**Cloud Sandboxes:** OnlineGDB (Chỉ sử dụng để kiểm thử nhanh hoặc khi môi trường local gặp lỗi phần cứng ; không áp dụng cho các dự án lớn do giới hạn về mặt quản lý tệp cấu trúc ).



### Project & Code Structure

* 
**Encapsulation Requirement:** Mọi logic xử lý trong Java bắt buộc phải nằm bên trong phạm vi một Lớp (`class`).


* 
**Naming Consistency:** Tên của `public class` phải trùng khớp tuyệt đối với tên tệp vật lý `.java` (Phân biệt chữ hoa/thường).


* 
**Package Management:** Sử dụng từ khóa `package` ở đầu tệp nhằm phân nhóm logic và cấu trúc thư mục logic.


* ⚠️ **Production Note (OJ Platforms):** Khi triển khai mã nguồn lên các hệ thống chấm bài tự động (Online Judge - OJ), bắt buộc phải **loại bỏ** dòng khai báo `package` để tránh lỗi biên dịch hệ thống (`Compilation Error - CE`).





### Application Entry Point (The `main` Method)

```java
public class Main {
    public static void main(String[] args) {
        // Điểm khởi đầu thực thi của luồng ứng dụng
    }
}

```

---

## 2. Primitive Data Types Matrix

Java tích hợp 8 kiểu dữ liệu nguyên thủy, dưới đây là ma trận cấu trúc của 6 kiểu dữ liệu cốt lõi:

| Category | Data Type | Memory Size | Value Range (Approx.) | Use Case & Optimization |
| --- | --- | --- | --- | --- |
| **Integer** | <br>`int` 

 | 4 Bytes (32-bit) 

 | <br>$-2 \times 10^9$ to $2 \times 10^9$ 

 | Kiểu dữ liệu mặc định cho các phép toán số nguyên thông thường.

 |
|  | <br>`long` 

 | 8 Bytes (64-bit) 

 | <br>$-9 \times 10^{18}$ to $9 \times 10^{18}$ 

 | Áp dụng khi tập dữ liệu hoặc kết quả tính toán có rủi ro vượt ngưỡng `int`.

 |
| **Floating-Point** | <br>`float` 

 | 4 Bytes (32-bit) 

 | 6 - 7 chữ số phần thập phân 

 | Độ chính xác đơn. Yêu cầu hậu tố `F` hoặc `f` khi khởi tạo hằng số.

 |
|  | <br>`double` 

 | 8 Bytes (64-bit) 

 | 15 - 16 chữ số phần thập phân 

 | <br>**Độ chính xác kép.** Khuyến nghị dùng cho tất cả tính toán số thực nhằm giảm thiểu sai số.

 |
| **Character** | <br>`char` 

 | 2 Bytes (16-bit) 

 | Bảng mã Unicode 

 | Lưu trữ duy nhất một ký tự. Định dạng bằng nháy đơn `' '`.

 |
| **Logical** | <br>`boolean` 

 | 1 Bit 

 | <br>`true` hoặc `false` 

 | Điều hướng luồng chương trình trong các cấu trúc rẽ nhánh và logic.

 |

> 💡 **Network Optimization Note:** Kiểu `byte` (1 Byte) và `short` (2 Bytes) ít được sử dụng trong logic thông thường, nhưng đóng vai trò tối ưu hóa băng thông luồng dữ liệu (Data Stream) trong lập trình Socket mạng.
> 
> 

---

## 3. Variables & Naming Conventions

### Variable Syntax

```java
DataType variableName;             // Declaration
DataType variableName = value;    // Initialization

```

### Syntax Constraints (Quy tắc bắt buộc)

1. 
**Numeric Restriction:** Không cho phép ký tự đầu tiên của tên biến là chữ số (Ví dụ: `97Z` ❌, `Z97`  ).


2. 
**Special Characters:** Cấm sử dụng khoảng trắng và các ký tự đặc biệt, ngoại trừ dấu gạch dưới `_` và biểu tượng `$`.


3. 
**Reserved Keywords:** Không trùng với danh sách từ khóa hệ thống (Ví dụ: `int`, `class`, `public`).


4. 
**Case Sensitivity:** Trình biên dịch phân biệt chữ hoa và chữ thường (`total` và `Total` là hai thực thể độc lập).


5. 
**Scope Isolation:** Trong cùng một phạm vi hàm (Scope), không khai báo trùng tên biến.



### CamelCase Convention (Quy chuẩn công nghiệp)

* Áp dụng quy tắc **lowerCamelCase** cho toàn bộ tên biến: Chữ cái đầu tiên của từ thứ nhất viết thường, các từ tiếp theo viết hoa chữ cái đầu (Ví dụ: `banKinh`, `dienTich`, `luongNhanVien`).



---

## 4. Arithmetic Operators & Mathematical Rules

### Basic Operators

* Phép toán: `+`, `-`, `*`, `/` 


* Phép toán lấy dư: `%` (Trả về phần dư của phép chia nguyên. Ví dụ: `10 % 3 = 1`).



### Trình tự ưu tiên thực thi

> Trong ngoặc (`()`) ➡️ Nhân/Chia/Chia dư (`*`, `/`, `%`) ➡️ Cộng/Trừ (`+`, `-`) ➡️ Trình tự từ trái qua phải nếu cùng cấp.
> 
> 

### ⚠️ 4 Quy tắc tính toán ngầm định (Implicit Arithmetic Rules)

1. 
**Integer Arithmetic:** Biểu thức chỉ chứa các toán hạng số nguyên (`int`, `short`, `byte`) luôn trả về kết quả số nguyên (Phần thập phân bị cắt bỏ, không làm tròn). Ví dụ: `100 / 30 = 3`.


2. 
**Floating-Point Promotion:** Biểu thức chứa ít nhất một toán hạng số thực (`float`, `double`) sẽ tự động nâng cấp (Promote) toàn bộ biểu thức sang kiểu số thực. Ví dụ: `100 / 30.0 = 3.3333333333333335`.


3. 
**Integer Evaluation:** Các phép toán trên kiểu dữ liệu `int` sinh ra kết quả trung gian kiểu `int` trước khi thực hiện lệnh gán sang biến đích.


4. 
**Long Promotion:** Biểu thức chứa ít nhất một toán hạng kiểu `long` sẽ kích hoạt tính toán trên toàn bộ biểu thức bằng kiểu `long`.



---

## 5. Type Casting Techniques (Kỹ thuật ép kiểu kỹ sư)

### Floating-Point Division (Giữ phần thập phân)

Khi chia hai số nguyên, cần ép kiểu một toán hạng sang `double` trước khi thực hiện phép tính để tránh bị mất dữ liệu thập phân.

```java
int a = 100, b = 30;
double result1 = (double) a / b;   // Đúng: Ép kiểu trực tiếp toán hạng a
double result2 = 1.0 * a / b;      // Đúng: Nhân với hằng số double 1.0 (Khuyên dùng)

// Anti-Pattern (Lỗi logic phổ biến):
double wrongResult = (double) (a / b); // Sai: Tính toán chia nguyên (100/30 = 3) xong mới ép kiểu thành 3.0

```

### Integer Overflow Prevention (Chống tràn số)

Khi thực hiện nhân các số `int` có tiềm ẩn kết quả lớn hơn $2 \times 10^9$, bắt buộc phải chuyển đổi toán hạng đầu tiên sang kiểu `long` bằng hậu tố `L` hoặc ép kiểu.

```java
int a = 1_000_000;
int b = 5_000_000;
long validProduct1 = (long) a * b; // Đúng: Chuyển đổi a sang long trước khi nhân với b
long validProduct2 = 1L * a * b;   // Đúng: Đẩy hằng số 1 kiểu Long lên đầu biểu thức

// Anti-Pattern (Lỗi logic phổ biến):
long overflowProduct = a * b * 1L; // Sai: Phép tính a * b bị tràn số ở kiểu int trước khi gặp hằng số 1L

```

---

## 6. I/O Stream Management (Nhập/Xuất Dữ Liệu)

### Standard Output Stream (Dòng xuất)

* 
`System.out.print()`: Đẩy dữ liệu ra bảng điều khiển (Console), không chèn ký tự ngắt dòng.


* 
`System.out.println()`: Đẩy dữ liệu ra Console và tự động chèn ký tự xuống dòng (`\n`).


* 
`System.out.printf()`: Xuất dữ liệu theo định dạng đặc tả (Định dạng tương tự ngôn ngữ C).


* 
*Ứng dụng:* Giới hạn chữ số thập phân (Ví dụ lấy 2 chữ số sau dấu phẩy: `System.out.printf("%.2f\n", variable);`).





### Standard Input Stream (Dòng nhập với Scanner)

Khai báo import bắt buộc tại phần đầu tệp nguồn: `import java.util.Scanner;`.

```java
Scanner sc = new Scanner(System.in); // Khởi tạo instance Scanner đọc luồng hệ thống

int i     = sc.nextInt();     // Đọc luồng dữ liệu kiểu int
long l    = sc.nextLong();    // Đọc luồng dữ liệu kiểu long
float f   = sc.nextFloat();   // Đọc luồng dữ liệu kiểu float
double d  = sc.nextDouble();  // Đọc luồng dữ liệu kiểu double
boolean b = sc.nextBoolean(); // Đọc luồng dữ liệu kiểu boolean

// Mẹo xử lý luồng ký tự đơn (Java không hỗ trợ sc.nextChar()):
char c = sc.next().charAt(0); // Đọc một token chuỗi và trích xuất ký tự tại index 0

sc.close(); // Đóng luồng nhằm giải phóng tài nguyên hệ thống (Resource Leak Prevention)

```

> ⚠️ **Runtime Exception:** Việc nhập sai định dạng dữ liệu được chỉ định (Ví dụ: Nhập chuỗi văn bản hoặc số thực vào hàm `nextInt()`) sẽ khiến JVM ném ra ngoại lệ `java.util.InputMismatchException` và đình chỉ chương trình ngay lập tức.
> 
> 

---

## 7. Math API Reference

Toàn bộ các hàm toán học tĩnh nằm trong lớp `java.lang.Math` và được kích hoạt tự động mà không cần import cấu trúc.

* 
`Math.abs(x)`: Trả về giá trị tuyệt đối.


* 
`Math.max(a, b)` / `Math.min(a, b)`: Trả về giá trị cực đại / cực tiểu giữa 2 tham số.


* 
`Math.sqrt(x)`: Trả về căn bậc hai (Kiểu dữ liệu trả về mặc định: `double`).


* 
`Math.cbrt(x)`: Trả về căn bậc ba (Kiểu dữ liệu trả về mặc định: `double`).


* 
`Math.pow(x, y)`: Trả về lũy thừa $x^y$ (Kiểu dữ liệu trả về mặc định: `double`).



> ⚠️ **Cảnh báo định dạng của `Math.pow`:** Vì hàm trả về kiểu `double`, khi thực hiện tính toán trên tập số nguyên lớn, dữ liệu xuất ra sẽ tự động chuyển về dạng ký tự khoa học (Ví dụ: `2.43E+13`). Để hiển thị cấu trúc số nguyên chuẩn, bắt buộc phải ép kiểu thu hẹp (Narrowing Casting) kết quả về `long`.
> 
> 
> ```java
> long exactValue = (long) Math.pow(x, y);
> 
> ```
> 
>
