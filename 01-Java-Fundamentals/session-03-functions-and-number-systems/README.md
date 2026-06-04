<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=Java%20Functions%20And%20Number%20Systems&fontSize=50&fontColor=ffffff" alt="Header Banner">

  <h1>⚙️ Tổng Hợp Kiến Thức Hàm & Hệ Đếm</h1>
  <p><i>Tài liệu tóm tắt về cách xây dựng Hàm (Functions) và kiến thức cốt lõi về Các hệ đếm trong máy tính.</i></p>
  
  <p>
    <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java Badge" />
    <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown Badge" />
    <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status Badge" />
  </p>
</div>

---

## 📖 Giới thiệu
Kho lưu trữ này ghi chép chi tiết về cách xây dựng và tái sử dụng Hàm trong Java, kết hợp với nền tảng toán học về các hệ đếm (Nhị phân, Thập lục phân) bắt buộc phải có đối với mọi lập trình viên.

Nguồn tham khảo chính: **28TECH**.

## 📑 Mục lục
1. [Khái niệm và Cú pháp Hàm](#1-khái-niệm-và-cú-pháp-hàm)
2. [Tham số và Giá trị trả về](#2-tham-số-và-giá-trị-trả-về)
3. [Nạp chồng hàm (Function Overloading)](#3-nạp-chồng-hàm-function-overloading)
4. [Các Hàm toán học phổ biến (Math Class)](#4-các-hàm-toán-học-phổ-biến-math-class)
5. [Các Hệ đếm phổ biến trong máy tính](#5-các-hệ-đếm-phổ-biến-trong-máy-tính)

---

## 🚀 Nội dung chi tiết

### 1. Khái niệm và Cú pháp Hàm
* **Định nghĩa:** Phần lớn các chương trình được xây dựng để giải quyết bài toán lớn. Hàm (Function) được sử dụng để chia nhỏ chương trình thành các thủ tục nhỏ, giải quyết từng chức năng cụ thể.
* **Lợi ích:** Code trở nên mạch lạc, dễ đọc; tái sử dụng lại code; dễ dàng debug (sửa lỗi) và bảo trì.

**Cú pháp khai báo Hàm:**
```java
public static returnType functionName(parameter1, parameter2, ...) {
    // Khối lệnh bên trong hàm (Function body)
}

```

* `returnType`: Kiểu dữ liệu trả về (`void`, `int`, `boolean`, `double`...).
* `functionName`: Tên hàm (Nên đặt theo quy tắc CamelCase).
* `parameter`: Các tham số truyền vào hàm.

**Ví dụ định nghĩa và gọi hàm:**

```java
public class Main {
    // Định nghĩa hàm không có kiểu trả về (void) và không có tham số
    public static void xinChao() {
        System.out.println("Hello 28Tech!");
    }

    public static void main(String[] args) {
        System.out.println("Trước khi gọi hàm");
        xinChao(); // Function call (Gọi hàm)
        System.out.println("Sau khi gọi hàm");
    }
}

```

---

### 2. Tham số và Giá trị trả về

* **Tham số (Parameter):** Là những giá trị được truyền từ bên ngoài vào cho hàm khi hàm được gọi để tính toán.
* **Kiểu trả về (Return Type):** * `void`: Hàm thực hiện xong nhiệm vụ và không cần trả về giá trị nào.
* `int`, `long`, `float`, `double`: Hàm cần trả về một giá trị tính toán bằng từ khóa `return`.
* `boolean`: Hàm trả về kết quả logic đúng (`true`) hoặc sai (`false`).



```java
public class Main {
    // Hàm có tham số và có giá trị trả về là kiểu int
    public static int tinhTong(int a, int b) {
        int sum = a + b;
        return sum; // Trả giá trị ra ngoài
    }

    public static void main(String[] args) {
        int ketQua = tinhTong(10, 20); // Đối số truyền vào là 10 và 20
        System.out.println("Tổng là: " + ketQua); // Output: 30
    }
}

```

---

### 3. Nạp chồng hàm (Function Overloading)

Nạp chồng hàm là một tính năng cực kỳ mạnh mẽ trong Java. Bạn có thể tạo ra **nhiều hàm có cùng một tên**, nhưng phải **khác nhau về số lượng tham số hoặc kiểu dữ liệu của tham số**.

Khi gọi hàm, trình biên dịch của Java sẽ tự động phân tích đối số truyền vào và chọn đúng hàm phù hợp nhất để thực thi.

```java
public class Main {
    // Hàm tìm max cho số nguyên
    public static int findMax(int a, int b) {
        return (a > b) ? a : b;
    }

    // Hàm tìm max cùng tên, nhưng dành cho số thực
    public static float findMax(float a, float b) {
        return (a > b) ? a : b;
    }

    public static void main(String[] args) {
        System.out.println(findMax(10, 20));       // Tự động gọi hàm trả về int (Output: 20)
        System.out.println(findMax(10.2f, 30.4f)); // Tự động gọi hàm trả về float (Output: 30.4)
    }
}

```

---

### 4. Các Hàm toán học phổ biến (Math Class)

Java cung cấp sẵn thư viện `Math` chứa các hàm toán học thiết yếu:

| Tên Hàm | Chức năng | Ví dụ minh họa |
| --- | --- | --- |
| `Math.max(a, b)` | Tìm giá trị lớn nhất | `Math.max(10, 20)` $\rightarrow$ `20` |
| `Math.min(a, b)` | Tìm giá trị nhỏ nhất | `Math.min(10, 20)` $\rightarrow$ `10` |
| `Math.sqrt(n)` | Căn bậc 2 (Trả về `double`) | `Math.sqrt(100)` $\rightarrow$ `10.0` |
| `Math.pow(x, y)` | Tính $x^y$ (Trả về `double`) | `Math.pow(2, 10)` $\rightarrow$ `1024.0` |
| `Math.ceil(n)` | Làm tròn lên số nguyên gần nhất | `Math.ceil(20.3)` $\rightarrow$ `21.0` |
| `Math.floor(n)` | Làm tròn xuống số nguyên gần nhất | `Math.floor(20.8)` $\rightarrow$ `20.0` |
| `Math.round(n)` | Làm tròn chuẩn toán học (quá bán) | `Math.round(20.8)` $\rightarrow$ `21` |
| `Math.abs(n)` | Trị tuyệt đối | `Math.abs(-100)` $\rightarrow$ `100` |

---

### 5. Các Hệ đếm phổ biến trong máy tính

Việc nắm vững các hệ đếm là kỹ năng bắt buộc để thao tác xử lý bit, byte và làm chủ bộ nhớ trong lập trình.

#### a. Hệ Nhị Phân (Binary - Cơ số 2)

* Là ngôn ngữ gốc của máy tính. Chỉ sử dụng 2 giá trị là `0` và `1`. Với $K$ bit, ta có thể biểu diễn được $2^K$ giá trị khác nhau.
* **Cách chuyển từ Hệ 10 sang Hệ 2:** Lấy số đó chia liên tục cho 2, ghi lại số dư. Khi thương bằng 0, viết ngược các số dư từ dưới lên.
* *Ví dụ N = 37:* * 37 / 2 = 18 dư **1**
* 18 / 2 = 9 dư **0**
* 9 / 2 = 4 dư **1**
* 4 / 2 = 2 dư **0**
* 2 / 2 = 1 dư **0**
* 1 / 2 = 0 dư **1**
* $\rightarrow$ Kết quả viết ngược lại: **100101**





#### b. Hệ Thập Lục Phân (Hexadecimal - Cơ số 16)

* Được sử dụng phổ biến thứ 2 sau nhị phân (hay dùng để biểu diễn địa chỉ RAM, mã màu).
* Sử dụng 16 ký tự: `0` đến `9` và `A` đến `F` (A=10, B=11, C=12, D=13, E=14, F=15).
* Thường có tiền tố `0x` ở đầu để nhận diện.
* **Cách chuyển từ Hệ 10 sang Hệ 16:** Lấy số đó chia liên tục cho 16. Lấy số dư viết ngược lại (nhớ đổi các dư từ 10-15 sang A-F).
* *Ví dụ N = 762:*
* 762 / 16 = 47 dư **10** (Tương ứng là **A**)
* 47 / 16 = 2 dư **15** (Tương ứng là **F**)
* 2 / 16 = 0 dư **2** * $\rightarrow$ Kết quả viết ngược lại: **2FA**





#### c. Hệ Bát Phân (Octal - Cơ số 8)

* Sử dụng 8 chữ số từ `0` đến `7`. Thuật toán chuyển đổi áp dụng tương tự như việc chia liên tục cho 8 và lấy phần dư.

---

## 🛠️ Công cụ sử dụng

* **IDE tham khảo:** IntelliJ IDEA / Eclipse / VS Code
* **Môi trường:** Java Development Kit (JDK) 11+
* **Định dạng:** Markdown (`.md`)
