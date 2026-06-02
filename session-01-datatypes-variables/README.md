
```markdown
# ☕ CƠ BẢN VỀ JAVA: KIỂU DỮ LIỆU, BIẾN, TOÁN TỬ & RẼ NHÁNH

> [cite_start]📌 **Nguồn tài liệu:** Lộ trình phát triển tư duy lập trình viên 28Tech[cite: 4, 12, 140].
> [cite_start]🎯 **Mục tiêu mục này:** Làm chủ cú pháp căn bản, kiểm soát bộ nhớ RAM và phòng chống các bẫy logic/tràn số khi chấm bài tự động trên hệ thống (OJ)[cite: 15, 27, 240].

---

## 📂 1. Hệ Thống Kiểu Dữ Liệu & Biến (Data Types & Variables)

### a. Bảng tra cứu kích thước bộ nhớ
Java là ngôn ngữ lập trình định kiểu nghiêm ngặt. [cite_start]Cần ghi nhớ kích thước của từng kiểu dữ liệu nguyên thủy để tối ưu hóa thuật toán[cite: 15, 17]:

| Kiểu dữ liệu | Kích thước | [cite_start]Phạm vi giá trị & Đặc tính cốt lõi [cite: 17] |
| :--- | :---: | :--- |
| `byte` | 1 byte | [cite_start]Từ $-128$ đến $127$ [cite: 17] |
| `short` | 2 byte | [cite_start]Từ $-32,768$ đến $32,767$ [cite: 17] |
| `int` | 4 byte | Từ $-2^{31}$ đến $2^{31}-1$ (~2 tỷ). [cite_start]**Là kiểu số nguyên mặc định.** [cite: 17] |
| `long` | 8 byte | Từ $-2^{63}$ đến $2^{63}-1$. [cite_start]**Dùng cho số cực lớn, cần hậu tố `L` hoặc `l`.** [cite: 17, 120] |
| `float` | 4 byte | Số thực độ chính xác từ 6 - 7 chữ số sau dấu phẩy. [cite_start]**Cần hậu tố `F` hoặc `f`.** [cite: 17, 121] |
| `double` | 8 byte | Số thực độ chính xác tới 15 chữ số sau dấu phẩy. [cite_start]**Kiểu số thực mặc định.** [cite: 17, 122] |
| `char` | 2 byte | [cite_start]Lưu 1 kí tự đơn duy nhất, bọc trong dấu nháy đơn `' '`[cite: 17, 131]. |
| `boolean` | 1 byte | [cite_start]Chỉ nhận một trong hai giá trị logic: `true` hoặc `false`[cite: 17, 132]. |

### b. Quy tắc đặt tên biến & Name Convention
```text
1. [cite_start]KHÔNG bắt đầu bằng chữ số (Ví dụ sai: 1dientich, 2chuvi)[cite: 48].
2. [cite_start]KHÔNG chứa khoảng trắng hay ký tự đặc biệt (Ví dụ sai: ban kinh, dien#tich)[cite: 48].
3. [cite_start]KHÔNG trùng tên từ khóa của hệ thống (Ví dụ: int, main, for, while...)[cite: 48].
4. [cite_start]CÓ phân biệt chữ hoa và chữ thường (Ví dụ: 'banKinh' và 'BanKinh' là khác nhau)[cite: 48].
5. CAMELCASE (Quy tắc lạc đà): Viết thường từ đầu tiên, các từ tiếp theo viết 
   [cite_start]hoa chữ cái đầu tiên (Ví dụ chuẩn: banKinh, dienTich, luongNhanVien)[cite: 63, 64].

```

### c. Chú thích (Comment) trong mã nguồn

* 
`// Chú thích dòng đơn`: Dùng để giải thích nhanh một dòng lệnh.


* 
`/* Chú thích nhiều dòng */`: Dùng để giải thích một cụm hoặc một thuật toán dài.


* 
*Lưu ý:* Chú thích sẽ tự động được loại bỏ hoàn toàn khi chương trình thực thi.



---

## 📥 2. Kỹ Thuật Nhập Xuất Dữ Liệu (Scanner & Print)

```java
import java.util.Scanner; [cite_start]// Bắt buộc phải import thư viện lớp này ở đầu file [cite: 181]

public class Main {
    public static void main(String[] args) {
        [cite_start]// Khởi tạo đối tượng luồng nhập dữ liệu từ bàn phím [cite: 182, 183]
        Scanner sc = new Scanner(System.in); 
        
        [cite_start]// Cú pháp đọc dữ liệu theo từng kiểu tương ứng [cite: 183, 184, 185]
        int n = sc.nextInt();         
        long m = sc.nextLong();       
        float f = sc.nextFloat();     
        double d = sc.nextDouble();   
        char c = sc.nextLine().charAt(0); [cite_start]// Đọc ký tự đầu tiên của dòng [cite: 189]
        
        [cite_start]// 🚨 CHÚ Ý: Nhập sai kiểu dữ liệu sẽ quăng lỗi InputMismatchException[cite: 186, 187].
        [cite_start]// Ví dụ: Đang dùng nextInt() nhưng người dùng lại nhập ký tự chữ hoặc số thực[cite: 188].
    }
}

```

### 🌐 Định dạng hiển thị số thực với độ chính xác cho trước

Để kiểm soát số lượng chữ số phần thập phân hiển thị ra màn hình, ta sử dụng hàm `System.out.printf()` thay cho `print` thông thường:

```java
float chuVi = 3.18238f;
double dienTich = 39.91293912391293d;

System.out.printf("%.2f\n", chuVi);     [cite_start]// Output thực tế: 3.18 [cite: 167, 169]
System.out.printf("%.10f\n", dienTich); [cite_start]// Output thực tế: 39.9129391239 [cite: 167, 169]

```

---

## ⚡ 3. Hệ Thống Toán Tử & Các "Bẫy" Thuật Toán

### a. 

Danh sách toán tử toán học cốt lõi 

* 
`+`, `-`, `*`: Cộng, trừ, nhân.


* 
`/`: Chia lấy phần nguyên (Nếu cả 2 toán hạng đều là số nguyên).


* 
`%`: Chia lấy phần dư.



### 🚨 Bẫy 1: Chia mất phần thập phân (Integer Division)

* 
**Nguyên nhân:** Chia 2 số nguyên cho nhau, Java sẽ tự động cắt bỏ hoàn toàn phần thập phân của thương số.


* 
**Giải pháp:** Ít nhất 1 trong 2 toán hạng tham gia phép tính phải ở dạng số thực.



```java
int a = 300, b = 200;
// Cách xử lý sai: int c = a / b; [cite_start]-> Trả về kết quả = 1 (Bị mất .5) [cite: 228]
[cite_start]// Cách xử lý đúng: Ép kiểu một toán hạng sang kiểu float hoặc double [cite: 228]
float d = (float) a / b; [cite_start]// Trả về kết quả chính xác = 1.50 [cite: 228]

```

### 🚨 Bẫy 2: Tràn số khi nhân hai số nguyên (Integer Overflow)

* 
**Nguyên nhân:** Tích của 2 số kiểu `int` vượt quá giới hạn ($\approx 2$ tỷ) sẽ bị lỗi dữ liệu rác ngay lập tức, ngay cả khi bạn khai báo biến lưu trữ là kiểu `long`.


* 
**Giải pháp:** Phải can thiệp ép kiểu dữ liệu ngay trong quá trình tính toán.



```java
int a = 1000000, b = 1000000;
// Cách xử lý sai: long c = a * b; [cite_start]-> Kết quả lỗi: -727379968 [cite: 247, 248, 251]

[cite_start]// Cách xử lý đúng 1: Ép kiểu một trong hai biến sang long [cite: 250]
long d = (long) a * b; [cite_start]// Kết quả chuẩn: 1000000000000 [cite: 250, 251]

[cite_start]// Cách xử lý đúng 2: Nhân trực tiếp với hằng số kiểu long 1L ở đầu [cite: 250]
long e = 1L * a * b;   [cite_start]// Kết quả chuẩn: 1000000000000 [cite: 250, 251]

```

### b. Các toán tử logic & So sánh nâng cao

* 
**Toán tử so sánh (Trả về đúng/sai):** `>`, `>=`, `<`, `<=`, `!=` (So sánh khác), `==` (So sánh bằng).


* **Toán tử logic kết hợp nhiều biểu thức:**
* 
`&&` (Phép AND): Chỉ cho kết quả đúng khi mọi mệnh đề thành phần đều đúng.


* 
`||` (Phép OR): Chỉ cho kết quả sai khi tất cả đều sai, đúng khi có ít nhất 1 cái đúng.


* 
`!` (Phép NOT): Phủ định ngược lại giá trị logic hiện tại.




* 
**Toán tử tăng giảm đơn vị:** `++a` (Tăng trước khi tính), `a++` (Tăng sau khi tính), tương tự với `--`.


* **Toán tử ba ngôi:** `[Biểu thức] ? [cite_start][Giá trị khi Đúng] : [Giá trị khi Sai];`.



---

## 🔤 4. Bản Chất Ký Tự & Bảng Mã ASCII

Bản chất kiểu dữ liệu `char` được lưu trữ dưới dạng mã số nguyên trong bảng mã ASCII gồm 256 ký tự. Do đó, ký tự hoàn toàn có thể tham gia vào các phép tính cộng, trừ, nhân, chia. Khi tính toán, hệ thống sẽ tự động dùng mã số ASCII của nó.

```text
Dải mã ASCII cốt lõi bắt buộc phải thuộc lòng:
+ [cite_start]Ký tự chữ cái IN HOA ('A' - 'Z') : Từ mã số 65 đến 90[cite: 537].
+ [cite_start]Ký tự chữ cái in thường ('a' - 'z') : Từ mã số 97 đến 122[cite: 537].
+ [cite_start]Ký tự chữ số từ ('0' - '9')         : Từ mã số 48 đến 57[cite: 537].

```

### 🔥 Các đoạn code mẫu kiểm tra và xử lý biến đổi ký tự gốc (Thuộc bản chất)

```java
char c = 'a';

// 1. Kiểm tra tính chất ký tự bằng khoảng ký tự hoặc mã số nguyên trực tiếp
boolean isLower = (c >= 'a' && c <= 'z'); [cite_start]// Kiểm tra kí tự in thường [cite: 558, 559]
boolean isUpper = (c >= 'A' && c <= 'Z'); [cite_start]// Kiểm tra kí tự in hoa [cite: 554, 561]
boolean isDigit = (c >= '0' && c <= '9'); [cite_start]// Kiểm tra kí tự là chữ số [cite: 564, 566]

[cite_start]// 2. Chuyển đổi ký tự (Dựa trên khoảng cách 32 đơn vị trong bảng mã ASCII) [cite: 568, 571]
char upCase = (char) (c - 32);  [cite_start]// Biến 'a' thành chữ IN HOA 'A' tương ứng [cite: 570, 571, 572]
char lowCase = (char) (c + 32); [cite_start]// Biến 'A' thành chữ in thường 'a' tương ứng [cite: 568, 569]

```

---

## 🔀 5. Các Cấu Trúc Điều Khiển Rẽ Nhánh (Control Structures)

### a. Khối lệnh `if` - `else if` - `else`

```text
[cite_start]Cơ chế vận hành quan trọng: Hệ thống kiểm tra tuần tự các điều kiện từ trên xuống[cite: 487]. 
[cite_start]Ngay khi phát hiện ra MỘT điều kiện đúng, khối lệnh của nhánh đó sẽ được thực thi[cite: 487]. 
[cite_start]Sau khi thực hiện xong, TOÀN BỘ cấu trúc rẽ nhánh này sẽ KẾT THÚC NGAY LẬP TỨC[cite: 487]. 
[cite_start]Các điều kiện còn lại ở phía dưới (bao gồm cả khối else) sẽ bị bỏ qua hoàn toàn[cite: 487, 488].

```

### b. Cấu trúc `switch` - `case` và lỗi chí mạng về từ khóa `break`

Dùng để so sánh giá trị bằng cụ thể của một biến (`val` có thể là số, ký tự, hoặc chuỗi văn bản):

```java
switch (val) {
    case 1:
        [cite_start]// Đoạn mã thực thi khi val == 1 [cite: 503, 510, 511]
        break; [cite_start]// Ép chương trình thoát khỏi khối switch ngay lập tức [cite: 506, 512]
    case 2:
        [cite_start]// Đoạn mã thực thi khi val == 2 [cite: 513, 514]
        break; [cite_start]// [cite: 515]
    default:
        [cite_start]// Đoạn mã thực thi khi val không trùng khớp với bất kỳ trường hợp nào trên [cite: 504, 518, 519]
}

// 🚨 LƯU Ý CHÍ MẠNG: Nếu bạn bỏ quên câu lệnh "break;", chương trình sẽ rơi vào trạng thái
[cite_start]// "lọt rãnh" (Fall-through) - tự động chạy tiếp xuống các case bên dưới mà không kiểm tra lại điều kiện[cite: 506].

```

