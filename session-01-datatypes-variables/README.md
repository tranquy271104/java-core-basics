# ☕ CƠ BẢN VỀ JAVA: KIỂU DỮ LIỆU, BIẾN, TOÁN TỬ & RẼ NHÁNH

> 📌 Nguồn tài liệu: Lộ trình phát triển tư duy lập trình viên 28Tech.
> 🎯 Mục tiêu: Làm chủ cú pháp căn bản, kiểm soát bộ nhớ RAM và phòng chống 
  các bẫy logic/tràn số khi chấm bài tự động trên hệ thống (OJ).

---

## 📂 1. Hệ Thống Kiểu Dữ Liệu & Biến (Data Types & Variables)

### a. Bảng tra cứu kích thước bộ nhớ
Java là ngôn ngữ lập trình định kiểu nghiêm ngặt. Cần ghi nhớ kích thước 
của từng kiểu dữ liệu nguyên thủy để tối ưu hóa thuật toán:

+--------------+-----------+----------------------------------------------------+
| Kiểu dữ liệu | Kích thước| Phạm vi giá trị & Đặc tính cốt lõi (28Tech)        |
+--------------+-----------+----------------------------------------------------+
| byte         | 1 byte    | Từ -128 đến 127                                    |
| short        | 2 byte    | Từ -32,768 đến 32,767                              |
| int          | 4 byte    | Từ -2^31 đến 2^31-1 (~2 tỷ). Kiểu số nguyên gốc.  |
| long         | 8 byte    | Từ -2^63 đến 2^63-1. Số cực lớn, cần hậu tố L.    |
| float        | 4 byte    | Số thực thập phân, chính xác 6-7 chữ số (Đuôi F).   |
| double       | 8 byte    | Số thực thập phân, chính xác 15 chữ số (Mặc định). |
| char         | 2 byte    | Lưu các kí tự đơn, bọc trong dấu nháy đơn ' '.     |
| boolean      | 1 byte    | Chỉ nhận một trong hai giá trị logic: true/false.  |
+--------------+-----------+----------------------------------------------------+

