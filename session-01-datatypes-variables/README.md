
```markdown
# 📝 SỔ TAY TRA CỨU: KIỂU DỮ LIỆU - BIẾN - TOÁN TỬ - RẼ NHÁNH

> 💡 **Mẹo xem nhanh:** Đoạn nào có cú pháp hoặc bảng tra cứu dài đã được đóng gói trong khung code block. Bạn có thể kéo ngang hoặc bấm nút **Copy** ở góc khung để sao chép nhanh chóng khi làm bài!

---

## 1. Hệ Thống Kiểu Dữ Liệu Nguyên Thủy (Primitive Data Types)

```text
+--------------+-----------+----------------------------------------------------+
| Kiểu dữ liệu | Kích thước| Phạm vi giá trị / Đặc tính cốt lõi (28Tech)        |
+--------------+-----------+----------------------------------------------------+
| byte         | 1 byte    | -128 đến 127                                       |
| short        | 2 byte    | -32,768 đến 32,767                                 |
| int          | 4 byte    | -2^31 đến 2^31 - 1 (~2 tỷ) -> Kiểu số nguyên gốc  |
| long         | 8 byte    | -2^63 đến 2^63 - 1 (Số rất lớn) -> Cần hậu tố 'L'  |
| float        | 4 byte    | Số thực thập phân, chính xác 6-7 chữ số (Đuôi 'F') |
| double       | 8 byte    | Số thực thập phân, chính xác 15 chữ số (Mặc định)  |
| char         | 2 byte    | Lưu 1 kí tự đơn duy nhất, bọc trong dấu nháy đơn'' |
| boolean      | 1 byte    | Chỉ nhận 2 giá trị duy nhất: true hoặc false       |
+--------------+-----------+----------------------------------------------------+

