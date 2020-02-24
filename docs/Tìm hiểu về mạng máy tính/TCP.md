# Giao thức tầng giao vận TCP: transmission control protocol
## Đặc điểm:
- tính hướng nối: có thao tác thiết lập đường chuyền (three-way handshake).
- Tin cậy: sử dụng các nguyên lý của giao thức Go-back-N và selective repeate để cung cấp dịch vụ tin cậy trên nền của một đường chuyền không tin cậy của tầng dưới IP.

## Kết nối TCP:
- Kết nối TCP là kết nối song công, full duplex. Nó thuộc kiểu kết nối điểm điểm.
- Chỉ hoạt động trên các thiết bị đầu cuối, không hoạt động trên các thiết bị trung gian.
(Kết nối TCP):
Giải thích:

- Các tiến trình sau khi đẩy dữ liệu qua socket (cửa), sau khi qua socket, dữ liệu được đưa vào buffer, tiến trình sẽ không kiểm soát được dữ liệu nữa mà do chính thực thể TCP kiểm soát. Sau đó TCP sẽ gửi dần dữ liệu trong buffer.
- Lượng dữ liệu lớn nhất được đặt trong một segment giới hạn bởi biến MSS (Maximun segment size). Các giá trị phổ biến có thể là 512, 536, 1500 byte. (Để chánh hiện tượng phân mảnh IP). MSS chỉ giới hạn độ lớn của dữ liệu chứa trong gói tin, không phải độ lớn cả gói

## Cấu trúc một gói tin TCP: 
(Ảnh về một gói tin TCP)
Một gói tin TCP bao gồm:
-  Trường tiêu đề : 20 byte (Telnet có 21 byte), bao gồm.
      - Trường số hiệu cổng nguồn, số hiệu cổng đích.
      - Trường số thứ tự (sequence number) 32 bit, số biên nhận (acknowledgement number) 32 bit.
      - Độ lớn cửa sổ (window size) 16 bit.
      - Độ dài tiêu đề (length field) 4 bit.
      - Trường option: được sử dụng theo nhu cầu của bên gửi và bên nhận tùy theo việc thương lượng của hai bên.
      - Trường cờ flag 6 bit gồm các bit: ACK, RST, SYN (Thiết lập kết nối), FIN (ứng dụng đóng kết nối), PSH (chuyển dữ liệu lên tầng trên ngay lập tức), URG (khẩn urgent)
      - Còn một số trường khác....
-  Trường dữ liệu : 

## Thiết lập kết nối, giải phóng kết nối:
**Thiết lập kết nối: (Three-way handshake)**

Giả sử một tiến trình chạy trên client muốn thiết lập kết nối đến một tiến trình chạy trên server, tiến trình này sẽ yêu cầu thực thể TCP kết nối tới thực thể TCP của server.

B1: TCP client gửi một segment đặc biệt tới TCP server. Segment không chứa dữ liệu của tầng ứng dụng và trường cờ SYN được đặt là 1. Gói tin này còn được gọi là SYN segment. Sau đó TCP chọn một số thứ tự ban đầu (client_isn) và đặt giá trị này vào trường số thứ tụ của SYN segment.

B2: Gói SYN segment đến server, server phân phối bộ đệm TCP và mộ số biến phù TCP để phục vụ kết nối. Đồng thời TCP sẽ gửi lại client một segment đặc biệt không chứa dữ liệu. Nó chứa SYN có giá trị là 1, trường biên nhận trong tiêu đề có giá trị client_isn+1 (do độ dài của gói dữ liệu gửi cho client có độ dài 1 byte), một giá trị (server_isn) mà server chọn đặt vào trong tiêu đề của gói.

B3: Khi nhận được segment chấp nhận kết nối, client khởi tạo bộ đệm và các biến phục vụ kết nối. Client gửi segment thứ 3 biên nhận lại gói cho segment chấp nhận của server. (đặt giá trị server_isn+1) vào trường số biên nhận của segment. Bit SYN được đặt giá trị 0 và kết nối được thành lập. Gói segment này còn được gọi là SYNACK.

=> Hỏi => Chấp nhận => Đồng ý chấp nhận.

(Ảnh giai đoạn bắt tay ba bước)
(Ảnh trạng thái TCP trong quá trình kết nối).

**Đóng kết nối***
Điều kiện đóng: 
- Hai bên đều kết thúc kết nối.
- Giải phóng các tài nguyên phục vụ cho việc kết nối + các biến TCP.

Quá trình:
B1: TCP client sẽ gửi cho TCP server một segment đặc biệt với cờ FIN bằng 1.   (Yêu cầu đóng kết nối).
B2: TCP server sẽ gửi cho TCP client biên nhận của gói trên.                   (Chấp nhận đóng kết nối).
B3: TCP server sẽ gửi cho TCP cient một segment đặc biệt với cờ FIN trong phần tiêu đề bằng 1.
B4: Client sẽ gửi biên nhận cho gói trên.

(Ảnh kết thúc kết nối TCP)
(Các trạng thái kết nối TCP)







