# Java Basics: Data Types, Variables, Operators & Conditional Statements

## 📖 Giới thiệu

Repository này tổng hợp các kiến thức nền tảng của Java dành cho người mới bắt đầu, bao gồm:

* Kiểu dữ liệu (Data Types)
* Biến (Variables)
* Chú thích (Comments)
* Nhập/Xuất dữ liệu
* Toán tử (Operators)
* Cấu trúc rẽ nhánh (Conditional Statements)
* Bảng mã ASCII và xử lý ký tự

Đây là những kiến thức quan trọng trước khi học về vòng lặp, mảng, hàm và lập trình hướng đối tượng (OOP).

---

## 📂 Nội dung

### 1. Kiểu dữ liệu (Data Types)

Java cung cấp nhiều kiểu dữ liệu nguyên thủy:

| Kiểu dữ liệu | Kích thước |
| ------------ | ---------- |
| byte         | 1 byte     |
| short        | 2 byte     |
| int          | 4 byte     |
| long         | 8 byte     |
| float        | 4 byte     |
| double       | 8 byte     |
| char         | 2 byte     |
| boolean      | 1 byte     |

Ví dụ:

```java
int age = 20;
double gpa = 3.75;
char grade = 'A';
boolean pass = true;
```

---

### 2. Biến (Variables)

Khai báo biến:

```java
int number;
double salary;
char character;
```

Khởi tạo biến:

```java
int age = 19;
double score = 8.5;
```

Quy tắc đặt tên:

✅ Hợp lệ:

```java
studentName
averageScore
totalSalary
```

❌ Không hợp lệ:

```java
1student
student-name
for
while
```

---

### 3. Comments

Chú thích một dòng:

```java
// Đây là comment
```

Chú thích nhiều dòng:

```java
/*
   Đây là
   comment nhiều dòng
*/
```

---

### 4. Nhập xuất dữ liệu

Nhập dữ liệu với Scanner:

```java
Scanner sc = new Scanner(System.in);

int n = sc.nextInt();
double x = sc.nextDouble();
String name = sc.nextLine();
```

Xuất dữ liệu:

```java
System.out.println("Hello Java");
System.out.printf("%.2f", 3.14159);
```

---

### 5. Toán tử (Operators)

#### Toán tử số học

```java
+
-
*
/
%
```

Ví dụ:

```java
int a = 10;
int b = 3;

System.out.println(a + b);
System.out.println(a % b);
```

#### Toán tử so sánh

```java
>
<
>=
<=
==
!=
```

Ví dụ:

```java
System.out.println(a > b);
```

#### Toán tử logic

```java
&&
||
!
```

Ví dụ:

```java
if(a > 0 && b > 0){
    System.out.println("Positive");
}
```

#### Toán tử tăng giảm

```java
a++;
++a;
a--;
--a;
```

#### Toán tử ba ngôi

```java
int result = (a > b) ? a : b;
```

---

### 6. Cấu trúc rẽ nhánh

#### if

```java
if(score >= 5){
    System.out.println("Pass");
}
```

#### if - else

```java
if(score >= 5){
    System.out.println("Pass");
}
else{
    System.out.println("Fail");
}
```

#### if - else if

```java
if(score >= 8){
    System.out.println("Excellent");
}
else if(score >= 6.5){
    System.out.println("Good");
}
else{
    System.out.println("Average");
}
```

#### switch-case

```java
switch(day){
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Unknown");
}
```

---

### 7. ASCII và xử lý ký tự

Kiểm tra chữ thường:

```java
if(c >= 'a' && c <= 'z'){
    System.out.println("Lowercase");
}
```

Kiểm tra chữ hoa:

```java
if(c >= 'A' && c <= 'Z'){
    System.out.println("Uppercase");
}
```

Kiểm tra chữ số:

```java
if(c >= '0' && c <= '9'){
    System.out.println("Digit");
}
```

---

## 🎯 Mục tiêu

Sau khi hoàn thành phần này, bạn có thể:

* Hiểu các kiểu dữ liệu trong Java
* Khai báo và sử dụng biến
* Sử dụng Scanner để nhập dữ liệu
* Thực hiện các phép toán cơ bản
* Viết điều kiện với if, else, switch-case
* Xử lý ký tự bằng bảng mã ASCII

---

## 🚀 Công nghệ sử dụng

* Java SE
* JDK 17+
* IntelliJ IDEA / VS Code / Eclipse

---

## 👨‍💻 Tác giả

Trần Quý

Sinh viên Học viện Công nghệ Bưu chính Viễn thông (PTIT)

Định hướng: Java Backend • Network • System • Cloud • DevOps
