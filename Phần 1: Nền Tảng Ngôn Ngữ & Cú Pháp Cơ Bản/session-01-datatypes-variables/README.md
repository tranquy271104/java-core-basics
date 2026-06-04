<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=Java%20Basics%20Notes&fontSize=60&fontColor=ffffff" alt="Header Banner">

  <h1>☕ Tổng Hợp Kiến Thức Cơ Bản Java</h1>
  <p><i>Tài liệu tóm tắt súc tích, dễ hiểu dành cho quá trình chinh phục ngôn ngữ Java.</i></p>
  
  <p>
    <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java Badge" />
    <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown Badge" />
    <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status Badge" />
  </p>
</div>

---

## 📖 Giới thiệu
Kho lưu trữ này chứa các ghi chép chi tiết về nền tảng ngôn ngữ lập trình Java.

Nguồn tham khảo chính: **28TECH**.

## 📑 Mục lục
1. [Kiểu dữ liệu và Biến](#1-kiểu-dữ-liệu-và-biến-data-type--variable)
2. [Chú thích (Comment) trong Java](#2-chú-thích-comment-trong-java)
3. [Khai báo, Nhập và Xuất dữ liệu](#3-khai-báo-nhập-và-xuất-dữ-liệu)
4. [Toán tử (Operators)](#4-toán-tử-operators)
5. [Cấu trúc rẽ nhánh (Conditional Statements)](#5-cấu-trúc-rẽ-nhánh-conditional-statements)
6. [Bảng mã ASCII và Xử lý Kí tự](#6-bảng-mã-ascii-và-xử-lý-kí-tự)

---

## 🚀 Nội dung chi tiết

### 1. Kiểu dữ liệu và Biến (Data Type & Variable)

**a. Kiểu dữ liệu**
Java cung cấp các kiểu dữ liệu nguyên thủy để biểu diễn số nguyên, số thực, kí tự và giá trị đúng/sai:

| Kiểu dữ liệu | Kích thước | Phạm vi giá trị / Ý nghĩa |
| :--- | :--- | :--- |
| `byte` | 1 byte | `-128` đến `127` |
| `short` | 2 byte | `-32768` đến `32767` |
| `int` | 4 byte | `-2^31` đến `2^31 - 1` |
| `long` | 8 byte | `-2^63` đến `2^63 - 1` |
| `float` | 4 byte | Số thực, độ chính xác 6 - 7 chữ số sau dấu phẩy. |
| `double` | 8 byte | Số thực, độ chính xác tới 15 chữ số sau dấu phẩy. |
| `char` | 2 byte | Lưu các kí tự. |
| `boolean` | 1 byte | Lưu giá trị `true` hoặc `false`. |

**b. Biến và Quy tắc đặt tên**
* **Khái niệm:** Biến dùng để lưu trữ giá trị trong bộ nhớ khi chương trình tính toán.
* **Cú pháp:** `[Kiểu dữ liệu] [Tên biến];`
* **Quy tắc bắt buộc:**
    * Không bắt đầu bằng chữ số (Ví dụ sai: `1dientich`).
    * Không chứa khoảng trắng và kí tự đặc biệt (Ví dụ sai: `ban kinh`, `dien#tich`).
    * Không trùng từ khóa (`int`, `for`, `while`,...).
    * Có phân biệt chữ hoa và chữ thường (`banKinh` khác `BanKinh`).
* **Quy chuẩn đặt tên (CamelCase):** Chữ cái đầu tiên của từ đầu viết thường, các từ tiếp theo viết hoa chữ cái đầu (`banKinh`, `dienTich`, `luongNhanVien`).

---

### 2. Chú thích (Comment) trong Java
Chú thích dùng để giải thích code, giúp bảo trì code dễ dàng hơn và sẽ bị bỏ qua khi chương trình thực thi.
* **Trên một dòng:** Dùng `//`
* **Trên nhiều dòng:** Đặt giữa `/*` và `*/`

---

### 3. Khai báo, Nhập và Xuất dữ liệu

**Khai báo và Xuất dữ liệu**
Sử dụng `System.out.println()` để in xuống dòng hoặc `System.out.printf()` để định dạng số thực.

```java
public class Main {
    public static void main(String[] args) {
        int banKinh = 100;
        long dienTich = 10182383812838123L; // Thêm L cho kiểu long
        float PI = 3.14F;                  // Thêm F cho kiểu float
        double temp = 30.89129391293D;
        
        System.out.println("Giá trị diện tích: " + dienTich);
        
        // In định dạng số thực lấy 2 chữ số sau dấu phẩy
        float chuVi = 3.18238f;
        System.out.printf("%.2f\n", chuVi); // Output: 3.18
    }
}

```

**Nhập dữ liệu từ bàn phím**
Sử dụng lớp `Scanner` trong gói `java.util`.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int n = sc.nextInt();
        long m = sc.nextLong();
        float f = sc.nextFloat();
        // Nhập 1 kí tự
        char kiTu = sc.next().charAt(0); 
    }
}

```

> ⚠️ **Chú ý:** Nếu nhập sai kiểu dữ liệu (ví dụ nhập chữ vào `nextInt()`), chương trình sẽ ném ra ngoại lệ `InputMismatchException`.

---

### 4. Toán tử (Operators)

**a. Toán tử toán học & Các lưu ý quan trọng**
Gồm: `+`, `-`, `*`, `/` (chia), `%` (chia dư).

* **Lưu ý 1 (Phép chia nguyên):** Chia 2 số nguyên sẽ trả về số nguyên. Muốn lấy phần thập phân, ít nhất 1 trong 2 số phải là số thực. `float d = (float) 300 / 200; // 1.50`
* **Lưu ý 2 (Tràn số):** Nhân 2 số `int` lớn có thể gây tràn số trước khi gán vào biến `long`. Cần ép kiểu dữ liệu trước khi nhân. `long d = (long) a * b;`
* **Lưu ý 3 (Thứ tự ưu tiên):** Nhân chia trước, cộng trừ sau. Nên dùng dấu ngoặc đơn `()` để kiểm soát biểu thức.

**b. Toán tử so sánh và Logic**

* **So sánh:** `>`, `>=`, `<`, `<=`, `!=` (khác), `==` (bằng). Trả về `true`/`false`.
* **Logic:** * `&&` (AND): Chỉ đúng khi tất cả các mệnh đề đều đúng.
* `\|\|` (OR): Chỉ sai khi tất cả các mệnh đề đều sai.
* `!` (NOT): Phủ định giá trị logic hiện tại.



**c. Toán tử tăng giảm (`++`, `--`)**

* `++a` / `--a`: Tăng/giảm giá trị của `a` trước rồi mới thực hiện phép tính.
* `a++` / `a--`: Dùng giá trị hiện tại của `a` cho phép tính trước, sau đó mới tăng/giảm `a`.

**d. Toán tử ba ngôi**

* **Cú pháp:** `[Biểu thức so sánh] ? [Giá trị khi đúng] : [Giá trị khi sai];`
* *Ví dụ:* `int x = (10 < 20) ? 10 : 20;` -> `x` sẽ bằng `10`.

---

### 5. Cấu trúc rẽ nhánh (Conditional Statements)

a. Cấu trúc `if`, `if-else`, `else if`
Dùng để điều hướng chương trình dựa trên điều kiện. Khi một nhánh `else if` thỏa mãn, toàn bộ khối cấu trúc sẽ kết thúc.

```java
if (condition1) {
    // Code khi condition1 ĐÚNG
} else if (condition2) {
    // Code khi condition1 SAI và condition2 ĐÚNG
} else {
    // Code khi tất cả đều SAI
}

```

b. Cấu trúc `switch-case`
So sánh giá trị của một biến (`val`) với các trường hợp cố định. Cần có `break` để tránh lọt xuống các case phía dưới.

```java
switch(val) {
    case 1:
        // code
        break;
    case 2:
        // code
        break;
    default:
        // code khi không trùng case nào
}

```

---

### 6. Bảng mã ASCII và Xử lý Kí tự

Mỗi kí tự thuộc kiểu `char` đều có một mã số nguyên tương ứng trong bảng mã ASCII (gồm 256 kí tự). Bản chất kiểu `char` có thể đem đi cộng, trừ, nhân, chia như số nguyên.

**Các dải kí tự quan trọng:**

* `A-Z`: `65 - 90`
* `a-z`: `97 - 122`
* `0-9`: `48 - 57`

**Các câu lệnh kiểm tra và biến đổi cơ bản:**

* **Kiểm tra chữ thường:** `if (c >= 'a' && c <= 'z')`
* **Kiểm tra chữ hoa:** `if (c >= 'A' && c <= 'Z')`
* **Kiểm tra chữ số:** `if (c >= '0' && c <= '9')`
* **Chuyển Thường thành Hoa:** `c -= 32;`
* **Chuyển Hoa thành Thường:** `c += 32;`

---

## 🛠️ Công cụ sử dụng

* **IDE tham khảo:** IntelliJ IDEA / Eclipse / VS Code
* **Môi trường:** Java Development Kit (JDK) 11+
* **Định dạng:** Markdown (`.md`)


