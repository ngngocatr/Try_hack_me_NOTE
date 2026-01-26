# Network Core Protocol
## 1. Giới thiệu
### Mục Tiêu
- DNS
- WHOIS
- HTTP, FTP
- SMTP, POP3, IMAP

## 2. DNS
![2026-01-24-10-19-42](../../images/2026-01-24-10-19-42.png)

## 3. WHOIS
![2026-01-24-10-26-11](../../images/2026-01-24-10-26-11.png)

![2026-01-24-10-22-58](../../images/2026-01-24-10-22-58.png)

## 4. HTTP(s)

![2026-01-24-10-27-19](../../images/2026-01-24-10-27-19.png)

![2026-01-24-10-28-21](../../images/2026-01-24-10-28-21.png)

Sử dụng Wireshark, chúng ta có thể kiểm tra kỹ hơn sự trao đổi dữ liệu giữa trình duyệt Firefox và máy chủ web. Ảnh chụp màn hình bên dưới từ Wireshark hiển thị văn bản được trình duyệt gửi đi ( màu đỏ) và phản hồi của máy chủ web ( màu xanh) . Như bạn có thể thấy, rất nhiều thông tin được trao đổi giữa máy khách và máy chủ mà không được hiển thị cho người dùng. Ví dụ như phiên bản máy chủ web và thời điểm trang được sửa đổi lần cuối.
![2026-01-24-10-29-11](../../images/2026-01-24-10-29-11.png)

## 5. FTP
![2026-01-24-10-45-37](../../images/2026-01-24-10-45-37.png)
![2026-01-24-10-46-00](../../images/2026-01-24-10-46-00.png)

## 6. SMTP
![2026-01-24-10-54-03](../../images/2026-01-24-10-54-03.png)

![2026-01-24-10-57-09](../../images/2026-01-24-10-57-09.png)

![2026-01-24-10-57-41](../../images/2026-01-24-10-57-41.png)

## 7. POP3
![2026-01-24-11-00-29](../../images/2026-01-24-11-00-29.png)

![2026-01-24-11-00-47](../../images/2026-01-24-11-00-47.png)

![2026-01-24-11-00-59](../../images/2026-01-24-11-00-59.png)

Trong cửa sổ terminal bên dưới, ta có thể thấy một phiên POP3 qua telnet. Vì máy chủ POP3 mặc định lắng nghe trên cổng TCP 110, lệnh để kết nối đến cổng TELNET là telnet `10.48.186.108 110`. Đoạn mã trao đổi bên dưới truy xuất tin nhắn email đã gửi trong tác vụ trước đó.
![2026-01-24-11-01-56](../../images/2026-01-24-11-01-56.png)

Theo các bản ghi Wireshark trước đây, các lệnh màu đỏ được gửi bởi máy khách, và các dòng màu xanh là của máy chủ. Rõ ràng là người nào đó thu thập lưu lượng truy cập cũng có thể đọc được mật khẩu.
![2026-01-24-11-02-18](../../images/2026-01-24-11-02-18.png)

## 8. Kết luận
![2026-01-24-11-27-55](../../images/2026-01-24-11-27-55.png)