# **SQL Injection Lab**
- ### Người thực hiện: Đoàn Thái Minh Khang
- ### Thời gian: 10/7/2022
- ### Mục lục:
[A. KHÁI NIỆM](https://github.com/kahang3000/SQL-Injection#a-kh%C3%A1i-ni%E1%BB%87m)
1. SQL Injection là gì?
2. Ảnh hưởng của SQLi?
3. Phân loại

[B. DEMO MỘT SỐ LOẠI SQLi](https://github.com/kahang3000/SQL-Injection#b-demo-m%E1%BB%99t-s%E1%BB%91-lo%E1%BA%A1i-sqli)
1. UNION-based SQLi
2. Error-based SQLi
3. Blind SQLi

***
## **A. KHÁI NIỆM**

### **1. SQL Injection là gì?**
- Là lỗ hổng Web cho phép Attacker can thiệp vào các câu truy vấn mà Web App truyền đến Database.
- Thông thường lỗ hổng cho phép Attacker view data và trong nhiều trường hợp có thể chỉnh sửa hoặc xóa data.
- Trong một vài tình huống Attacker lợi dụng SQLi làm bàn đạp để tấn công vào server hoặc các cơ sở Back-end hoặc DoS.

### **2. Ảnh hưởng của SQLi?**
- Cho phép Attacker truy cập trái phép, thay đổi dữ liệu nhạy cảm như: Password, Credit Card, Credentials,…
- Các doanh nghiệp bị leaked data có thể ảnh hưởng đến danh tiếng/uy tín và phải đền tiền bồi thường.
- Một vài trường hợp Attacker có thể để lại Backdoor làm bàn đạp cho các cuộc tấn công chuyên sâu hơn.

### **3. Phân loại**
- In-band SQLi
    - Error-based SQLi
    - Union-based SQLi
- Inferential SQLi (Blind SQLi)
    - Blind-boolean-based SQLi
    - Time-based-blind SQLi
- Out-of-band SQLi

***
## **B. DEMO MỘT SỐ LOẠI SQLi**
### **1. UNION-based SQLi:**

- Bằng cách lợi dụng toán tử **UNION** trong ngôn ngữ SQL cho phép tổng hợp kết quả của 2 hay nhiều câu truy vấn **SELECTION** để nhận được HTTP response có thể chứa dữ liệu mà Attacker có thể sử dụng.
- Entry point có lỗ hổng SQLi

     http://localhost/CRUD/read.php
```php
<?php
// Check existence of id parameter before processing further
if(isset($_GET["id"])){
    // Include config file
    require_once "config.php";

    $id = $_GET['id'];
    $sql = "SELECT * FROM nhanvien WHERE id = $id";
    $result = mysqli_query($link, $sql);
    if (mysqli_num_rows($result) > 0) {
        // Store data of each row
        while($row = mysqli_fetch_assoc($result)) {
            $name = $row["name"];
            $address = $row["address"];
            $salary = $row["salary"];
            echo "<pre>ID: {$id}<br />Name: {$name}<br />Address: {$address}<br />Salary: {$salary}<br /></pre>";
            echo '<a href="welcome.php">Go back</a>';
        }
        } else {
        echo "0 Results";
        }
        mysqli_close($link);
    }
?>

```
