<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=Java%20Loops%20Notes&fontSize=60&fontColor=ffffff" alt="Header Banner">

  <h1>🔁 Tổng Hợp Kiến Thức Vòng Lặp Java</h1>
  <p><i>Tài liệu tóm tắt súc tích, dễ hiểu dành cho quá trình làm chủ các cấu trúc lặp trong Java.</i></p>
</div>

---

## 📖 Giới thiệu
Kho lưu trữ này chứa các ghi chép chi tiết về cấu trúc vòng lặp (Loops) trong ngôn ngữ lập trình Java.

Nguồn tham khảo chính: **28TECH**.

## 📑 Mục lục
1. [Bản chất của Vòng lặp](#1-bản-chất-của-vòng-lặp)
2. [Vòng lặp For](#2-vòng-lặp-for)
3. [Câu lệnh điều khiển Break và Continue](#3-câu-lệnh-điều-khiển-break-và-continue)
4. [Vòng lặp While](#4-vòng-lặp-while)
5. [Vòng lặp Do-While](#5-vòng-lặp-do-while)

---

## 🚀 Nội dung chi tiết

### 1. Bản chất của Vòng lặp
* **Bài toán đặt ra:** Hãy viết chương trình in ra 1000 dòng "Hello World!". Nếu gõ thủ công 1000 lệnh hiển thị sẽ khiến mã nguồn cực kỳ dài, rối và tối nghĩa.
* **Giải pháp:** Vòng lặp (Loop) ra đời giúp lặp đi lặp lại một hoặc một nhóm câu lệnh mà không cần phải viết lại code nhiều lần.

---

### 2. Vòng lặp For

**a. Khái niệm & Ứng dụng**
* Vòng lặp for được sử dụng phổ biến nhất trong lập trình.
* Thường được ưu tiên áp dụng khi chúng ta đã xác định hoặc biết trước số vòng lặp cần thực hiện.

**b. Cú pháp**
Vòng lặp for gồm 3 phần chính nằm trong cặp ngoặc tròn, phân tách nhau bắt buộc bằng hai dấu chấm phẩy `;`:

```java
for ([Câu lệnh khởi tạo]; [Điều kiện lặp]; [Câu lệnh cập nhật]) {
     // Khối lệnh bên trong vòng lặp for
}

```

* **Ý nghĩa các thành phần:**
* **Câu lệnh khởi tạo:** Khai báo và khởi tạo một biến đóng vai trò làm biến đếm cho vòng lặp (thường là i, j, k).
* **Điều kiện lặp:** Biểu thức logic. Chừng nào điều kiện lặp còn đúng (true), vòng lặp còn tiếp tục chạy.
* **Câu lệnh cập nhật:** Thay đổi giá trị của biến đếm ngay sau khi các câu lệnh bên trong thân for thực thi xong một lượt.



**c. Ví dụ mã nguồn mẫu**

```java
// Ví dụ 1: In tuần tự các số tự nhiên từ 1 đến 1000
for (int i = 1; i <= 1000; i++) {
    System.out.print(i + " ");
}

```

```java
// Ví dụ 2: Nhảy bước (In ra các số lẻ từ 1 đến 10)
for (int i = 1; i <= 10; i += 2) {
    System.out.print(i + " "); // Output: 1 3 5 7 9
}

```

> ⚠️ **CHÚ Ý (Vòng lặp vô hạn):** Nếu khuyết điều kiện lặp hoặc biến đếm không được cập nhật đúng cách, vòng lặp sẽ chạy vĩnh viễn gây treo chương trình.
> *Ví dụ:* `for (int i = 1; ; i++) { ... }` sẽ in ra vô hạn các số bắt đầu từ 1.

---

### 3. Câu lệnh điều khiển Break và Continue

Để kiểm soát luồng chạy của vòng lặp linh hoạt theo từng điều kiện thuật toán, Java cung cấp hai câu lệnh điều khiển:

* **Câu lệnh break:** Khi gặp từ khóa này, vòng lặp chứa nó sẽ lập tức kết thúc và thoát hẳn ra ngoài ngay mà không cần đợi điều kiện lặp chuyển sang sai. Thông thường `break` đi kèm với `if` để dừng sớm vòng lặp.

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // Thoát hẳn vòng lặp ngay khi i bằng 5
    }
    System.out.print(i + " "); // Output: 1 2 3 4
}

```

* **Câu lệnh continue:** Khi gặp từ khóa này, vòng lặp sẽ bỏ qua toàn bộ các câu lệnh còn lại nằm phía dưới nó trong lượt lặp hiện tại, để lập tức nhảy sang một lượt lặp mới (thực hiện phần cập nhật biến đếm đối với vòng `for`).

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue; // Bỏ qua lệnh in khi i = 3 để nhảy sang lượt i = 4
    }
    System.out.print(i + " "); // Output: 1 2 4 5 (Không in số 3)
}

```

---

### 4. Vòng lặp While

**a. Cấu trúc và Hoạt động**

* Vòng lặp `while` được sử dụng khi chưa xác định được số vòng lặp cụ thể cần thực hiện.
* Hệ thống sẽ kiểm tra điều kiện trước. Chừng nào điều kiện lặp còn đúng (true) thì khối lệnh bên trong thân `while` còn tiếp tục thực thi.

```java
while ([Điều kiện lặp]) {
     // Các câu lệnh của vòng lặp
}

```

> ⚠️ **CHÚ Ý:** Lỗi rất thường gặp khi sử dụng while là quên cập nhật biến điều kiện trong thân vòng lặp, dẫn đến việc chương trình bị lặp vĩnh viễn.

**b. Ứng dụng thuật toán kinh điển: Tách và Xử lý chữ số**
Đây là kỹ thuật nền tảng cực kỳ quan trọng dùng để giải quyết các bài toán phân tích cấu trúc của một số nguyên trên hệ thống OJ:

```java
// Thuật toán 1: Tách và in ra từng chữ số từ phải qua trái (hàng đơn vị trước)
int n = 1234;
while (n != 0) {
    System.out.println(n % 10); // Lấy chữ số hàng đơn vị (In ra: 4, 3, 2, 1)
    n /= 10;                     // Chia cho 10 để loại bỏ chữ số vừa in
}

```

```java
// Thuật toán 2: Tính tổng các chữ số của một số nguyên
int num = 1234;
int sum = 0;
while (num != 0) {
    sum += num % 10; // Cộng dồn chữ số hàng đơn vị vào tổng
    num /= 10;       // Loại bỏ chữ số hàng đơn vị
}
System.out.println("Tổng các chữ số: " + sum); // Output: 10

```

---

### 5. Vòng lặp Do-While

**a. Bản chất và Điểm khác biệt chí mạng**

* Vòng lặp do-while hoạt động tương tự như vòng while nhưng có một điểm khác biệt cực lớn: Nó luôn luôn thực thi khối lệnh bên trong ít nhất 1 lần đầu tiên, sau đó mới tiến hành kiểm tra điều kiện lặp.
* Thường dùng khi chưa xác định số vòng lặp nhưng bắt buộc hệ thống phải chạy mẫu trước một lượt.

```java
do {
     // Khối câu lệnh bên trong vòng lặp do-while
} while ([Điều kiện lặp]); // 🚨 BẮT BUỘC phải có dấu chấm phẩy ';' ở cuối

```

**b. Ví dụ minh họa**

```java
int i = 100;

// Dù điều kiện i < 100 bị SAI ngay từ đầu, khối lệnh vẫn chạy được 1 lần
do {
    System.out.println("Giá trị i: " + i); // Vẫn in ra: 100
} while (i < 100);

```

> ⚠️ **LỖI CÚ PHÁP PHỔ BIẾN:** Thiếu dấu chấm phẩy `;` đằng sau từ khóa đóng ngoặc của `while([Điều kiện lặp]);` làm chương trình báo lỗi biên dịch.

---

## 🛠️ Công cụ sử dụng

* **IDE tham khảo:** IntelliJ IDEA / Eclipse / VS Code
* **Môi trường:** Java Development Kit (JDK) 11+
* **Định dạng:** Markdown (.md)
