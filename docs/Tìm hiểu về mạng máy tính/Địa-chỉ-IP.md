# Địa chỉ IP:
- Khi nói đến tầng mạng của mô hình TCP/IP ta có ba giao thức quan trọng:
  - Giao thức định tuyến: Dijkstra hoặc là Bellman Ford.
  - Giao thức ICMP (Internet control message protocols).
  - Giao thức IP.
- Với giao thức IP có các ứng dụng sau:
  - Xác định địa chỉ tầng mạng, cách sử dụng địa chỉ IP.
  - Xác định ý nghĩa các trường trong datagram (gói dữ liệu PDU của tầng mạng).
  - Xác định hành động của các router và thiết bị đầu cuối khi nhận được các datagram.
- Hai phiên bản chính và được được sử dụng phổ biến là IPv4 và IPv6:

**Định nghĩa: giao diện**
- Nằm giữa thiết bị bất kỳ (Máy tính, router) và một kết nối vật lý là một giao diện ghép nối. Số lượng giao diện ghép nối này có thể là 1 với một máy tính thông thường với 1 đường kết nối vật lý, nhưng có thể là nhiều với một router có nhiệm vụ chuyển gói tin từ một kết nối này tới một kết nối khác.
- Địa chỉ IP sẽ ứng với mỗi giao diện (Không phải ứng với 1 thiết bị). 

## 1. Địa chỉ IPv4:
- Địa chỉ IPv4 có độ dài 32 bit (4 byte). Đủ để đánh địa chỉ cho 4.3 tỉ giao diện kết nối.
- Được viết theo ký pháp dấu chấm thập phân (dot-decimal notation): có nghĩa là 1 địa chỉ là một dải gồm 32 bit, cứ mỗi 8 bit ta đặt một dấu chấm phía sau, mỗi 8 bit nằm giữa hai dấu chấm ta đổi ra hệ thập phân => mỗi số ta thu đươc là một số có độ lớn từ 0 -> 255.
- Địa chỉ cho mạng: Mỗi giao diện kết nối của một máy tính hoặc một router phải có một địa chỉ IP xác định duy nhất. Địa chỉ này ko thể lựa chọn một cách tùy ý mà phải phụ thuộc vào mạng mà nó kết nối vào. 

  **Mạng**: Là cấu trúc tổng thể gồm các máy tính, router và liên kết giữa chúng. Thuật ngữ này còn được sử dụng với ý nghĩa cụ thể hơn, liên quan chặt chẽ tới địa chỉ IP.

![IPv4 struc](/docs/pics/28_IPv4.png)

  Trong hình vẽ trên 3 giao diện của router được kết nối tới 7 máy tính. Địa chỉ giao diện của các router và máy tính có các đặc điểm là 24 bit đầu là giống nhau. Chúng được kết nối với nhau bằng một kết nối duy nhất. 

  Giao diện của những máy tính này, và giao diện nối chúng vào router tạo thành một mạng IP. (IP network) hay đơn giản là mạng.

  Với một cấu trúc liên mạng gồm nhiều router và máy tính, chúng ta có thể sử dụng một phương pháp để xác định các mạng trong hệ thống. Ta bỏ hết các giao diện của các máy tính và router đi, còn lại được các mạng cô lập, mỗi mạng đó được gọi là một mạng IP.

### a. Kiến trúc của địa chỉ IP:
  Cấu trúc của địa chỉ IPv4:
- 24 bit địa chỉ ban đầu giống nhau được gọi là phần mạng.
- 8 bit địa chỉ còn lại là phần host của địa chỉ IP.
  Ký hiệu VD: 22.3.1.1.0/24 trong đó ký hiệu "/24" được gọi là mặt nạ mạng (network mask), chúng cũng được xem như là tiền tố mạng (network prefix). 

  Kiến trúc địa chỉ Internet đầu tiên được đưa ra 4 lớp địa chỉ được minh họa như hình vẽ dưới đây:

![IPv4 struc](/docs/pics/27_cấu_trúc_IPv4.png)

  Lớp E được dự trữ cho tương lai, nghiên cứu và phát triển hệ thống mạng.

  Nhưng cấu trúc chia ra bốn lớp địa chỉ này không còn được sử dụng nữa, nó không còn hợp lý khi số các tổ trức nhỏ và vừa ra tăng. Một lớp địa chỉ IP có thể là quá lớn so với một tổ trức nhưng lớp khác lại là quá nhỏ cho một tổ trức khác. Với kiểu gán địa chỉ không phù hợp như vậy thì không gia địa chỉ (address space) IPv4 sẽ nhanh chóng bị cạn kiệt. 

  Để giải quyết vấn đề này, vào năm 1993,tổ trức IETF đã chuẩn hóa "Định tuyến liên miền không phân lớp" (Classless interdomain routing - CIDER). Nó cho phép độ dài của phần mạng (tiền tố mạng) của địa chỉ IP tùy ý, không nhất thiết là 8, 16, 24 bit. Đồng nghĩa với việc cấp địa chỉ cho các tổ chức sẽ không gây ra hiện tượng bị thừa hay thiếu.

