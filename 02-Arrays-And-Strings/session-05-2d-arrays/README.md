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
Kho lưu trữ này chứa các ghi chép chi tiết về Cấu trúc dữ liệu **Mảng 2 chiều (2D Arrays)**. [cite_start]Mảng 2 chiều được sử dụng phổ biến trong các bài toán liên quan tới ma trận, bảng số, hoặc lưu trữ tọa độ hệ Oxy[cite: 820, 1131]. [cite_start]Có thể coi mảng 2 chiều chính là các mảng 1 chiều được xếp chồng lên nhau[cite: 820].

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

**a. Khai báo mảng 2 chiều:**
[cite_start]Khi khai báo, các bạn cần chỉ định rõ số hàng (row) và số cột (column) của ma trận[cite: 826].

```java
// Khai báo mảng 2 chiều trống có 3 hàng và 3 cột
[cite_start]int[][] b = new int[3][3]; [cite: 838]

// Khai báo và khởi tạo trực tiếp giá trị
int[][] a = {
    {1, 2, 3}, // Hàng 0
    {4, 5, 6}, // Hàng 1
    {7, 8, 9}  // Hàng 2
[cite_start]}; [cite: 831, 832, 835, 836]

```

**b. Truy cập phần tử:**
Để truy cập phần tử, dùng cú pháp `tên_mảng[chỉ_số_hàng][chỉ_số_cột]`. Cả hàng và cột đều được đánh số từ `0`.

* 
*Ví dụ:* `a[0][2]` sẽ lấy phần tử ở hàng 0, cột 2 (Giá trị là 3).



---

### 2. Nhập và Duyệt mảng 2 chiều

Để duyệt qua mảng 2 chiều, ta cần sử dụng **2 vòng lặp For lồng nhau**: vòng lặp ngoài chạy theo từng hàng, vòng lặp trong chạy theo từng cột của hàng đó.

```java
Scanner sc = new Scanner(System.in);
int n = sc.nextInt(); [cite_start]// Số hàng [cite: 857]
int m = sc.nextInt(); [cite_start]// Số cột [cite: 858]
[cite_start]int[][] a = new int[n][m]; [cite: 864]

// 1. Nhập mảng 2 chiều
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        [cite_start]a[i][j] = sc.nextInt(); [cite: 864, 865]
    }
}

// 2. In mảng 2 chiều
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        [cite_start]System.out.print(a[i][j] + " "); [cite: 867, 868]
    }
    System.out.println(); // Xuống dòng sau khi in xong 1 hàng
}

```

---

### 3. Các bài toán cơ bản trên Ma trận

**a. Tìm phần tử Lớn nhất / Nhỏ nhất:**

```java
[cite_start]int minVal = Integer.MAX_VALUE; [cite: 878]
[cite_start]int maxVal = Integer.MIN_VALUE; [cite: 878]

for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        [cite_start]minVal = Math.min(minVal, a[i][j]); [cite: 883, 884, 885]
        [cite_start]maxVal = Math.max(maxVal, a[i][j]); [cite: 886, 887]
    }
}

```

**b. Tính tổng từng hàng của ma trận:**

```java
for (int i = 0; i < n; i++) {
    int rowSum = 0; [cite_start]// Reset tổng mỗi khi sang hàng mới [cite: 905]
    for (int j = 0; j < m; j++) {
        [cite_start]rowSum += a[i][j]; [cite: 906, 907]
    }
    System.out.println("Tổng hàng " + i + ": " + rowSum);
}

```

**c. Cộng / Trừ / Nhân Ma trận:**

* **Cộng/Trừ:** Hai ma trận phải **cùng kích thước** (cùng số hàng và cột). Kết quả là `a[i][j] + b[i][j]`.


* 
**Nhân 2 ma trận:** Để ma trận A (cỡ $n \times m$) nhân được với ma trận B (cỡ $p \times q$), thì **số cột của A phải bằng số hàng của B** ($m = p$). Ma trận kết quả C sẽ có cỡ $n \times q$.



```java
// Cấu trúc nhân ma trận C = A * B
int[][] c = new int[n][q];
for(int i = 0; i < n; i++) {
    for(int j = 0; j < q; j++) {
        c[i][j] = 0;
        for(int k = 0; k < m; k++) {
            c[i][j] += a[i][k] * b[k][j]; [cite_start]// Tích vô hướng [cite: 984, 986, 987, 988]
        }
    }
}

```

---

### 4. Kỹ thuật duyệt các ô liền kề (dx, dy)

Đây là kỹ thuật cực kỳ quan trọng để giải các bài toán trên lưới (Grid), tìm đường đi BFS/DFS. Thay vì viết nhiều lệnh `if`, ta dùng 2 mảng `dx` và `dy` để sinh ra tọa độ của các ô xung quanh.

* 
**Duyệt 4 ô chung cạnh (Lên, Xuống, Trái, Phải):** 



```java
[cite_start]int[] dx = {-1, 0, 0, 1}; [cite: 1009]
[cite_start]int[] dy = {0, -1, 1, 0}; [cite: 1010]

for (int k = 0; k < 4; k++) {
    int i_new = i + dx[k]; [cite_start]// Tọa độ hàng mới [cite: 1028, 1029]
    int j_new = j + dy[k]; [cite_start]// Tọa độ cột mới [cite: 1028, 1029]
    // ... Kiểm tra (i_new, j_new) có hợp lệ không rồi xử lý
}

```

* 
**Duyệt 8 ô chung đỉnh (Gồm cả 4 ô chéo):** 



```java
[cite_start]int[] dx = {-1, -1, -1, 0, 0, 1, 1, 1}; [cite: 1042]
[cite_start]int[] dy = {-1, 0, 1, -1, 1, -1, 0, 1}; [cite: 1042]

```

* 
**Duyệt 8 nước đi của Quân Mã (Knight) trên bàn cờ:** 



```java
[cite_start]int[] dx = {-2, -2, -1, -1, 1, 1, 2, 2}; [cite: 1070]
[cite_start]int[] dy = {-1, 1, -2, 2, -2, 2, -1, 1}; [cite: 1072]

```

---

### 5. Sắp xếp mảng 2 chiều theo hàng

Khi muốn lưu các cặp số (ví dụ: tọa độ điểm $Oxy$), mảng 2 chiều là một lựa chọn hoàn hảo. Ta có thể sử dụng `Comparator` để sắp xếp các tọa độ này theo một điều kiện cụ thể.

*Ví dụ:* Cho danh sách tọa độ, sắp xếp tăng dần theo hoành độ $X$. Nếu hoành độ bằng nhau thì sắp xếp tăng dần theo tung độ $Y$.

```java
// Khai báo mảng Object Integer để dùng Comparator
[cite_start]Integer[][] a = new Integer[n][2]; [cite: 1139]

// ... Nhập dữ liệu cho a[i][0] và a[i][1] ...

[cite_start]Arrays.sort(a, new Comparator<Integer[]>() { [cite: 1145]
    @Override
    [cite_start]public int compare(Integer[] o1, Integer[] o2) { [cite: 1146]
        [cite_start]if (o1[0] != o2[0]) { [cite: 1149]
            return o1[0] - o2[0]; [cite_start]// So sánh X [cite: 1150, 1151]
        } else {
            return o1[1] - o2[1]; [cite_start]// So sánh Y [cite: 1154, 1156]
        }
    }
});

```

---

## 🛠️ Công cụ sử dụng

* **IDE tham khảo:** IntelliJ IDEA / Eclipse / VS Code
* **Môi trường:** Java Development Kit (JDK) 11+
* **Định dạng:** Markdown (`.md`)
