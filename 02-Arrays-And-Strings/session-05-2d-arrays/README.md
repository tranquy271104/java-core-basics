<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=Java%202D%20Arrays%20Notes&fontSize=60&fontColor=ffffff" alt="Header Banner">

  <h1>📦 Tổng Hợp Kiến Thức Mảng 2 Chiều</h1>
  <p><i>Tài liệu tóm tắt súc tích, dễ hiểu về Cấu trúc dữ liệu Mảng 2 Chiều (Ma trận) trong Java.</i></p>
  
  <p>
    <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java Badge" />
    <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown Badge" />
    <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge" alt="Status Badge" />
  </p>
</div>

---

## 📖 Giới thiệu
Kho lưu trữ này chứa các ghi chép chi tiết về Cấu trúc dữ liệu **Mảng 2 chiều (2D Arrays)**. Trong lập trình, mảng 2 chiều thường được ứng dụng để giải quyết các bài toán về ma trận, bảng số, lưới tọa độ (grid), hoặc đồ thị. Về bản chất, mảng 2 chiều chính là một "mảng của các mảng 1 chiều" xếp chồng lên nhau.

Nguồn tham khảo chính: **28TECH**.

## 📑 Mục lục
1. [Khai báo và Truy cập phần tử](#1-khai-báo-và-truy-cập-phần-tử)
2. [Nhập và Duyệt mảng 2 chiều](#2-nhập-và-duyệt-mảng-2-chiều)
3. [Các bài toán cơ bản trên Ma trận](#3-các-bài-toán-cơ-bản-trên-ma-trận)
4. [Kỹ thuật duyệt các ô liền kề (dx, dy)](#4-kỹ-thuật-duyệt-các-ô-liền-kề-dx-dy)
5. [Sắp xếp mảng 2 chiều theo hàng](#5-sắp-xếp-mảng-2-chiều-theo-hàng)

---

## 🚀 Nội dung chi tiết

### 1. Khai báo và Truy cập phần tử

**a. Cú pháp khai báo:**
Khi khởi tạo mảng 2 chiều, ta cần xác định rõ kích thước của 2 chiều: Số hàng (Row) và Số cột (Column).

```java
// Khởi tạo một mảng 2 chiều gồm 3 hàng và 3 cột (các ô nhớ mang giá trị mặc định là 0)
int[][] b = new int[3][3];

// Khai báo và gán giá trị trực tiếp cho từng ô
int[][] a = {
    {1, 2, 3}, // Hàng chỉ số 0
    {4, 5, 6}, // Hàng chỉ số 1
    {7, 8, 9}  // Hàng chỉ số 2
};

```

**b. Cách truy cập:**
Mỗi phần tử được định vị bởi tọa độ `[chỉ_số_hàng][chỉ_số_cột]`. (Lưu ý: Chỉ số luôn bắt đầu từ `0`).

* Ví dụ: Từ mảng `a` ở trên, lệnh `a[0][2]` sẽ trả về phần tử nằm ở hàng đầu tiên, cột thứ ba $\rightarrow$ Giá trị là `3`.

---

### 2. Nhập và Duyệt mảng 2 chiều

Để quét qua toàn bộ các ô trong ma trận, phương pháp chuẩn nhất là dùng **2 vòng lặp `for` lồng nhau**. Vòng ngoài điều khiển biến hàng, vòng trong điều khiển biến cột.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Nhập số lượng hàng
        int m = sc.nextInt(); // Nhập số lượng cột
        int[][] a = new int[n][m];

        // Bước 1: Nhập dữ liệu cho ma trận
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                a[i][j] = sc.nextInt();
            }
        }

        // Bước 2: In ma trận ra màn hình theo đúng định dạng lưới
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                System.out.print(a[i][j] + " ");
            }
            System.out.println(); // Kết thúc một hàng thì bắt buộc phải xuống dòng
        }
    }
}

```

---

### 3. Các bài toán cơ bản trên Ma trận

**a. Tìm giá trị Max / Min của toàn bộ ma trận:**

```java
int minVal = Integer.MAX_VALUE;
int maxVal = Integer.MIN_VALUE;

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        minVal = Math.min(minVal, a[i][j]);
        maxVal = Math.max(maxVal, a[i][j]);
    }
}

```

**b. Tính tổng các phần tử trên từng hàng:**

```java
for (int i = 0; i < n; i++) {
    int rowSum = 0; // Biến lưu tổng phải được reset về 0 mỗi khi chuyển sang hàng mới
    for (int j = 0; j < m; j++) {
        rowSum += a[i][j];
    }
    System.out.println("Tổng của hàng " + i + " là: " + rowSum);
}

```

**c. Phép nhân 2 Ma trận:**
Điều kiện kiên quyết: Số cột của ma trận A bắt buộc phải bằng số hàng của ma trận B. Nếu A cỡ $n \times m$ và B cỡ $m \times p$, thì ma trận kết quả C sẽ có cỡ $n \times p$.

```java
int[][] c = new int[n][p];

for(int i = 0; i < n; i++) {
    for(int j = 0; j < p; j++) {
        c[i][j] = 0;
        for(int k = 0; k < m; k++) {
            c[i][j] += a[i][k] * b[k][j]; 
        }
    }
}

```

---

### 4. Kỹ thuật duyệt các ô liền kề (dx, dy)

Đây là "vũ khí tối thượng" để xử lý các bài toán duyệt đồ thị (BFS, DFS) trên lưới 2D. Thay vì dùng một đống lệnh `if-else` lồng nhau, ta định nghĩa 2 mảng cấu trúc bước đi `dx` và `dy`.

**Trường hợp 1: Duyệt 4 ô chung cạnh (Trên, Dưới, Trái, Phải)**

```java
int[] dx = {-1, 0, 0, 1};
int[] dy = {0, -1, 1, 0};

// Từ ô hiện tại (i, j), ta tạo vòng lặp sinh ra 4 tọa độ lân cận
for (int k = 0; k < 4; k++) {
    int i_new = i + dx[k]; 
    int j_new = j + dy[k]; 
    // Sau đó kiểm tra xem (i_new, j_new) có nằm trong biên của ma trận không rồi xử lý...
}

```

**Trường hợp 2: Duyệt 8 ô chung đỉnh (Bao gồm cả 4 góc chéo)**

```java
int[] dx = {-1, -1, -1, 0, 0, 1, 1, 1};
int[] dy = {-1, 0, 1, -1, 1, -1, 0, 1};

```

**Trường hợp 3: Nước đi của Quân Mã (Knight) trong cờ vua (Hình chữ L)**

```java
int[] dx = {-2, -2, -1, -1, 1, 1, 2, 2};
int[] dy = {-1, 1, -2, 2, -2, 2, -1, 1};

```

---

### 5. Sắp xếp mảng 2 chiều theo hàng

Mảng 2 chiều rất phù hợp để lưu trữ một tập hợp các điểm tọa độ $(x, y)$. Khi cần sắp xếp các tọa độ này theo một quy luật phức tạp, ta sẽ kết hợp `Arrays.sort()` với một `Comparator` tùy chỉnh.

*Ví dụ: Sắp xếp các điểm tăng dần theo hoành độ X. Nếu hoành độ X trùng nhau, tiếp tục sắp xếp tăng dần theo tung độ Y.*

```java
import java.util.Arrays;
import java.util.Comparator;

public class Main {
    public static void main(String[] args) {
        // Lưu ý: Cần dùng mảng đối tượng Integer[][] thay vì int[][] để có thể truyền vào Comparator
        Integer[][] points = new Integer[n][2];
        
        // ... Code nhập dữ liệu ...

        Arrays.sort(points, new Comparator<Integer[]>() {
            @Override
            public int compare(Integer[] p1, Integer[] p2) {
                if (!p1[0].equals(p2[0])) {
                    return p1[0] - p2[0]; // So sánh ưu tiên theo X
                } else {
                    return p1[1] - p2[1]; // So sánh phụ theo Y
                }
            }
        });
    }
}

```

---

## 🛠️ Công cụ sử dụng

* **IDE tham khảo:** IntelliJ IDEA / Eclipse / VS Code
* **Môi trường:** Java Development Kit (JDK) 11+
* **Định dạng:** Markdown (`.md`)
