# CƠ BẢN VỀ JAVA: KIỂU DỮ LIỆU, BIẾN, TOÁN TỬ & RẼ NHÁNH

> Nguồn tài liệu: Lộ trình tư duy lập trình viên 28Tech.
> Mục tiêu: Tra cứu nhanh lý thuyết cốt lõi và các bẫy OJ.

---

## 1. Hệ Thống Kiểu Dữ Liệu & Biến (Data Types & Variables)

### a. Danh sách kích thước bộ nhớ
Java định kiểu nghiêm ngặt, cần nhớ rõ kích thước của từng kiểu dữ liệu:

- byte    (1 byte) : Từ -128 đến 127
- short   (2 byte) : Từ -32,768 đến 32,767
- int     (4 byte) : Từ -2^31 đến 2^31-1 (~2 tỷ). Kiểu mặc định.
- long    (8 byte) : Từ -2^63 đến 2^63-1. Số lớn, cần đuôi L.
- float   (4 byte) : Số thực, chính xác 6-7 chữ số (Cần đuôi F).
- double  (8 byte) : Số thực, chính xác 15 chữ số (Kiểu mặc định).
- char    (2 byte) : Lưu 1 kí tự đơn, bọc trong dấu nháy đơn ' '.
- boolean (1 byte) : Chỉ nhận giá trị logic true hoặc false.

### b. Quy tắc đặt tên biến & Name Convention
- KHÔNG bắt đầu bằng chữ số (Ví dụ sai: 1dientich, 2chuvi).
- KHÔNG chứa dấu cách và ký tự đặc biệt (Ví dụ sai: ban kinh, dien#tich).
- KHÔNG trùng tên từ khóa hệ thống (Ví dụ: int, main, for, while...).
- CÓ phân biệt chữ hoa và chữ thường (banKinh và BanKinh là khác nhau).
- CAMELCASE: Viết thường từ đầu tiên, các từ tiếp theo viết hoa chữ cái đầu 
  (Ví dụ chuẩn: banKinh, dienTich, luongNhanVien).

### c. Chú thích (Comment) trong mã nguồn
- // Chú thích dòng đơn: Giải thích nhanh một dòng lệnh.
- /* Chú thích nhiều dòng */: Giải thích một cụm thuật toán dài.

---

## 2. Kỹ Thuật Nhập Xuất Dữ Liệu (Scanner & Print)

Cú pháp mã nguồn mẫu:
--------------------------------------------------------------------------------
import java.util.Scanner; // Khai báo lớp này ở đầu file

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in); 
        
        int n = sc.nextInt();             
        long m = sc.nextLong();           
        float f = sc.nextFloat();         
        double d = sc.nextDouble();       
        char c = sc.nextLine().charAt(0);
        
        // CHÚ Ý: Nhập sai kiểu dữ liệu sẽ quăng lỗi InputMismatchException.
        // Ví dụ: Đang dùng nextInt() nhưng nhập chữ hoặc số thực.
    }
}
--------------------------------------------------------------------------------

🌐 Định dạng hiển thị số thực với độ chính xác cho trước:
Sử dụng System.out.printf() để ép số chữ số phần thập phân:
-> System.out.printf("%.2f\n", chuVi);     // Lấy 2 chữ số thập phân
-> System.out.printf("%.10f\n", dienTich); // Lấy 10 chữ số thập phân

---

## 3. Hệ Thống Toán Tử & Các "Bẫy" Thuật Toán

### a. Danh sách toán tử toán học cốt lõi
- +, -, *: Cộng, trừ, nhân.
- /: Chia lấy phần nguyên (Nếu cả 2 toán hạng là số nguyên).
- %: Chia lấy phần dư.

### 🚨 Bẫy 1: Chia mất phần thập phân (Integer Division)
- Nguyên nhân: Chia 2 số nguyên cho nhau, Java tự động cắt bỏ phần thập phân.
- Giải pháp: Ép kiểu một toán hạng sang kiểu float hoặc double.
--------------------------------------------------------------------------------
int a = 300, b = 200;
// Xử lý sai: int c = a / b; -> Kết quả thương = 1 (Mất .5)
// Xử lý đúng:
float d = (float) a / b; // Kết quả chính xác = 1.50
--------------------------------------------------------------------------------