Khuân dạng mới theo chuẩn CIDER sẽ có dạng **a.b.c.d/x** 
VD: a.b.c.d/21 thì 21 bit đầu được xác định là địa chỉ mạng của tổ chức. 

Trên thực tế tổ chức có thể tiếp tục chia 11 bit còn lại để tạo thành các mạng con (subnetting).

### b. Gán địa chỉ cho mỗi giao diện:
- Cấu hình bằng tay. Địa chỉ IP được người quản trị viên của mạng cấu hình vào máy tính (thường trong file cấu hình).
- Giao thức cấu hình bằng địa chỉ động (DHCP Dynamics host configuration protocol). Cho phép một máy chủ gán một địa chỉ IP cho một máy hỗ trợ giao thức DHCP khi được yêu cầu.

### c. Cấp địa chỉ IP:
- Địa chỉ IP được một tổ chức phi lợi nhuận ICANN quản lý theo nguyên tắc ghi trong RFC 2050, nó còn quản trị các root server DNS. Nó chịu trách nghiệm đặt tên miền cũng như giải quyết tranh chấp về đặt tên miền. 
- Hiện nay việc phân phối địa chỉ IP được cơ quan đăng ký cấp vùng quản lý có 3 cơ quan như vậy:
  - ARIN: cho khu vực châu Mĩ và một số vùng ở châu Phi.
  - RIPE: Cho khu vực châu Âu.
  - APNIC: cho khu vực châu Á.

## 2. Địa chỉ IPv6:
- Được chuẩn hóa bởi IETF vào năm 1998 với mục tiêu để thay thế địa chỉ IPv4 khi không gian địa chỉ này đang dần cạn kiệt.
- Khác với IPv4, IPv6 có độ dài 128 bit đủ để đánh địa chỉ cho 2^128.
- Địa chỉ IPv6 được biểu diễn bởi 8 phần, cách nhau bởi dấu ":", mỗi phần gồm 16 bit đánh kí tự của mã thập lục phân.
- Đơn giản hóa địa chỉ IPv6: 
  - Với mỗi phần gồm 4 số 0 "0000" sẽ được rút gọn bởi :: đứng cạnh nhau.
  - Với mỗi 1 hay 2 trở lên số 0 nằm bên trái ký tự sẽ được bỏ. 

VD:2001:0db8:0000:0000:0000:8a2e:0370:7334 -> 2001:db8::8a2e:370:7334.

## 3. Chuyển đổi giữa IPv6 và IPv4: 
Có 2 kỹ thuật chuyển đổi được sử dụng: Dual-stack, tunneling.
- **Dual-stack**: Là kỹ thuật đưa vào các thiết bị hỗ trợ cả hai phiên bản IP là IPv4 và IPv6. Những thiết bị như vậy có khả năng gửi và nhận cả hai gói dữ liệu thuộc hai phiên bản của IP. Khi trao đổi với một nút IPv4 nó sẽ sử dụng gói dữ liệu IPv4 và khi trao đổi với một nút IPv6 sẽ sử dụng gói dữ liệu IPv6. Nút này cần phải có cả hai loại địa chỉ, và phải có khả năng nhận biết được nút có khả năng IPv6 hay không. Điều này có thể giải quyết bằng hệ thống DNS.
  - Nhược điểm: Nó cho phép sử dụng cả hai phiên bản. Nhưng giả sử một nút hỗ trợ IPv6 muốn gửi gói tin IPv6 cho một máy hỗ trợ IPv6 qua một nút chỉ hỗ trợ IPv4. Trường hợp này gây ra hiện tượng phải chuyển từ IPv6 sang IPv4, khiến một số trường thông tin trong gói dữ liệu của IPv6 không được bảo toàn. Điều đó sẽ được khắc phục trong Tunneling.

![anh]()
- **Tunneling**: Khắc phục vấn đề trên, kỹ thuật này cho phép đặt gói dữ liệu IPv6 vào trong gói dữ liệu của IPv4 để chuyển đi. Qua các nút chỉ hỗ trợ IPv4 và được tách ra thành gói dữ liệu nguyên bản khi đến nút hỗ trợ IPv6.
![anh2]()

## 4. IPv4-mapped IPv6:
- Sự áp dụng của dual-stack IPv4 và IPv6 đã tạo ra một loại địa chỉ đặc biệt hơn là địa chỉ IPv4-mapped IPv6. 
- Được biểu diễn bởi:
  - 96 bit đầu viết theo ký pháp của IPv6.
  - 32 bit còn lại là của chuẩn IPv4 được viết bởi ký pháp dấu chấm thập phân.
- Loại địa chỉ này không còn được sử dụng do sự khác biệt quá lớn giữa tính năng của hai phiên bản.


