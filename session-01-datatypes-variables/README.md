

---

# ☕ Java Căn Bản: Biến, Kiểu Dữ Liệu, Toán Tử & Nhập Xuất

## 1. Công cụ lập trình & Cấu trúc file Java (Setup & Structure)

* **Các IDE phổ biến:** NetBeans, Eclipse, IntelliJ IDEA, VS Code. Giáo viên khuyến khích sử dụng công cụ có sẵn thay vì biên dịch online để quản lý dự án lâu dài.


* **Trình biên dịch Online:** Chỉ nên dùng tạm thời (ví dụ: OnlineGDB) khi máy lỗi. Không dùng lâu dài vì khó quản lý các file mã nguồn khi dự án lên tới hàng trăm dòng.


* **Cấu trúc một file Java bắt buộc:**
* Mọi mã nguồn xử lý đều phải được đặt bên trong một lớp (`class`).


* Tên của `public class` phải trùng hoàn toàn với tên file `.java`.


* 
**Gói (`package`):** Dùng để phân loại và quản lý các file mã nguồn (như các thư mục nhỏ).


* ⚠️ **Lưu ý khi nộp bài chấm tự động (OJ):** Khi nộp bài lên các hệ thống online như OJ, **phải xóa dòng khai báo `package**` ở đầu file để tránh bị lỗi biên dịch (CE).




* 
**Hàm `main` (Điểm khởi đầu):** Là nơi chương trình bắt đầu thực thi.


```java
public class Main {
    public static void main(String[] args) {
        // Câu lệnh thực thi đặt ở đây
    }
}

```



---

## 2. Các kiểu dữ liệu cơ bản (Primitive Data Types)

Java hỗ trợ 8 kiểu dữ liệu nguyên thủy, trong đó có 6 kiểu cốt lõi cần nhớ:

| Nhóm dữ liệu | Kiểu dữ liệu | Kích thước | Giới hạn lưu trữ (Ước lượng) | Ghi chú & Ứng dụng |
| --- | --- | --- | --- | --- |
| **Số nguyên** | `int` | 4 bytes (32-bit) 

 | <br>$-2 \times 10^9$ đến $2 \times 10^9$ (Tối đa 10 chữ số) 

 | Dùng phổ biến nhất cho số nguyên thông thường.

 |
|  | `long` | 8 bytes (64-bit) 

 | <br>$-9 \times 10^{18}$ đến $9 \times 10^{18}$ (Tối đa 19 chữ số) 

 | Dùng khi dữ liệu hoặc kết quả tính toán có thể cực lớn.

 |
| **Số thực** | `float` | 4 bytes (32-bit) 

 | Độ chính xác đơn (6 - 7 chữ số sau dấu phẩy) 

 | Ít dùng, khi gán hằng số cần thêm hậu tố `F` hoặc `f`.

 |
|  | `double` | 8 bytes (64-bit) 

 | Độ chính xác kép (15 - 16 chữ số sau dấu phẩy) 

 | <br>**Ưu tiên dùng** để đảm bảo độ chính xác cao, giảm sai số.

 |
| **Ký tự** | `char` | 2 bytes (16-bit) 

 | Bảng mã **Unicode** 

 | Chỉ lưu *một* ký tự duy nhất, đặt trong nháy đơn `' '`.

 |
| **Logic** | `boolean` | 1 bit 

 | Chỉ nhận `true` hoặc `false` 

 | Dùng trong các cấu trúc rẽ nhánh, phép toán điều kiện.

 |

> 📌 *Mở rộng:* Kiểu `byte` (1 byte) và `short` (2 bytes) rất ít dùng trong thuật toán thông thường, chủ yếu ứng dụng trong lập trình mạng (Socket) để tối ưu hóa dung lượng truyền tải giữa Client - Server.
> 
> 

---

## 3. Khai báo biến & Quy tắc đặt tên (Variables & Naming Conventions)

### Cú pháp cơ bản

```java
Kiểu_Dữ_Liệu Tên_Biến;              [cite_start]// Khai báo biến [cite: 135]
Kiểu_Dữ_Liệu Tên_Biến = Giá_Trị;     [cite_start]// Khai báo kết hợp khởi tạo [cite: 153, 154]
int x, y, z;                        [cite_start]// Khai báo nhiều biến cùng kiểu trên một dòng [cite: 142]

```

