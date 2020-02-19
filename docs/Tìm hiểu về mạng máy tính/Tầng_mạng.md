# TẦNG MẠNG:
## 1. Nhiệm vụ (chức năng) chính của tầng mạng:
- Xác định đường chuyền (path determination).
- Chuyển mạch (switching).
- Thiết lập kết nối (call setup).

## 2. Mô hình dịch vụ:
- Chuyển mạch gói: (datagram):
    - Dịch vụ không hướng nối (Connectionless).
    - Các máy tính đặt vào gói tin địa chỉ thiết bị nhận, chuyển gói tin vào mạng. Các thiết bị trung chuyển sẽ định tuyến gói tin về tới đích bằng cách:
      - Xác định địa chỉ đích.
      - Tìm kiếm trên bảng định tuyến.
      - Vì bảng định tuyến được cập nhật liên tục nên các gói tin có thể đến đích theo các con đường khác nhau.
- Chuyển mạch ảo (virtual circuit): 
    (connection oriented) là dịch vụ hướng nối do:
    - Phải thiết lập kết nối và kết thúc kết nối.
    - Duy trì thông tin trạng thái của kết nối tại tất cả các thiết bị trung gian.
    Ba giai đoạn trong dịch vụ chuyền mạch ảo:
    - Thiết lập mạch.
    - Chuyền dữ liệu.
    - Giải phóng mạch ảo.
    - Thông điệp trao đổi giữa các thiết bị: yêu cầu khởi tạo, kết thúc mạch ảo, thông điệp trao đổi giữa các thiết bị chuyển mạch yêu cầu thiết lập VC được gọi là signal message (thông điệp báo hiệu). Giao thức được sử dụng là signal protocols.

## 3. Nguồn gốc:
- CBR xuất phát từ dịch vụ mạng điện thoại chuyền thống sử dụng mạch thực.
- Mạng điện thoại chuyền thống kết nối các thiết bị không có khả năng tính toán (dump devices): bỏi vậy để cung cấp được dịch vụ với các yêu cầu về độ chễ, tốc độ..., tầng mạng phải phức tạp hơn.
- Trái lại với kiến trúc internet, nó kết nối các thiết bị có khả năng tính toán, được thiết kế để đặt các tính năng phụ trợ vào trong các thiết bị đầu cuối thay vì ở mạng khiến cho tầng mạng trở nên đơn giản. Nó không đảm bảo bất kể dịch vụ nào do vậy có thể kết nối mạng sử dụng các công nghệ kết nối khác nhau. (Vệ tinh, Ethernet, cáp quang, sóng vô tuyến).

## 4. Tổng kết mô hình dịch vụ của các kiến trúc mạng:
()
ATM: Các gói tin trong kiến trúc mạng này được gọi là ATM cell.
(tìm hiểu thêm: https://www.cisco.com/c/en/us/support/docs/asynchronous-transfer-mode-atm/atm-traffic-management/10422-cbr.html)
- **Dịch vụ chuyền tốc độ cố định: CBR (constant bit rate)**: Một VC của kiến trúc mạng ATM được cấu hình thành một kết nối sử dụng dịch vụ CBR sẽ cung cấp đường chuyền với một tốc độ ổn định. Với một số thông số, CTD (cell transfer delay) độ trễ của các gói tin, "jitter" hay được gọi là biến thiên độ trễ CDV (cell delay variation), tỷ lệ các cell bị mất (cell lost rate), tốc độ chuyền tối đa CPR (cell peak rate).  
- **Dịch vụ chuyền với tốc độ không xác định ( Unspecified bit rate) UBR**: Giống mô hình cố gắng tối đa của internet, phù hợp với ứng dụng không cần tốc độ chuyền cố định.
- **Dịch vụ chuyền tốc độ có sẵn ABR (avaliable bit rate):** Giống mô hình của internet nhưng thêm hai tính năng quan trọng sau:
    - Được đảm bảo tốc độ chuyền nhỏ nhất MCR (minimun cell rate): Khi tài nguyên rỗi ABR có thể chuyền với tốc độ lơn hơn tốc độ này.
    - Có phản hồi tắc nghẽn từ tầng mạng, từ bên gửi để điều chỉnh tốc độ gửi.
- **Dịch vụ chuyền tốc độ biến đổi** VBR (variable bit rate): Giống như CBR nhưng tốc độ có thể được thay đổi theo một số tham số người dùng nhập. Có hai loại real-time, nonreal-time.

## 5. Nguyên lý định tuyến:







