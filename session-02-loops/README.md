# 🔁 SỔ TAY TRA CỨU BUỔI 3: CẤU TRÚC VÒNG LẶP (LOOPS)

---

## 1. Bản Chất Của Vòng Lặp
- Bài toán đặt ra: Cần in ra 1000 dòng chữ "Hello World!". Nếu gõ thủ công 
  1000 lệnh printf sẽ làm code cực kỳ dài và tối nghĩa.
- Giải pháp: Sử dụng vòng lặp (Loop) để tái sử dụng một khối lệnh với số lần 
  nhất định hoặc chừng nào điều kiện logic còn thỏa mãn.

---

## 2. Vòng Lặp For

### a. Cú pháp cơ bản
for ([Câu lệnh khởi tạo]; [Điều kiện lặp]; [Câu lệnh cập nhật]) {
    // Khối lệnh được thực thi khi điều kiện lặp trả về giá trị true
}

### b. Thành phần cấu tạo (Gồm 3 phần chính cách nhau bằng dấu ';')
- Câu lệnh khởi tạo: Khai báo và khởi tạo biến đếm (thường là i, j, k).
- Điều kiện lặp: Kiểm tra trước mỗi vòng lặp. Nếu đúng (true) thì chạy tiếp, 
  nếu sai (false) vòng lặp kết thúc ngay lập tức.
- Câu lệnh cập nhật: Thay đổi giá trị biến đếm ngay sau khi khối lệnh 
  bên trong vòng for thực hiện xong một lượt.

### c. Tư duy ứng dụng vòng For
- Được sử dụng nhiều nhất trong lập trình thực tế.
- Thường được ưu tiên áp dụng khi đã XÁC ĐỊNH TRƯỚC SỐ VÒNG LẶP cần thực hiện.

### d. Đoạn mã thực hành mẫu vòng For
// Ví dụ 1: In ra các số từ 1 đến 1000 tuần tự
for (int i = 1; i <= 1000; i++) {
    System.out.print(i + " ");
}

// Ví dụ 2: Vòng lặp nhảy bước (In ra các số lẻ từ 1 đến 10)
for (int i = 1; i <= 10; i += 2) {
    System.out.print(i + " "); // Output: 1 3 5 7 9
}

// 🚨 BẪY LỖI CHÍ MẠNG: Vòng lặp vô hạn (Infinite Loop)
// Nếu khuyết điều kiện dừng, vòng lặp sẽ chạy vĩnh viễn làm treo hệ thống
for (int i = 1; ; i++) { 
    System.out.println(i); // Vòng lặp in ra vô hạn các số tự nhiên
}

---

## 3. Câu Lệnh Điều Khiển Vòng Lặp: Break & Continue

### a. Câu lệnh Break
- Ý nghĩa: Dùng để cưỡng ép dừng và thoát khỏi vòng lặp ngay lập tức mà không 
  cần đợi điều kiện lặp chuyển sang sai.
- Ứng dụng: Thường đi kèm với câu lệnh cấu trúc rẽ nhánh if để kiểm tra 
  điều kiện dừng đặc biệt của thuật toán.
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // Vòng lặp lập tức kết thúc khi i bằng 5
    }
}

---

## 4. Vòng Lặp While

### a. Cú pháp cơ bản
while ([Điều kiện lặp]) {
    // Khối câu lệnh của vòng lặp
}

### b. Tư duy ứng dụng vòng While
- Được sử dụng khi CHƯA XÁC ĐỊNH ĐƯỢC SỐ VÒNG LẶP cần thực hiện cụ thể.
- Khối lệnh bên trong chỉ được chạy khi điều kiện lặp trả về giá trị true.
- 🚨 BẪY LỖI: Rất dễ bị lặp vĩnh viễn nếu quên câu lệnh cập nhật điều kiện dừng 
  ở bên trong thân vòng lặp while.

### c. Kỹ thuật thuật toán kinh điển sử dụng While: Tách và Xử lý chữ số
Đây là dạng bài tập cực kỳ phổ biến trên hệ thống OJ để phân tích cấu trúc 
của một số nguyên:

// Thuật toán 1: Tách và in từng chữ số hàng đơn vị từ phải qua trái
int n = 1234;
while (n != 0) {
    System.out.println(n % 10); // Lấy chữ số hàng đơn vị (In ra: 4, 3, 2, 1)
    n /= 10;                     // Loại bỏ chữ số hàng đơn vị vừa tách
}

// Thuật toán 2: Tính tổng các chữ số của một số nguyên nguyên bản
int n = 1234;
int sum = 0;
while (n != 0) {
    sum += n % 10; // Cộng dồn chữ số hàng đơn vị vào biến tổng
    n /= 10;       // Làm mất số hàng đơn vị để chuyển sang số tiếp theo
}
System.out.println("Tổng các chữ số: " + sum); // Output: 10 (1+2+3+4)

---

## 5. Vòng Lặp Do - While

### a. Cú pháp cơ bản
do {
    // Khối câu lệnh bên trong vòng lặp
} while ([Điều kiện lặp]); // BẮT BUỘC có dấu chấm phẩy ';' ở cuối

### b. Đặc tính khác biệt chí mạng
- Hoạt động tương tự vòng while nhưng Do-While LUÔN LUÔN THỰC THI KHỐI CODE 
  BÊN TRONG ÍT NHẤT 1 LẦN ĐẦU TIÊN, sau đó mới tiến hành kiểm tra điều kiện lặp.
- Ứng dụng khi chưa xác định được số vòng lặp nhưng yêu cầu hệ thống phải 
  chạy mẫu trước một lượt (Ví dụ: Menu lựa chọn, nhập dữ liệu kiểm thử).

### c. Đoạn mã thực hành mẫu Do-While
// Ví dụ 1: Điều kiện sai ngay từ đầu nhưng vẫn chạy 1 lần
int i = 100;
do {
    System.out.println(i); // Vẫn in ra giá trị 100
} while (i < 100);          // Kiểm tra thấy 100 < 100 là sai -> Thoát lặp.