### 🚨 Bẫy 2: Tràn số khi nhân hai số nguyên (Integer Overflow)
- Nguyên nhân: Tích 2 số int lớn vượt quá 2 tỷ sẽ bị lỗi dữ liệu rác, 
  ngay cả khi dùng biến long để lưu kết quả.
- Giải pháp: Can thiệp ép kiểu dữ liệu ngay trong phép tính.
--------------------------------------------------------------------------------
int a = 1000000, b = 1000000;
// Xử lý sai: long c = a * b; -> Kết quả lỗi: -727379968

// Xử lý đúng 1: Ép kiểu một biến sang long: long d = (long) a * b;
// Xử lý đúng 2: Nhân với hằng số long 1L:   long e = 1L * a * b;
--------------------------------------------------------------------------------

### b. Các toán tử logic & So sánh nâng cao
- Toán tử so sánh: >, >=, <, <=, != (Khác), == (Bằng).
- Toán tử logic: && (AND - Cả 2 đúng), || (OR - Ít nhất 1 đúng), ! (NOT).
- Toán tử tăng giảm: ++a / --a (Tính sau khi tăng), a++ / a-- (Tăng sau khi tính).
- Toán tử ba ngôi: [Biến] = [Biểu thức] ? [Giá trị Đúng] : [Giá trị Sai];

---

## 4. Bản Chất Ký Tự & Bảng Mã ASCII

Kiểu dữ liệu char được lưu bằng mã số nguyên trong bảng mã ASCII (256 ký tự). 
Khi tính toán, hệ thống sẽ tự động dùng mã số ASCII của ký tự đó.

Dải mã ASCII cốt lõi bắt buộc phải thuộc lòng:
+ Ký tự chữ cái IN HOA ('A' - 'Z') : Từ mã số 65 đến 90.
+ Ký tự chữ cái in thường ('a' - 'z') : Từ mã số 97 đến 122.
+ Ký tự chữ số từ ('0' - '9')         : Từ mã số 48 đến 57.

🔥 Đoạn code mẫu kiểm tra và biến đổi ký tự:
--------------------------------------------------------------------------------
char c = 'a';

boolean isLower = (c >= 'a' && c <= 'z'); // Kiểm tra kí tự in thường
boolean isUpper = (c >= 'A' && c <= 'Z'); // Kiểm tra kí tự in hoa
boolean isDigit = (c >= '0' && c <= '9'); // Kiểm tra kí tự là chữ số

char upCase = (char) (c - 32);  // Biến chữ thường thành chữ IN HOA tương ứng
char lowCase = (char) (c + 32); // Biến chữ hoa thành chữ in thường tương ứng
--------------------------------------------------------------------------------

---

## 5. Các Cấu Trúc Điều Khiển Rẽ Nhánh (Control Structures)

### a. Khối lệnh if - else if - else
Cơ chế vận hành: Hệ thống kiểm tra tuần tự các điều kiện từ trên xuống. Ngay khi 
có một điều kiện đúng, khối lệnh nhánh đó sẽ chạy và kết thúc cấu trúc ngay. 
Các điều kiện còn lại ở phía dưới sẽ bị bỏ qua hoàn toàn.

### b. Cấu trúc switch - case và từ khóa break
Dùng để so sánh giá trị bằng cụ thể của một biến:
--------------------------------------------------------------------------------
switch (val) {
    case 1:
        // Đoạn mã thực thi khi val == 1
        break; // Ép chương trình thoát khỏi khối switch
    case 2:
        // Đoạn mã thực thi khi val == 2
        break; 
    default:
        // Đoạn mã thực thi khi không trùng khớp với các case trên
}

// LƯU Ý CHÍ MẠNG: Nếu thiếu câu lệnh "break;", chương trình sẽ bị hiện tượng
// "lọt rãnh" (Fall-through) - tự động chạy tiếp xuống các case bên dưới mà không 
// kiểm tra lại điều kiện.
--------------------------------------------------------------------------------