### b. Quy tắc đặt tên biến & Name Convention
- KHÔNG bắt đầu bằng chữ số (Ví dụ sai: 1dientich, 2chuvi).
- KHÔNG chứa dấu cách và ký tự đặc biệt (Ví dụ sai: ban kinh, dien#tich).
- KHÔNG trùng tên từ khóa của hệ thống (Ví dụ: int, main, for, while...).
- CÓ phân biệt chữ hoa và chữ thường (Ví dụ: banKinh và BanKinh là khác nhau).
- CAMELCASE: Viết thường từ đầu tiên, các từ tiếp theo viết hoa chữ cái đầu 
  (Ví dụ chuẩn: banKinh, dienTich, luongNhanVien).

### c. Chú thích (Comment) trong mã nguồn
- // Chú thích dòng đơn: Dùng để giải thích nhanh một dòng lệnh.
- /* Chú thích nhiều dòng */: Dùng để giải thích một cụm thuật toán dài.
* Lưu ý: Chú thích sẽ tự động được loại bỏ hoàn toàn khi chương trình thực thi.

---

## 📥 2. Kỹ Thuật Nhập Xuất Dữ Liệu (Scanner & Print)

Cú pháp mã nguồn mẫu:
--------------------------------------------------------------------------------
import java.util.Scanner; // Bắt buộc import lớp này ở đầu file

public class Main {
    public static void main(String[] args) {
        // Khởi tạo đối tượng nhập dữ liệu từ bàn phím
        Scanner sc = new Scanner(System.in); 
        
        // Cú pháp đọc dữ liệu theo từng kiểu tương ứng
        int n = sc.nextInt();             
        long m = sc.nextLong();           
        float f = sc.nextFloat();         
        double d = sc.nextDouble();       
        char c = sc.nextLine().charAt(0); // Đọc ký tự đầu của dòng
        
        // CHÚ Ý: Nhập sai kiểu dữ liệu sẽ quăng lỗi InputMismatchException.
        // Ví dụ: Đang dùng nextInt() nhưng nhập chữ hoặc số thực.
    }
}
--------------------------------------------------------------------------------

🌐 Định dạng hiển thị số thực với độ chính xác cho trước:
Để kiểm soát số lượng chữ số thập phân hiển thị, ta sử dụng hàm System.out.printf():
-> System.out.printf("%.2f\n", chuVi);     // Output thực tế: 3.18
-> System.out.printf("%.10f\n", dienTich); // Output thực tế: 39.9129391239

---

## ⚡ 3. Hệ Thống Toán Tử & Các "Bẫy" Thuật Toán

### a. Danh sách toán tử toán học cốt lõi
- +, -, *: Cộng, trừ, nhân.
- /: Chia lấy phần nguyên (Nếu cả 2 toán hạng là số nguyên).
- %: Chia lấy phần dư.

### 🚨 Bẫy 1: Chia mất phần thập phân (Integer Division)
- Nguyên nhân: Chia 2 số nguyên cho nhau, Java tự động cắt bỏ phần thập phân.
- Cách xử lý đúng: Ép kiểu một toán hạng sang kiểu float hoặc double.
--------------------------------------------------------------------------------
int a = 300, b = 200;
// Cách xử lý sai: int c = a / b; -> Trả về kết quả = 1
// Cách xử lý đúng:
float d = (float) a / b; // Trả về kết quả chính xác = 1.50
--------------------------------------------------------------------------------

### 🚨 Bẫy 2: Tràn số khi nhân hai số nguyên (Integer Overflow)
- Nguyên nhân: Tích của 2 số kiểu int vượt quá giới hạn sẽ bị sai dữ liệu rác, 
  ngay cả khi dùng biến long để lưu kết quả.
- Giải pháp: Phải can thiệp ép kiểu dữ liệu ngay trong quá trình tính toán.
--------------------------------------------------------------------------------
int a = 1000000, b = 1000000;
// Cách xử lý sai: long c = a * b; -> Kết quả lỗi: -727379968

// Cách xử lý đúng 1: Ép kiểu một trong hai biến sang long
long d = (long) a * b; // Kết quả chuẩn: 1000000000000

// Cách xử lý đúng 2: Nhân trực tiếp với hằng số kiểu long 1L ở đầu
long e = 1L * a * b;   // Kết quả chuẩn: 1000000000000
--------------------------------------------------------------------------------

### b. Các toán tử logic & So sánh nâng cao
- Toán tử so sánh: >, >=, <, <=, != (Khác), == (Bằng).
- Toán tử logic: && (AND - Cả 2 đúng), || (OR - Ít nhất 1 đúng), ! (NOT - Phủ định).
- Toán tử tăng giảm: ++a / --a (Tính sau khi tăng), a++ / a-- (Tăng sau khi tính).
- Toán tử ba ngôi: [Biến] = [Biểu thức] ? [Giá trị khi Đúng] : [Giá trị khi Sai];

---

## 🔤 4. Bản Chất Ký Tự & Bảng Mã ASCII

Kiểu dữ liệu char được lưu trữ dưới dạng mã số nguyên trong bảng mã ASCII gồm 256 ký tự. 
Ký tự hoàn toàn có thể tham gia vào các phép tính cộng, trừ, nhân, chia. Khi tính toán, 
hệ thống sẽ dùng mã số ASCII của nó.

Dải mã ASCII cốt lõi bắt buộc phải thuộc lòng:
+ Ký tự chữ cái IN HOA ('A' - 'Z') : Từ mã số 65 đến 90.
+ Ký tự chữ cái in thường ('a' - 'z') : Từ mã số 97 đến 122.
+ Ký tự chữ số từ ('0' - '9')         : Từ mã số 48 đến 57.

🔥 Các đoạn code mẫu kiểm tra và xử lý biến đổi ký tự gốc (Bản chất):
--------------------------------------------------------------------------------
char c = 'a';

// 1. Kiểm tra tính chất ký tự bằng khoảng ký tự hoặc mã số nguyên
boolean isLower = (c >= 'a' && c <= 'z'); // Kí tự in thường
boolean isUpper = (c >= 'A' && c <= 'Z'); // Kí tự in hoa
boolean isDigit = (c >= '0' && c <= '9'); // Kí tự là chữ số

// 2. Chuyển đổi ký tự (Dựa trên khoảng cách 32 đơn vị trong bảng mã ASCII)
char upCase = (char) (c - 32);  // Biến chữ thường thành chữ IN HOA tương ứng
char lowCase = (char) (c + 32); // Biến chữ hoa thành chữ in thường tương ứng
--------------------------------------------------------------------------------

---

## 🔀 5. Các Cấu Trúc Điều Khiển Rẽ Nhánh (Control Structures)

### a. Khối lệnh if - else if - else
Cơ chế vận hành: Hệ thống kiểm tra tuần tự các điều kiện từ trên xuống. Ngay khi phát 
hiện ra một điều kiện đúng, khối lệnh nhánh đó sẽ thực thi và kết thúc cấu trúc ngay. 
Các điều kiện còn lại ở phía dưới sẽ bị bỏ qua hoàn toàn.

### b. Cấu trúc switch - case và từ khóa break
Dùng để so sánh giá trị bằng cụ thể của một biến (số, ký tự, hoặc chuỗi văn bản):
--------------------------------------------------------------------------------
switch (val) {
    case 1:
        // Đoạn mã thực thi khi val == 1
        break; // Ép chương trình thoát khỏi khối switch
    case 2:
        // Đoạn mã thực thi khi val == 2
        break; 
    default:
        // Đoạn mã thực thi khi val không trùng khớp với các case trên
}

// 🚨 LƯU Ý CHÍ MẠNG: Nếu thiếu câu lệnh "break;", chương trình sẽ bị hiện tượng
// "lọt rãnh" (Fall-through) - tự động chạy tiếp xuống các case bên dưới mà không 
// kiểm tra lại điều kiện.
--------------------------------------------------------------------------------