### Quy tắc đặt tên biến bắt buộc (Syntax Rules)

* Không được bắt đầu bằng chữ số (Ví dụ: `97Z` ❌, `Z97`  ).


* Không chứa khoảng trắng hoặc các ký tự đặc biệt (ngoại trừ ký tự `_` và `$`).


* Không trùng với các từ khóa (`keywords`) có sẵn của Java (Ví dụ: `int`, `class`, `public`...).


* Java có phân biệt chữ hoa chữ thường (Ví dụ: `a` và `A` là hai biến hoàn toàn khác nhau).


* Trong cùng một hàm, không được phép khai báo hai biến trùng tên nhau.



### Quy chuẩn đặt tên của cộng đồng Java (CamelCase Convention)

* 
**Quy tắc Lạc đà (camelCase):** Từ đầu tiên viết thường toàn bộ, các từ tiếp theo viết hoa chữ cái đầu tiên (Ví dụ: `banKinh`, `dienTich`, `luongNhanVien`, `diemTrungBinh`). Đây là tiêu chuẩn chung bắt buộc toàn cầu khi đi học và đi làm.



---

## 4. Các toán tử toán học & 4 Quy tắc ngầm định (Operators)

### Các toán tử cơ bản

* 
`+`, `-`, `*`, `/` (Phép chia).


* 
`%` (Phép chia lấy dư): Chỉ lấy phần dư của phép chia nguyên (Ví dụ: `10 % 3 = 1`, `1 % 10 = 1`).



### ⚠️ 4 Quy tắc tính toán ngầm định buộc phải nằm lòng

1. 
**Biểu thức toàn số nguyên (`int`, `long`...):** Kết quả trả về luôn luôn là một số nguyên (mất phần thập phân). Ví dụ: `100 / 30 = 3`.


2. 
**Biểu thức chứa ít nhất một số thực (`float`, `double`):** Kết quả tự động chuyển sang số thực. Ví dụ: `100 / 30.0 = 3.3333`.


3. 
**Biểu thức gồm các toán hạng `int`:** Kết quả trung gian tạm thời được lưu trữ dưới kiểu `int` trước khi gán sang biến nhận.


4. 
**Biểu thức chứa ít nhất một toán hạng `long`:** Toàn bộ biểu thức tính toán sẽ tự động được xử lý dưới kiểu `long`.



---

## 5. Kỹ thuật ép kiểu nâng cao (Type Casting)

### Giữ phần thập phân khi chia hai số nguyên

Nếu thực hiện phép chia hai biến kiểu `int`, Java sẽ thực hiện chia nguyên. Để lấy kết quả số thực, ta phải ép kiểu một trong hai biến sang số thực trước khi chia.

```java
int a = 100, b = 30;
double thuong1 = (double) a / b;   [cite_start]// Cách 1: Ép kiểu trực tiếp biến a [cite: 254]
double thuong2 = 1.0 * a / b;      [cite_start]// Cách 2: Nhân với 1.0 để tự động chuyển sang double (Ưu tiên dùng) [cite: 261, 262]

// ❌ SAI LẦM PHỔ BIẾN:
double thuong3 = (double) (a / b); // Sai! [cite_start]Hệ thống chia nguyên ra 3 trước rồi mới ép thành 3.0 [cite: 258]

```

### Phòng chống tràn số khi nhân các số nguyên `int`

Khi nhân các số nguyên có giá trị lớn hơn $2 \times 10^9$ (ví dụ: Tính diện tích hình chữ nhật có cạnh là $10^6$), kết quả trung gian sẽ bị tràn số kiểu `int` dẫn tới sai lệch dữ liệu. Ta phải ép kiểu toán hạng đầu tiên sang `long`.

```java
int a = 1000000; // 1 triệu
int b = 5000000; // 5 triệu
long tich1 = (long) a * b; [cite_start]// Ép biến 'a' sang long trước rồi mới nhân b [cite: 271, 274]
long tich2 = 1L * a * b;   [cite_start]// Nhân với hằng số 1 kiểu Long (1L) ở đầu biểu thức [cite: 275]

// ❌ SAI LẦM PHỔ BIẾN:
long tich3 = a * b * 1L;   // Sai! [cite_start]Phép toán tính từ trái qua phải, a * b bị tràn trước khi gặp 1L [cite: 276, 277]

```

---

## 6. Nhập/Xuất dữ liệu (Scanner & Output)

