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
- Định tuyến: việc xác định đường đi của các gói tin khi đi qua các thiết bị trung gian.
- Trái tim của một giao thức định tuyến là một thuật toán định tuyến, với một mục tiêu: có một tập hợp các router và các liên kết giữa chúng ta phải sác định được đường đi tốt nhất cho gói tin từ nguồn tới đích.
- Ta sẽ sử dụng ký thuật biểu diễn sơ đồ mạng đồ thị:
(ảnh).
- Các đỉnh (node) (nút) của sơ đồ này biểu diễn các router, những đoạn thẳng (cung) biểu diễn kết nối giữa hai nút, các kết nối này sẽ có một giá tri ta gọi là giá của cung, là một giá trị đại số biểu thị cho độ khó của việc chuyền gói tin qua cung đó (giá trị càng lớn chuyền càng khó), (thực tế dựa trên thực tế độ tắc nghẽn hay trễ của đường chuyền).

**Phân loại thuật toán**: Thuật toán định tuyến có hai loại:
        - **Thuật toán định tuyến toàn cục:** (global) thuật toán yêu cầu dữ liệu về tất cả các cung trong mạng, chúng được gọi là link state vì phải biết được mỗi liên kết vào mạng trước khi bước vào quá trình tính toán.
        - **Thuật toán định tuyến phân tán:** Thực hiện dần theo hình thức phân tán, không nút nào co đầy đủ thông tin về giá của các liên kết trong mạng. (giải thích tạm)
Có thêm 2 kiểu phân loại nữa là: theo nơi tính toán (tập trung vs nhiều nới) để nói đến nơi chạy thuật toán định tuyến, theo tính chất động hay tĩnh của giao thức (Chỉ sự thay đổi của các tuyến đường theo thời gian do tác động của các yếu tố bên ngoài).

### a. Thuật toán linkk state: Dijkstra
- Cần phải xác định được cấu trúc mạng và giá của các kết nối đều phải được sác định trước. Điều này sảy ra bằng cách mỗi nút sẽ tự gửi thông điệp quảng bá về mình khi tham gia vào mạng sau đó mạng sẽ dần dần biết được thông tin về toàn bộ mạng. 
- Còn được gọi là thuật toán Dijkstra (theo tên người phát minh).
- Link hướng dẫn: https://www.youtube.com/watch?v=XB4MIexjvY0&t=474s
- Độ phức tạp của thuật toán qua n bước: n.(n+1)/2 (hay gọi là O(n^2)) có thể được cải thiệt bằng cách sử dụng cấu trúc dữ liệu HEAP.

### b. Thuật toán distance vector: Belman Ford.








