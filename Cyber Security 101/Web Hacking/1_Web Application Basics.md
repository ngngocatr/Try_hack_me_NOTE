# Web Application Basics
## 1. Giới thiệu
### 1. Giới thiệu
Trong bài học này tìm hiểu những yếu tố quan trọng của web như _URL, HTTP request, HTTP response, ..._\
Bài học sẽ giúp nắm vững những kiến thức thiết yếu, hữu dụng khi muốn xây dựng và làm việc với những ứng dụng web
### 2. Mục tiêu
- Hiểu rõ ứng dụng web là gì? Cách nó hoạt động
- Phân tích `URL` và cách nó truy câp tài nguyên web
- Tìm hiểu cách thức hoạt động của `HTTP request` và `HTTP response`
- Làm quen với các _method request HTTP_
- Hiểu ý nghĩa của các `status code` 
- Các `Headder` và tầm quan trọng của nó với bảo mật
## 2. Tổng quan về ứng dụng web
### 1. Front end
Một ứng dụng web sẽ cho người dùng tương tác với nó bằng cách sử dụng `HTML, CSS, JS`\
`HTML` là một tập hợp các chỉ dẫn hoặc mã lệnh hướng dẫn trình duyệt web để có thể render\
`CSS` dùng để mô tả giao diện chuẩn, chẳng hạn như _màu sắc, kiểu chữ, bố cục_ nhất định\
`Java Script` cho phép người dùng thực hiện các hành động trên web, nó là một tập hợp các hướng dẫn nâng cao hơn, đưa ra các lựa chọn và quyết định về những gì cần hiển thị
### 2. Back end
`Database` là nơi thông tin được lưu trữ, chỉnh sửa và truy xuất của web\
Có rất nhiều thành phần khác hỗ trợ web như _web server, applications server, dịch vụ lưu trữ, các thiết bị mạng,..._ và các phần mềm khác hỗ trợ web\
`WAF`(_Web Application Firewall_) là một thành phần tùy chọn dành cho web, nó giúp lọc bỏ những _request_ độc hại cho _web server_ trước khi nó được _web server_ xử lí
### 3. Tóm lại
Việc xây dựng một ứng dụng web gồm nhiều thành phần:
- `Front end`: _HTML, CSS, JS_ tập trung vào trải nghiệm người dùng trong trình duyệt
- `Back end`: _web server, Database, WAF_ tập trung vào việc xử lí dữ liệu người dùng

## 3. URL
### 1. Khái niệm
Địa chỉ `URL`(_Uniform Resource Locator_) là một địa chỉ web cho phép truy cập cá thông tin trực tuyến: _web, ảnh, video_ hoặc các phương tiện truyền thông khác\
Nó hướng dẫn trình duyệt bạn đến đúng vị trí trên _Internet_
### 2. Cấu trúc
![2026-01-23-21-42-31](./images/2026-01-23-21-42-31.png)

URL được tạo từ nhiều thành phần, mỗi phần có một vai trò khác nhau trong việc tìm kiếm, truy cập tài nguyên

