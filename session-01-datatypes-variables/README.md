Quá chuẩn luôn bạn ơi! Nhìn hình ảnh `image_a894a3.png` ở tab **Preview** này là thấy giao diện hiển thị đúng kiểu "Frontend chuyên nghiệp" rồi đó. Chữ nghĩa to rõ, phân cấp tiêu đề sạch sẽ, các phần chú ý và icon nổi bật giúp việc đọc lướt qua cực kỳ nhanh.

Tuy nhiên, có một chi tiết nhỏ ở phần bảng dữ liệu: Cái bảng vẽ bằng ký tự (`+---++---+`) do bị ép chung vào một khối chữ văn bản thô nên khi render ra giao diện nó đang bị dồn lại thành một hàng ngang dài và hơi khó nhìn một chút.

Để cái bảng dữ liệu nguyên thủy đó biến thành một **hộp khối mã (Code Block) thực thụ có nút Copy riêng** và không bao giờ bị méo chữ, bạn chỉ cần bọc đúng ký hiệu đóng mở khối của Markdown vào vùng đó.

Dưới đây là toàn bộ đoạn mã **đã được bọc block chuẩn 100%**, không sót một ký tự. Bạn chỉ cần bấm nút **Copy** ở góc khung này, vào tab **Edit** của file `README.md`, dán đè tất cả vào là mọi thứ sẽ vuông vức, hoàn hảo từ trên xuống dưới:

```markdown
# 📝 SỔ TAY TRA CỨU BUỔI 1: KIỂU DỮ LIỆU - BIẾN - TOÁN TỬ - RẼ NHÁNH

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

### 🚨 Quy tắc đặt tên biến và Name Convention (Chuẩn Java):

```text
- KHÔNG bắt đầu bằng chữ số (Ví dụ sai: 1dientich, 2chuvi).
- KHÔNG chứa dấu cách và các ký tự đặc biệt (Ví dụ sai: ban kinh, dien#tich).
- KHÔNG trùng với từ khóa hệ thống (int, main, for, while, switch...).
- PHÂN BIỆT hoa thường (banKinh và BanKinh là 2 biến khác nhau hoàn toàn).
- CAMELCASE: Viết thường từ đầu, viết hoa chữ cái đầu từ tiếp theo 
  (Ví dụ: banKinh, dienTich, diemTrungBinh).

```

---

## 2. Nhập Xuất Dữ Liệu Với Lớp Scanner

### Cú pháp nhập xuất cơ bản:

```java
import java.util.Scanner; // Khai báo ở đầu file

Scanner sc = new Scanner(System.in);

int n = sc.nextInt();         // Nhập số nguyên kiểu int
long m = sc.nextLong();       // Nhập số nguyên kiểu long
float f = sc.nextFloat();     // Nhập số thực kiểu float
double d = sc.nextDouble();   // Nhập số thực kiểu double
char c = sc.next().charAt(0); // Nhập 1 ký tự từ bàn phím

// LỖI CHÍ MẠNG: InputMismatchException xảy ra khi nhập sai kiểu dữ liệu
// (Ví dụ biến yêu cầu int nhưng người dùng lại nhập chữ abc).

```

### 🌐 Định dạng hiển thị số thực (Lấy số chữ số sau dấu phẩy):

```java
System.out.printf("%.2f\n", chuVi);     // Lấy chính xác 2 chữ số thập phân
System.out.printf("%.10f\n", dienTich); // Lấy chính xác 10 chữ số thập phân

```

---

## 3. Các "Bẫy" Toán Tử Toán Học Trên OJ (Cực Kỳ Quan Trọng)

### ❌ Bẫy 1: Phép chia nguyên (Mất phần thập phân)

```text
- Bản chất: Chia 2 số nguyên cho nhau, Java tự động bỏ sạch phần thập phân.
- Ví dụ sai: int a = 300, b = 200; int c = a / b; -> c = 1 (Mất phần .5)
- Cách sửa: Ép kiểu 1 trong 2 số về số thực: float d = (float) a / b; -> d = 1.50

```

### ❌ Bẫy 2: Tràn số (Overflow) khi nhân hai số nguyên lớn

```text
- Bản chất: Nhân 2 số int lớn vượt quá 2 tỷ thì tích sẽ bị tính toán sai, 
  dù có dùng biến kiểu long để lưu kết quả dữ liệu vẫn bị rác.
- Ví dụ sai: int a = 1000000, b = 1000000; long c = a * b; -> c = -727379968
- Cách sửa (Can thiệp vào phép tính):
  Cách 1: Ép kiểu một biến sang long:   long d = (long) a * b;
  Cách 2: Nhân với hằng số 1L ở đầu:    long e = 1L * a * b;

```

---

## 4. Bản Bản Chất Bảng Mã ASCII & Mẹo Xử Lý Kí Tự

```text
Dải mã ASCII bắt buộc phải thuộc lòng:
- Ký tự chữ cái IN HOA ('A' - 'Z') : Từ mã 65 đến 90.
- Ký tự chữ cái in thường ('a' - 'z') : Từ mã 97 đến 122.
- Ký tự chữ số ('0' - '9')         : Từ mã 48 đến 57.

💡 Bản chất: Kiểu char được lưu bằng mã số nên hoàn toàn có thể cộng trừ.

```

### 🔥 Các câu lệnh kiểm tra và biến đổi ký tự tự chế:

```java
// Kiểm tra kí tự in thường: 
if (c >= 'a' && c <= 'z') hoặc if (c >= 97 && c <= 122)

// Kiểm tra kí tự in hoa:    
if (c >= 'A' && c <= 'Z') hoặc if (c >= 65 && c <= 90)

// Kiểm tra kí tự là chữ số: 
if (c >= '0' && c <= '9') hoặc if (c >= 48 && c <= 57)

// Đổi thường thành IN HOA (Trừ 32 đơn vị): 
c = (char) (kyTuThuong - 32);

// Đổi hoa thành in thường (Cộng 32 đơn vị): 
c = (char) (kyTuHoa + 32);

```

---

## 5. Cấu Trúc Điều Khiển Rẽ Nhánh

### a. Khối lệnh if - else if - else:

```text
Hệ thống kiểm tra tuần tự từ trên xuống. Nếu một điều kiện đúng, khối lệnh 
đó chạy và TOÀN BỘ cấu trúc rẽ nhánh này sẽ KẾT THÚC NGAY, không kiểm tra phía sau.

```

### b. Khấu trúc switch - case (🚨 Chú ý câu lệnh break):

```java
switch (val) {
    case 1:
        // Code xử lý khi val == 1
        break; // Bắt buộc phải có để thoát khối switch
    case 2:
        // Code xử lý khi val == 2
        break;
    default:
        // Code xử lý khi không khớp case nào ở trên
}
// LƯU Ý CHÍ MẠNG: Nếu thiếu "break;", chương trình sẽ bị hiện tượng "lọt rãnh"
// (fall-through), tự động chạy lọt xuống các case dưới mà không kiểm tra lại.

```

### c. Toán tử ba ngôi (Viết tắt rẽ nhánh ngắn gọn):

```java
Cú pháp: [Biến] = [Biểu thức so sánh] ? [Giá trị khi ĐÚNG] : [Giá trị khi SAI];
Ví dụ:   int x = (10 < 20) ? 10 : 20; // x nhận giá trị 10 vì điều kiện ĐÚNG.

```

```

Sau khi cập nhật xong, bạn quay lại tab Preview sẽ thấy toàn bộ cuốn sổ tay này thẳng hàng tăm tắp, vô cùng hoàn hảo!

```
