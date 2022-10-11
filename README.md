# **SQL Injection Lab**
- ### Người thực hiện: Đoàn Thái Minh Khang
- ### Thời gian: 10/7/2022
- ### Mục lục:
    - A. KHÁI NIỆM
        1. SQL Injection là gì?
        2. Ảnh hưởng của SQLi?
        3. Phân loại

    - B. DEMO MỘT SỐ LOẠI SQLi
        1. UNION based
        2. Error based
        3. Blind SQLi

***
## **A. KHÁI NIỆM**

**1. SQL Injection là gì?**
- Là lỗ hổng Web cho phép Attacker can thiệp vào các câu truy vấn mà Web App truyền đến Database.
- Thông thường lỗ hổng cho phép Attacker view data và trong nhiều trường hợp có thể chỉnh sửa hoặc xóa data.
- Trong một vài tình huống Attacker lợi dụng SQLi làm bàn đạp để tấn công vào server hoặc các cơ sở Back-end hoặc DoS.

**2. Ảnh hưởng của SQLi?**
- Cho phép Attacker truy cập trái phép, thay đổi dữ liệu nhạy cảm như: Password, Credit Card, Credentials,…
- Các doanh nghiệp bị leaked data có thể ảnh hưởng đến danh tiếng/uy tín và phải đền tiền bồi thường.
- Một vài trường hợp Attacker có thể để lại Backdoor làm bàn đạp cho các cuộc tấn công chuyên sâu hơn.

**3. Phân loại**
- In-band SQLi
    - Error-based SQLi
    - Union-based SQLi
- Inferential SQLi (Blind SQLi)
    - Blind-boolean-based SQLi
    - Time-based-blind SQLi
- Out-of-band SQLi

***
## **B. DEMO MỘT SỐ LOẠI SQLi**