`Scheme`(_giao thức_) là phương thức được sử dụng để truy cập web, các phương thức phổ biến nhất là `HTTP` và `HTTPS`. HTTPS an toàn hơn vì nó mã hóa kết nối. Các web thường bắt buộc dùng `HTTPS` để tăng cường bảo mật\
`User`: một số _URL_ còn có thể bao gồm phần thông tin user đối với các trang web yêu cầu đăng nhập/xác thực. Điều này chủ yếu xảy ra ở những _URL_ cần thông tin đăng nhập để truy cập vào các tài nguyên __nhất định__. Tuy nhiên việc này rất hiếm vì việc đưa thông tin đăng nhập vào _URL_ không an toàn lắm- nó có thể làm lộ thông tin, gây ra các rủi ro bảo mật\
`Host/Domain`(_Tên miền_) là phần quan trọng nhất của _URL_ vì nó cho biết bạn đang truy cập vào trong web nào. Mỗi tên miền phải là duy nhất được đăng kí thông qua các nhà đăng kí tên miền\
`Port` (_Cổng_): số cổng giúp định hướng trình duyệt đến đúng dịch vụ. Số cổng nằm trong khoảng từ `1` đến `443`. Cổng `80` cho `HTTP` và `443` cho `HTTPS`\
`Path` (_Đường dẫn_) là một phần của _URL_ trỏ dẫn đến tệp, trang cụ thể trên máy chủ mà người dùng truy cập\
`Query string` là phần tử URL bắt đầu bằng dấu chấm hỏi (_?_). Nó được sử dụng trong các truy vấn tìm kiếm hoặc trong các trường nhập liệu biểu mẫu. Người dùng có thể tùy chỉnh các chuỗi truy vấn này, nên việc sử lí chúng một cách an toàn là rất quan trọng trong các cuộc tấn công chèn (Injection)\
`Fragment` được bắt đầu bằng dấu `#` giúp trỏ đến một phần cụ thể của web, tương tự `string query`, nó có thể bị thay đổi và chèn mã độc vào
## 4. HTTP Messages
`HTTP Messages` là các gói dữ liệu được trao đổi giữa `client` và `web server`. Những thông điệp này rất quan trọng để hiểu rõ cách thức hoạt động của các web vì chúng cho thấy cách thức họa động của người dùng và phản hồi của server được truyền đạt\
Có 2 loại `HTTP Messages`:
- __HTTP request__: được client gửi đi để kích hoạt hành động dứng dụng trên web
- __HTTP response__: được máy chủ gửi đi để đáp lại request của người dùng

![2026-01-23-22-08-00](../../images/2026-01-23-22-08-00.png)

`Start line` như một phần giới thiệt của thông điệp. Nó cho phép biết được loại thông điệp nào đang được gửi đi, là request từ client hay response từ server

`Header` được tạo thành từ các cắp `key-value` cung cấp thông tin bổ dung, nó đưa ra hướng dẫn cho cả client và server xử lí request hoặc response. Các tiêu đề này bao gồm nhiều thứ như bảo mật, content-type, ..., đảm bảo mọi thứ diễn ra trong suôn sẻ trong quá trình gửi và nhận

`Empty Line` là một dòng trống dùng để phần cách phần tiêu đề với phần nội dung

`Body` là phần lưu trữ data thực tế. Trong một request, body có thể bao gồm data mà người dùng muốn gửi đến server. Trong một response, body chứ nội dung mà người dùng yêu cầu

_?Tại sao việc hiểu thông điệp lại quan trọng_
- Những thông điệp này là nền tảng cho cách giao tiếp của các ứng dụng web. Nếu chúng được cấu hình đúng cách, mọi thứ sẽ hoạt động trơn tru
- Hiểu được cách họa động sẽ giúp chẩn đoán được các sự cố trong giao tiếp web, điều này đồng nghĩa với hiệu suất và độ tin cậy hơn cho ứng dụng web
- Điều này cũng rất quan trọng đối với vấn đề bảo mật. Hiểu rõ các thông diệp HTTP giúp triển khai các biện pháp bảo mật mạnh mẽ để bảo vệ dữ liệu trong quá trình truyền tải

## 5. HTTP Request: request line and methods
**HTTP Request** là tin nhắn mà người dùng (client) gửi đến máy chủ web để tương tác với ứng dụng web và thực hiện một hành động nào đó. Đây thường là điểm tiếp xúc đầu tiên giữa người dùng và máy chủ, do đó việc hiểu rõ cơ chế này là rất quan trọng trong an ninh mạng [1].

Một HTTP Request cơ bản bao gồm các thành phần chính: Method, Path và Version [1].

## 1. Dòng yêu cầu (Request Line)
Dòng đầu tiên của yêu cầu (start line) thông báo cho máy chủ biết loại yêu cầu đang được xử lý. Nó bao gồm 3 phần [2]:
*   **HTTP Method:** Hành động muốn thực hiện.
*   **URL Path:** Đường dẫn đến tài nguyên.
*   **HTTP Version:** Phiên bản giao thức.

