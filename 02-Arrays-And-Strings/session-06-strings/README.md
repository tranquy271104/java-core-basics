<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=Java%20Strings%20Notes&fontSize=60&fontColor=ffffff" alt="Header Banner">

  <h1>🔤 Tổng Hợp Kiến Thức Xử Lý Chuỗi (String)</h1>
  <p><i>Tài liệu tóm tắt súc tích, chuyên sâu về cách thao tác với xâu ký tự, số lớn và StringBuilder trong Java.</i></p>
  
  <p>
    <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java Badge" />
    <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown Badge" />
    <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status Badge" />
  </p>
</div>

---

## 📖 Giới thiệu
Kho lưu trữ này chứa các ghi chép chi tiết về lớp `String` trong Java. Lớp String cung cấp hàng loạt các phương thức mạnh mẽ để xử lý văn bản, tách từ, chuyển đổi kiểu dữ liệu và giải quyết các bài toán về tần suất ký tự.

Nguồn tham khảo chính: **28TECH**.

## 📑 Mục lục
1. [Khái niệm và Hiện tượng trôi lệnh](#1-khái-niệm-và-hiện-tượng-trôi-lệnh-khi-nhập-chuỗi)
2. [Các hàm xử lý chuỗi thông dụng](#2-các-hàm-xử-lý-chuỗi-thông-dụng)
3. [Tách từ trong chuỗi (Split & Tokenizer)](#3-tách-các-từ-trong-chuỗi)
4. [Kiểm tra loại ký tự (Lớp Character)](#4-kiểm-tra-và-chuyển-đổi-loại-ký-tự)
5. [Chuyển đổi kiểu dữ liệu và Lớp BigInteger](#5-chuyển-đổi-kiểu-và-xử-lý-số-lớn-biginteger)
6. [Đếm tần suất ký tự (Array & Map)](#6-đếm-tần-suất-xuất-hiện-của-ký-tự)
7. [Lớp StringBuilder (Tối ưu bộ nhớ)](#7-lớp-stringbuilder-chuỗi-có-thể-thay-đổi)

---

## 🚀 Nội dung chi tiết

### 1. Khái niệm và Hiện tượng trôi lệnh khi nhập chuỗi

String trong Java là một đối tượng **không thể thay đổi (Immutable)**. Mỗi khi bạn dùng hàm thay đổi chuỗi, hệ thống thực chất đang tạo ra một chuỗi hoàn toàn mới.

Để nhập chuỗi có chứa dấu cách từ bàn phím, ta dùng hàm `nextLine()`. Hàm này sẽ đọc toàn bộ dữ liệu cho đến khi gặp phím `Enter` (dấu xuống dòng).

🚨 **Bẫy kinh điển: Hiện tượng trôi lệnh (Buffer Issue)**
Nếu trước lệnh `nextLine()` bạn có sử dụng các lệnh đọc số như `nextInt()`, `nextDouble()...`, phím `Enter` cuối cùng của việc nhập số vẫn còn kẹt lại trong bộ đệm. Lệnh `nextLine()` tiếp theo sẽ ăn ngay dấu `Enter` đó và kết thúc luôn (trả về chuỗi rỗng).

**Cách khắc phục: Xóa bộ đệm bằng một lệnh `nextLine()` thừa.**
```java
Scanner sc = new Scanner(System.in);
int n = sc.nextInt();
sc.nextLine(); // Đọc và loại bỏ phím Enter thừa trong bộ đệm
String s = sc.nextLine(); // Bây giờ mới nhập chuỗi chuẩn xác
System.out.println(s);

```

---

### 2. Các hàm xử lý chuỗi thông dụng

Giả sử ta có chuỗi `String s = "java 28tech";` và `String t = "JAVA 28TECH";`

| Cú pháp hàm | Ý nghĩa & Kết quả |
| --- | --- |
| `s.length()` | Trả về độ dài chuỗi $\rightarrow$ `11` |
| `s.charAt(index)` | Lấy ký tự tại vị trí chỉ số `index` (từ 0 đến length-1) |
| `s.toUpperCase()` | Trả về chuỗi IN HOA $\rightarrow$ `"JAVA 28TECH"` |
| `t.toLowerCase()` | Trả về chuỗi in thường $\rightarrow$ `"java 28tech"` |
| `s.concat(" hi")` | Nối chuỗi (giống phép `+`) $\rightarrow$ `"java 28tech hi"` |
| `s.compareTo(t)` | So sánh phân biệt hoa thường theo từ điển (Trả về `< 0`, `0`, hoặc `> 0`) |
| `s.compareToIgnoreCase(t)` | So sánh KHÔNG phân biệt hoa thường $\rightarrow$ Trả về `0` (bằng nhau) |
| `s.substring(5)` | Cắt chuỗi từ vị trí số 5 đến cuối $\rightarrow$ `"28tech"` |
| `s.contains("28")` | Kiểm tra chuỗi con có tồn tại không $\rightarrow$ `true` |

---

### 3. Tách các từ trong chuỗi

Khi cần tách một câu thành các từ đơn lẻ (bỏ qua các khoảng trắng thừa), ta có 2 cách tối ưu:

**Cách 1: Sử dụng `split("\\s+")` (Regex)**

```java
String s = "java    28tech C++";
String[] arr = s.split("\\s+"); // \s+ đại diện cho một hoặc nhiều dấu cách liên tiếp
for (String x : arr) {
    System.out.println(x);
}

```

**Cách 2: Sử dụng `StringTokenizer` (Khuyên dùng cho tốc độ cao)**

```java
import java.util.StringTokenizer;

String s = "java    28tech C++";
StringTokenizer st = new StringTokenizer(s); // Mặc định tách theo khoảng trắng
while (st.hasMoreTokens()) {
    System.out.println(st.nextToken());
}

```

---

### 4. Kiểm tra và Chuyển đổi loại ký tự

Sử dụng các phương thức tĩnh của lớp `Character`:

* `Character.isDigit(c)`: Kiểm tra có phải chữ số `0-9`.
* `Character.isLowerCase(c)`: Kiểm tra có phải chữ in thường `a-z`.
* `Character.isUpperCase(c)`: Kiểm tra có phải chữ IN HOA `A-Z`.
* `Character.isAlphabetic(c)`: Kiểm tra có phải chữ cái.
* `Character.toLowerCase(c)` / `Character.toUpperCase(c)`: Ép kiểu chữ.

---

### 5. Chuyển đổi kiểu và Xử lý Số lớn (BigInteger)

* **Số $\rightarrow$ Chuỗi:** Nhanh nhất là cộng với chuỗi rỗng `String s = "" + 2804;`
* **Chuỗi $\rightarrow$ Số:** Sử dụng `Integer.parseInt(s)` hoặc `Long.parseLong(s)`.

**Lớp BigInteger:** Khi con số quá lớn (lên đến hàng trăm chữ số, vượt qua giới hạn của kiểu `long`), ta phải lưu số dưới dạng Chuỗi (String) và tính toán bằng lớp `BigInteger`.

```java
import java.math.BigInteger;

String s1 = "18238128381283812381123123";
String s2 = "192399239192393";

BigInteger num1 = new BigInteger(s1);
BigInteger num2 = new BigInteger(s2);

System.out.println(num1.add(num2));      // Cộng
System.out.println(num1.subtract(num2)); // Trừ
System.out.println(num1.multiply(num2)); // Nhân
System.out.println(num1.divide(num2));   // Chia lấy nguyên

```

---

### 6. Đếm tần suất xuất hiện của ký tự

Bài toán kinh điển: Đếm số lần mỗi ký tự xuất hiện trong chuỗi và in ra theo thứ tự từ điển.

**Cách 1: Sử dụng mảng đếm (Nhanh nhất)**
Mã ASCII có 256 ký tự cơ bản, ta dùng mảng `int[256]` làm mảng đếm.

```java
String s = "28tech28te";
int[] cnt = new int[256];

for (char x : s.toCharArray()) {
    cnt[x]++; // Tăng tần suất của ký tự lên 1
}

for (int i = 0; i < 256; i++) {
    if (cnt[i] != 0) {
        System.out.println((char) i + " " + cnt[i]);
    }
}

```

**Cách 2: Sử dụng TreeMap (Tiện lợi, tự động sắp xếp key)**

```java
import java.util.TreeMap;
import java.util.Map;

String s = "28tech28te";
TreeMap<Character, Integer> map = new TreeMap<>();

for (char x : s.toCharArray()) {
    if (map.containsKey(x)) {
        map.put(x, map.get(x) + 1);
    } else {
        map.put(x, 1);
    }
}

for (Map.Entry<Character, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " " + entry.getValue());
}

```

---

### 7. Lớp StringBuilder (Chuỗi có thể thay đổi)

Vì `String` là bất biến (immutable), mỗi lần nối chuỗi bằng dấu `+` trong vòng lặp sẽ tạo ra cực kỳ nhiều rác bộ nhớ, làm phần mềm chạy rất chậm. Khắc phục điều này bằng lớp **`StringBuilder`**.

**Ví dụ: Thuật toán chuẩn hóa Tên riêng**

```java
String s = "NGUYEN   Thuy     linh";
StringBuilder sb = new StringBuilder("");
String[] arr = s.split("\\s+"); // Tách các từ

for (String x : arr) {
    // Viết hoa chữ cái đầu
    sb.append(Character.toUpperCase(x.charAt(0)));
    // Viết thường các chữ cái sau
    for (int j = 1; j < x.length(); j++) {
        sb.append(Character.toLowerCase(x.charAt(j)));
    }
    sb.append(" "); // Thêm khoảng trắng giữa các từ
}

sb.deleteCharAt(sb.length() - 1); // Xóa khoảng trắng thừa ở cuối
System.out.println(sb.toString()); // Output: Nguyen Thuy Linh

```

---

## 🛠️ Công cụ sử dụng

* **IDE tham khảo:** IntelliJ IDEA / Eclipse / VS Code
* **Môi trường:** Java Development Kit (JDK) 11+
* **Định dạng:** Markdown (`.md`)
