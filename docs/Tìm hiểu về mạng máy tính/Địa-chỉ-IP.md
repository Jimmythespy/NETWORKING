# Địa chỉ IP:
- Khi nói đến tầng mạng của mô hình TCP/IP ta có ba giao thức quan trọng:
  - Giao thức định tuyến: Dijkstra hoặc là Bellman Ford.
  - Giao thức ICMP (Internet control message protocols).
  - Giao thức IP.
- Với giao thức IP mục đích của nó là:
  - Xác định địa chỉ tầng mạng sử dụng địa chỉ IP.
  - Xác định ý nghĩa các trường trong datagram (gói dữ liệu PDU của tầng mạng).
  - Hành động của các router và thiết bị đầu cuối khi nhận được datagram.
- Hai phiên bản chính được sử dụng là IPv4 và IPv6:
- Nằm giữa thiết bị bất kỳ (Máy tính, router) và một kết nối vật lý là một giao diện ghép nối. Số lượng giao diện ghép nối này có thể là 1 với một máy tính thông thường với 1 đường kết nối vật lý, nhưng có thể là nhiều với một router có nhiệm vụ chuyển gói tin từ một kết nối này tới một kết nối khác.
- Địa chỉ IP sẽ ứng với mỗi giao diện (Không phải ứng với 1 thiết bị). 

## 1. Địa chỉ IPv4:
- Địa chỉ IPv4 có độ dài 32 bit (4 byte). Đủ để đánh địa chỉ cho 4.3 tỉ giao diện kết nối.
- Được viết theo ký pháp dấu chấm thập phân (dot-decimal notation): có nghĩa là 1 địa chỉ gồm 32 bit, cứ mỗi 8 bit ta đặt một dấu chấm phía sau, mỗi 8 bit đó ta đổi ra hệ thập phân => trước mỗi dấu chấm (trừ số cuối cùng) là một số có độ lớn từ 0 -> 255.
- Địa chỉ cho mạng: Mỗi giao diện kết nối của một máy tính hoặc một router phải có một địa chỉ IP xác định duy nhất. Địa chỉ này ko thể lựa chọn một cách tùy ý mà phải phụ thuộc vào mạng mà nó kết nối vào. 

Mạng: Là cấu trúc tổng thể gồm các máy tính, router và liên kết giữa chúng. Thuật ngữ này còn được sử dụng với ý nghĩa cụ thể hơn, liên quan chặt chẽ tới địa chỉ IP.

![IPv4](/docs/pics/28_IPv4.png)
Trong hình vẽ trên 3 giao diện của router được kết nối tới 7 máy tính. Địa chỉ giao diện của các router và máy tính có các đặc điểm là 24 bit đầu là giống nhau. Chúng được kết nối với nhau bằng một kết nối duy nhất. 

Giao diện của những máy tính này, và giao diện nối chúng vào router tạo thành một mạng IP. (IP network) hay đơn giản là mạng.

Cấu trúc của địa chỉ IPv4 này:
- 24 bit địa chỉ ban đầu giống nhau được gọi là phần mạng.
- 8 bit địa chỉ còn lại là phần host của địa chỉ IP.

Ký hiệu VD: 22.3.1.1.0/24 trong đó ký hiệu "/24" được gọi là mặt nạ mạng (network mask), chúng cũng được xem như là tiền tố mạng (network prefix). 

Với một cấu trúc liên mạng gồm nhiều router và máy tính, chúng ta có thể sử dụng một phương pháp để xác định các mạng trong hệ thống. Ta bỏ hết các giao diện của các máy tính và router đi, còn lại được các mạng cô lập, mỗi mạng đó được gọi là một mạng IP.

### a. Kiến trúc của địa chỉ IP:
Kiến trúc địa chỉ Internet đầu tiên được đưa ra 4 lớp địa chỉ được minh họa như hình vẽ dưới đây:
![IPv4 struc](/docs/pics/27_cấu_trúc_IPv4.png)

Còn thiếu một lớp E được dự trữ cho tương lai, nghiên cứu và phát triển.

Nhưng cấu trúc chia ra làm bốn lớp địa chỉ này không còn được sử dụng nữa, bởi nó không còn hợp lý khi số các tổ trức nhỏ và vừa càng tăng. Một lớp địa chỉ IP có thể là quá lớn so với một tổ trức nhưng lớp khác lại là quá nhỏ. Với kiểu gán địa chỉ không phù hợp như vậy thì không gia địa chỉ IPv4 sẽ nhanh chóng bị cạn kiệt. Bởi vậy vào năm 1993 IETF chuẩn hóa "Định tuyến liên miền không phân lớp" (Classless interdomain routing - CIDER). Nó cho phép việc độ dài của phần mạng của địa chỉ IP tùy ý, không nhất thiết là 8, 16, 24 bit. 

Khuân dạng mới sẽ có dạng **a.b.c.d/x** 
VD: a.b.c.d/21 thì 21 bit đầu được xác định là địa chỉ mạng của tổ chức. 

Trên thực tế tổ chức có thể tiếp tục chia 11 bit còn lại để tạo thành các mạng con (subnetting).

### b. Gán địa chỉ cho mỗi giao diện:
- Cấu hình bằng tay. Địa chỉ IP được người quản trị viên của mạng cấu hình vào máy tính (thường trong file cấu hình).
- Giao thức cấu hình bằng địa chỉ động (DHCP Dynamics host configuration protocol). Cho phép một máy chủ gán một địa chỉ IP cho một máy DHCP khi được yêu cầu.

### c. Cấp địa chỉ IP:
- Địa chỉ IP được một tổ chức phi lợi nhuận ICANN quản lý theo nguyên tắc ghi trong RFC 2050, nó còn quản trị các root server DNS. Nó chịu trách nghiệm đặt tên miền cũng như giải quyết tranh chấp về đặt tên miền. 
- Hiện nay việc phân phối địa chỉ IP được cơ quan đăng ký cấp vùng quản lý có 3 cơ quan như vậy:
  - ARIN: cho khu vực châu Mĩ và một số vùng ở châu Phi.
  - RIPE: Cho khu vực châu Âu.
  - APNIC: cho khu vực châu Á.