> Ví dụ: `METHOD /path HTTP/version` [2]

---

## 2. Các phương thức HTTP (HTTP Methods)

![2026-01-23-22-31-54](../../images/2026-01-23-22-31-54.png)

Phương thức HTTP cho biết hành động mà người dùng muốn thực hiện đối với tài nguyên xác định bởi URL [2].

### Các phương thức phổ biến và lưu ý bảo mật:
*   **GET:** Dùng để lấy dữ liệu mà không thay đổi gì trên server.
    *   *Lưu ý:* Không đặt thông tin nhạy cảm (như mật khẩu, token) vào GET request vì chúng hiển thị dưới dạng văn bản thuần [2].
*   **POST:** Gửi dữ liệu đến server (thường để tạo hoặc cập nhật).
    *   *Lưu ý:* Luôn xác thực (validate) và làm sạch (clean) đầu vào để tránh tấn công SQL injection hoặc XSS [3].
*   **PUT:** Thay thế hoặc cập nhật tài nguyên.
    *   *Lưu ý:* Phải đảm bảo người dùng có quyền (authorized) trước khi chấp nhận yêu cầu [3].
*   **DELETE:** Xóa tài nguyên khỏi server.
    *   *Lưu ý:* Tương tự PUT, cần kiểm tra kỹ quyền hạn của người dùng [3].

### Các phương thức khác:
*   **PATCH:** Cập nhật một phần của tài nguyên. Cần xác thực dữ liệu để tránh không nhất quán [4], [5].
*   **HEAD:** Giống GET nhưng chỉ lấy phần headers (không lấy nội dung), dùng để kiểm tra metadata [4].
*   **OPTIONS:** Cho biết các phương thức nào được hỗ trợ cho một tài nguyên cụ thể [4].
*   **TRACE:** Hiển thị các phương thức được phép (thường dùng debug). Nên tắt (disable) nếu không dùng vì lý do bảo mật [4], [5].
*   **CONNECT:** Dùng để tạo kết nối bảo mật (ví dụ: HTTPS) cho giao tiếp mã hóa [5].

---

### 3. Đường dẫn URL (URL Path)
URL path chỉ định vị trí tài nguyên mà người dùng đang yêu cầu (ví dụ: `/api/users/123` xác định một người dùng cụ thể) [5].

**Bảo mật:** Kẻ tấn công thường thao túng URL path để khai thác lỗ hổng, vì vậy cần thực hiện 3 điều sau [6]:
1.  **Validate (Xác thực):** Ngăn chặn truy cập trái phép.
2.  **Sanitise (Làm sạch):** Tránh các cuộc tấn công tiêm nhiễm (injection attacks).
3.  **Protect (Bảo vệ):** Bảo vệ dữ liệu nhạy cảm thông qua đánh giá rủi ro và quyền riêng tư.

---

## 4. Các phiên bản HTTP (HTTP Versions)
Phiên bản HTTP xác định giao thức giao tiếp giữa client và server [6].

*   **HTTP/0.9 (1991):** Phiên bản đầu tiên, chỉ hỗ trợ GET [7].
*   **HTTP/1.0 (1996):** Thêm headers và hỗ trợ nhiều loại nội dung hơn, cải thiện caching [7].
*   **HTTP/1.1 (1997):** Có kết nối liên tục (persistent connections), vẫn được sử dụng rộng rãi và tương thích tốt nhất hiện nay [7], [8].
*   **HTTP/2 (2015):** Hiệu suất nhanh hơn nhờ ghép kênh (multiplexing), nén header và ưu tiên tải [7].
*   **HTTP/3 (2022):** Sử dụng giao thức mới (QUIC) giúp kết nối nhanh và an toàn hơn so với HTTP/2 [7].

*Lưu ý:* Dù HTTP/2 và HTTP/3 nhanh và an toàn hơn, nhiều hệ thống vẫn dùng HTTP/1.1 do tính tương thích cao với các thiết lập hiện có [8].