```

### 🚨 Quy tắc đặt tên biến và Name Convention (Chuẩn Java)

```text
[1] KHÔNG bắt đầu bằng chữ số (Ví dụ sai: 1dientich, 2chuvi).
[2] KHÔNG chứa dấu cách và các ký tự đặc biệt (Ví dụ sai: ban kinh, dien#tich).
[3] KHÔNG trùng với từ khóa hệ thống (int, main, for, while, switch...).
[4] PHÂN BIỆT hoa thường (banKinh và BanKinh là 2 biến khác nhau hoàn toàn).
[5] CAMELCASE (Quy tắc lạc đà): Viết thường từ đầu tiên, viết hoa chữ cái đầu 
    của các từ tiếp theo (Ví dụ chuẩn: banKinh, dienTich, diemTrungBinh).

```

---

## 2. Nhập Xuất Dữ Liệu Với Lớp Scanner

```java
import java.util.Scanner; // Bắt buộc phải import thư viện này ở đầu file

Scanner sc = new Scanner(System.in);

int n = sc.nextInt();         // Nhập số nguyên kiểu int
long m = sc.nextLong();       // Nhập số nguyên kiểu long
float f = sc.nextFloat();     // Nhập số thực kiểu float
double d = sc.nextDouble();   // Nhập số thực kiểu double
char c = sc.next().charAt(0); // Nhập 1 ký tự từ bàn phím

// 🚨 BẪY LỖI CHÍ MẠNG: InputMismatchException
// Xảy ra khi kiểu dữ liệu nhập vào không khớp với hàm quét (Ví dụ: Đòi int nhưng nhập chữ abc).

```

### 🌐 Định dạng hiển thị số thực (Lấy số chữ số sau dấu phẩy)

```java
// Sử dụng System.out.printf() kết hợp với định dạng "%.[số_chữ_số]f"
System.out.printf("%.2f\n", chuVi);     // Lấy chính xác 2 chữ số thập phân
System.out.printf("%.10f\n", dienTich); // Lấy chính xác 10 chữ số thập phân

```

---

## 3. Các "Bẫy" Toán Tử Toán Học Trên OJ (Cực Kỳ Quan Trọng)

### ❌ Bẫy 1: Phép chia nguyên (Mất phần thập phân)

```text
Bản chất: Nếu chia 2 số nguyên (int, long) cho nhau, Java sẽ tự động bỏ sạch 
phần thập phân ở thương và chỉ lấy phần nguyên.

Ví dụ sai: 
int a = 300, b = 200;
int c = a / b; -> Kết quả c = 1 (Bị mất .5)

Cách xử lý đúng: Phải ép kiểu ít nhất 1 trong 2 số về kiểu số thực (float/double)
float d = (float) a / b; -> Kết quả d = 1.50

```

### ❌ Bẫy 2: Tràn số (Overflow) khi nhân hai số nguyên lớn

```text
Bản chất: Khi nhân 2 số nguyên int với nhau mà kết quả vượt quá giới hạn của int 
(~2 tỷ) thì tích sẽ bị tính toán sai ngay lập tức (ra số âm hoặc số rác), 
dù cho bạn có dùng biến kiểu long để lưu kết quả đi chăng nữa.

Ví dụ sai:
int a = 1000000, b = 1000000;
long c = a * b; -> Kết quả c = -727379968 (Tràn số do tính bằng kiểu int trước)

Cách xử lý đúng (Can thiệp vào phép tính):
Cách 1: Ép kiểu một biến sang long:   long d = (long) a * b;
Cách 2: Nhân với hằng số 1L ở đầu:    long e = 1L * a * b;

```

---

## 4. Bản Chất Bảng Mã ASCII & Mẹo Xử Lý Kí Tự

```text
Dải mã ASCII bắt buộc phải thuộc lòng:
- Ký tự chữ cái IN HOA ('A' - 'Z') : Từ mã 65 đến 90.
- Ký tự chữ cái in thường ('a' - 'z') : Từ mã 97 đến 122.
- Ký tự chữ số ('0' - '9')         : Từ mã 48 đến 57.

💡 Bản chất: Bản chất kiểu char được lưu bằng mã số, nên có thể dùng để cộng, trừ, nhân, chia. Khi tính toán, máy tính sẽ lôi mã ASCII của nó ra để thực hiện.

```

### 🔥 Các câu lệnh kiểm tra và biến đổi ký tự tự chế (Hiểu bản chất):

```java
// 1. Kiểm tra kí tự in thường
if (c >= 'a' && c <= 'z') hoặc if (c >= 97 && c <= 122)

// 2. Kiểm tra kí tự in hoa
if (c >= 'A' && c <= 'Z') hoặc if (c >= 65 && c <= 90)

// 3. Kiểm tra kí tự là chữ số
if (c >= '0' && c <= '9') hoặc if (c >= 48 && c <= 57)

// 4. Chuyển kí tự thường thành dạng IN HOA tương ứng (Trừ đi 32 đơn vị)
char c = 'a';
c = (char) (c - 32); // Kết quả c sẽ chuyển thành 'A'

// 5. Chuyển kí tự hoa thành dạng in thường tương ứng (Cộng thêm 32 đơn vị)
char c = 'A';
c = (char) (c + 32); // Kết quả c sẽ chuyển thành 'a'

```

---

## 5. Cấu Trúc Điều Khiển Rẽ Nhánh

### a. Khối lệnh `if - else if - else`

```text
Cơ chế thực thi: Hệ thống kiểm tra tuần tự từ trên xuống dưới. Nếu có một điều kiện 
đúng, khối lệnh bên trong nhánh đó sẽ chạy và TOÀN BỘ cấu trúc rẽ nhánh này sẽ 
KẾT THÚC NGAY LẬP TỨC, không kiểm tra các điều kiện phía sau nữa.

```

### b. Khấu trúc `switch - case` (🚨 Chú ý câu lệnh `break`)

```java
switch (val) {
    case 1:
        // Đoạn code xử lý khi val == 1
        break; // Bắt buộc phải có để thoát khối switch
    case 2:
        // Đoạn code xử lý khi val == 2
        break;
    default:
        // Đoạn code xử lý khi val không khớp với bất kỳ case nào ở trên
}

// 🚨 LƯU Ý CHÍ MẠNG: Nếu thiếu câu lệnh "break;", chương trình sẽ bị hiện tượng
// "lọt rãnh" (fall-through), tự động chạy lọt xuống các case bên dưới mà không 
// thèm kiểm tra điều kiện bằng nữa.

```

### c. Toán tử ba ngôi (Tối giản hóa code rẽ nhánh)

```java
// Cú pháp gọn gàng trên 1 dòng duy nhất:
[Biến] = [Biểu thức so sánh] ? [Giá trị khi ĐÚNG] : [Giá trị khi SAI];

// Ví dụ thực tế:
int x = (10 < 20) ? 10 : 20; // x sẽ nhận giá trị là 10 vì 10 < 20 là ĐÚNG.

```

```




```