### Xuất dữ liệu ra màn hình (Output)

* 
`System.out.print()`: In dữ liệu nhưng không tự động xuống dòng.


* 
`System.out.println()`: In dữ liệu và **tự động xuống dòng** (viết tắt của print line).


* 
`System.out.printf()`: In dữ liệu theo đặc tả/định dạng (tương tự ngôn ngữ C). Đặc biệt hữu ích khi giới hạn số chữ số sau dấu thập phân.


* Cú pháp in số thực lấy 2 chữ số sau dấu phẩy kèm xuống dòng (`\n`):
```java
[cite_start]System.out.printf("%.2f\n", bien_so_thuc); [cite: 173, 174]

```




* 
**Phép nối chuỗi (`+`):** Khi nối một chuỗi văn bản với một biến số, Java tự động chuyển đổi biến số đó thành chuỗi văn bản để ghép lại với nhau.


```java
[cite_start]System.out.println("Chu vi hình chữ nhật là: " + chuVi); [cite: 46, 285]

```



### Nhập dữ liệu từ bàn phím (Scanner)

Cần import thư viện ở trên cùng, phía trước khai báo `class`: `import java.util.Scanner;`.

```java
Scanner sc = new Scanner(System.in); [cite_start]// Khởi tạo luồng đọc dữ liệu từ bàn phím [cite: 177]

int x = sc.nextInt();         [cite_start]// Nhập số nguyên kiểu int [cite: 180]
long y = sc.nextLong();       [cite_start]// Nhập số nguyên lớn kiểu long [cite: 180, 236]
float f = sc.nextFloat();     [cite_start]// Nhập số thực kiểu float [cite: 180]
double d = sc.nextDouble();   [cite_start]// Nhập số thực lớn kiểu double [cite: 180]
boolean b = sc.nextBoolean(); // Nhập giá trị logic true/false

// ⚠️ Mẹo nhập ký tự (Java không hỗ trợ hàm sc.nextChar()):
char c = sc.next().charAt(0); [cite_start]// Đọc một từ dưới dạng chuỗi rồi trích xuất ký tự đầu tiên tại chỉ số 0 [cite: 75, 183]

sc.close(); [cite_start]// Đóng Scanner để giải phóng tài nguyên hệ thống [cite: 188]

```

> ⚠️ **Lỗi ngoại lệ `InputMismatchException`:** Nếu gọi hàm `nextInt()` nhưng người dùng cố tình nhập vào một số thực (`3.4`), một chuỗi văn bản, hoặc một số nguyên vượt quá phạm vi của kiểu `int`, chương trình sẽ lập tức ném lỗi ngoại lệ này và dừng hoạt động ngay lập tức.
> 
> 

---

## 7. Các hàm thường dùng trong lớp toán học `Math`

Các hàm toán học nằm trong lớp `Math` được tích hợp sẵn trong nhân Java, không cần cài đặt hay import thư viện ngoài.

* 
`Math.abs(x)`: Trả về giá trị tuyệt đối của số $x$.


* 
`Math.max(a, b)` / `Math.min(a, b)`: Trả về số lớn nhất / nhỏ nhất giữa 2 số.


* 
`Math.sqrt(x)`: Tính căn bậc hai $\sqrt{x}$ (Trả về dữ liệu kiểu `double`).


* 
`Math.cbrt(x)`: Tính căn bậc ba $\sqrt[3]{x}$ (Trả về dữ liệu kiểu `double`).


* 
`Math.pow(x, y)`: Tính lũy thừa $x^y$ (Trả về dữ liệu kiểu `double`).



> ⚠️ **Lưu ý chí mạng khi sử dụng `Math.pow`:**
> Vì hàm này luôn trả về kiểu số thực (`double`), khi làm việc với số nguyên lớn hoặc tính lũy thừa nguyên dương, nếu in trực tiếp ra màn hình, hệ thống sẽ hiển thị theo ký tự khoa học (dạng như $2.43E+13$). Bạn bắt buộc phải thực hiện **ép kiểu kết quả về `long**` trước khi hiển thị để cấu trúc số nguyên hiển thị chính xác.
> 
> 
> ```java
> long ketQuaNguyen = (long) Math.pow(x, y); [cite_start]// Ép kiểu chuẩn số nguyên [cite: 54, 300]
> 
> ```
> 
>
