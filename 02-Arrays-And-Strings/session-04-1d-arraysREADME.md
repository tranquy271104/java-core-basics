<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=Java%201D%20Arrays%20Notes&fontSize=60&fontColor=ffffff" alt="Header Banner">

  <h1>📦 Tổng Hợp Kiến Thức Mảng 1 Chiều</h1>
  <p><i>Tài liệu tóm tắt súc tích, dễ hiểu về Cấu trúc dữ liệu Mảng 1 Chiều (1D Array) trong Java.</i></p>
  
  <p>
    <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java Badge" />
    <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown Badge" />
    <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status Badge" />
  </p>
</div>

---

## 📖 Giới thiệu
Kho lưu trữ này chứa các ghi chép chi tiết về Cấu trúc dữ liệu **Mảng 1 chiều (1D Arrays)**, bao gồm lý thuyết cốt lõi và các dạng thuật toán xử lý mảng kinh điển thường gặp trong các kỳ thi lập trình.

Nguồn tham khảo chính: **28TECH**.

## 📑 Mục lục
1. [Định nghĩa và Tính chất](#1-định-nghĩa-và-tính-chất-của-mảng-1-chiều)
2. [Cú pháp Khai báo mảng](#2-khai-báo-mảng)
3. [Truy cập phần tử và Duyệt mảng](#3-truy-cập-phần-tử-và-duyệt-mảng)
4. [Mảng làm tham số của Hàm](#4-mảng-làm-tham-số-của-hàm)
5. [Ưu và Nhược điểm của Mảng](#5-ưu-và-nhược-điểm-của-mảng)
6. [Các bài toán Mảng 1 chiều cơ bản](#6-một-số-bài-toán-cơ-bản-cần-lưu-ý)

---

## 🚀 Nội dung chi tiết

### 1. Định nghĩa và Tính chất của mảng 1 chiều
* **Khái niệm:** Là một cấu trúc dữ liệu gồm nhiều phần tử có **cùng kiểu dữ liệu**, được lưu trữ ở các ô nhớ **liên tiếp nhau** trong bộ nhớ RAM.
* **Ứng dụng:** Được sử dụng khi bạn cần lưu trữ và xử lý một số lượng khổng lồ các phần tử có cùng đặc tính (Ví dụ: Lưu trữ trọng lượng của 1000 con gà, điểm số của 10.000 học sinh...).
* **Tính phổ biến:** Mảng 1 chiều đơn giản, dễ hiểu và được sử dụng cực kỳ rộng rãi trong mọi ngôn ngữ lập trình.

---

### 2. Khai báo mảng

**Cú pháp tổng quát:**
```java
Data_type[] array_name = new Data_type[Number_of_element];

```

**Các ví dụ khai báo:**

| Khai báo | Ý nghĩa |
| --- | --- |
| `int[] a = new int[100];` | Mảng số nguyên `a` có 100 phần tử |
| `float[] b = new float[1000];` | Mảng số thực `b` có 1000 phần tử |
| `double[] diem = new double[10];` | Mảng số thực `diem` có 10 phần tử |
| `char[] ten = new char[50];` | Mảng ký tự `ten` có 50 phần tử |

**Khởi tạo giá trị ban đầu:**

* Khai báo mảng `a` có 3 phần tử, giá trị mặc định của hệ thống sẽ là `0`:
`int[] a = new int[3];`
* Khai báo và gán trực tiếp giá trị cho các phần tử:
`int[] a = {1, 2, 3};`

---

### 3. Truy cập phần tử và Duyệt mảng

Các phần tử trong mảng được truy cập thông qua **chỉ số (Index)**.

* Chỉ số của mảng luôn bắt đầu từ **`0`** và kết thúc ở **`n - 1`** (với `n` là kích thước mảng).
* Cú pháp truy cập: `array_name[index]`

**Kỹ thuật Duyệt mảng:**

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Nhập số lượng phần tử
        int[] a = new int[n]; // Khởi tạo mảng kích thước n
        
        // 1. Nhập dữ liệu cho mảng bằng vòng lặp For
        for(int i = 0; i < n; i++){
            a[i] = sc.nextInt();
        }
        
        // 2. Duyệt và in mảng bằng For truyền thống (Dựa vào chỉ số index)
        for(int i = 0; i < n; i++){
            System.out.print(a[i] + " ");
        }
        
        // 3. Duyệt và in mảng bằng For-each (Lấy trực tiếp giá trị)
        for(int x : a){
            System.out.print(x + " ");
        }
    }
}

```

> ⚠️ **Chú ý:** Khi khai báo kích thước của mảng, hãy đọc kỹ giới hạn số lượng phần tử tối đa của đầu bài (Contest/OJ) để cấp phát đủ bộ nhớ, tránh lỗi `ArrayIndexOutOfBoundsException`.

---

### 4. Mảng làm tham số của Hàm

Khi truyền một mảng vào làm tham số của hàm, **bản chất là truyền tham chiếu**. Do đó, mọi thay đổi đối với các phần tử bên trong hàm **sẽ làm thay đổi trực tiếp tới mảng gốc** ở bên ngoài.

```java
public class Main {
    // Hàm nhân đôi giá trị các phần tử trong mảng
    public static void nhanDoi(int[] a, int n){
        for(int i = 0; i < n; i++){
            a[i] *= 2; // Cập nhật trực tiếp vào mảng gốc
        }
    }

    public static void main(String[] args) {
        int[] a = {1, 2, 3, 4};
        nhanDoi(a, 4); 
        
        for(int x : a){
            System.out.print(x + " "); // Output: 2 4 6 8
        }
    }
}

```

---

### 5. Ưu và Nhược điểm của Mảng

✅ **Ưu điểm:**

* Đơn giản, dễ hiểu, logic lưu trữ mạch lạc.
* Tốc độ truy cập phần tử cực kỳ nhanh chóng (độ phức tạp O(1)) nhờ việc gọi trực tiếp thông qua chỉ số Index.
* Dễ dàng khai báo hàng loạt phần tử cùng kiểu dữ liệu.
* Dễ dàng thao tác duyệt qua mọi phần tử chỉ với một vòng lặp duy nhất.

❌ **Nhược điểm:**

* **Kích thước cố định (Fixed Size):** Bạn không thể mở rộng hay thu hẹp số lượng phần tử của mảng một khi nó đã được cấp phát.
* Việc chèn (Insert) hoặc xóa (Delete) phần tử ở giữa mảng cực kỳ tốn thời gian và khó khăn do phải dịch chuyển hàng loạt các ô nhớ phía sau.

---

### 6. Một số bài toán cơ bản cần lưu ý

**a. Tìm phần tử nhỏ nhất và lớn nhất (Max/Min)**

```java
// Giả sử mảng a có n phần tử đã được nhập dữ liệu
int maxElement = a[0];
int minElement = a[0];

for(int i = 1; i < n; i++){
    // Cách 1: Dùng lệnh if
    if (a[i] > maxElement) maxElement = a[i];
    
    // Cách 2: Dùng hàm Math của Java (Ngắn gọn và khuyên dùng hơn)
    minElement = Math.min(a[i], minElement);
}

```

**b. Liệt kê hoặc Đếm phần tử thỏa mãn điều kiện**
Sử dụng kết hợp vòng lặp và câu lệnh rẽ nhánh `if`. Hoặc có thể viết thêm các hàm kiểm tra logic (ví dụ: Hàm kiểm tra Số nguyên tố, Số hoàn hảo, Số chính phương...) rồi gọi vào trong vòng lặp.

**c. Bài toán liên quan tới Cặp số (Mọi tổ hợp chập 2)**
Khi bạn cần xét mọi cặp 2 phần tử trong mảng (Ví dụ: Đếm số cặp có tổng bằng `K`), bạn bắt buộc phải dùng **2 vòng lặp For lồng nhau**.

```java
int ans = 0;
// Vòng lặp i chạy từ đầu đến kế cuối
for (int i = 0; i < n; i++) {
    // Vòng lặp j chạy từ phần tử ngay sau i cho tới cuối mảng
    for (int j = i + 1; j < n; j++) {
        if (a[i] + a[j] == K) {
            ans++;
        }
    }
}

```

*(Tổng quát: Nếu cần xét bộ `k` phần tử, bạn cần `k` vòng For lồng nhau).*

**d. Sắp xếp mảng (Arrays.sort)**

```java
import java.util.Arrays;
import java.util.Collections;

// 1. Sắp xếp Tăng dần (Áp dụng được cho mảng nguyên thủy int[])
int[] a = {1, 3, 2, 5, 4};
Arrays.sort(a); // Output: 1 2 3 4 5

// 2. Sắp xếp Giảm dần (BẮT BUỘC dùng mảng Object Integer[])
Integer[] b = {1, 3, 2, 5, 4};
Arrays.sort(b, Collections.reverseOrder()); // Output: 5 4 3 2 1

```

**e. Tìm kiếm phần tử X trong mảng (Linear Search)**

```java
public static boolean timKiem(int[] a, int n, int x) {
    for (int i = 0; i < n; i++) {
        if (a[i] == x) {
            return true; // Dừng hàm ngay lập tức nếu tìm thấy
        }
    }
    return false; // Duyệt hết mảng không thấy thì trả về false
}

```

---

## 🛠️ Công cụ sử dụng

* **IDE tham khảo:** IntelliJ IDEA / Eclipse / VS Code
* **Môi trường:** Java Development Kit (JDK) 11+
* **Định dạng:** Markdown (`.md`)
