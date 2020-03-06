# Địa chỉ IP:
- Khi nói đến tầng mạng của mô hình TCP/IP ta có ba giao thức quan trọng:
 - Giao thức định tuyến: Dijkstra hoặc là Bellman Ford.
 - Giao thức ICMP (Internet control message protocols).
 - Giao thức IP.
- Với giao thức IP mục đích của nó là:
 - Xác định địa chỉ tầng mạng sử dụng địa chỉ IP.
 - Xác định ý nghĩa các trường trong datagram (gói dữ liệu PDU của tầng mạng).
 - Hành động của các router và thiết bị đầu cuối khi nhận được datagram.
Hai phiên bản chính được sử dụng là IPv4 và IPv6:
- Nằm giữa thiết bị bất kỳ (Máy tính, router) và một kết nối vật lý là một giao diện ghép nối. Số lượng giao diện ghép nối này có thể là 1 với một máy tính thông thường với 1 đường kết nối vật lý, nhưng có thể là nhiều với một router có nhiệm vụ chuyển gói tin từ một kết nối này tới một kết nối khác.
- Địa chỉ IP sẽ ứng với mỗi giao diện (Không phải ứng với 1 thiết bị). 

## 1. Địa chỉ IPv4:
- Địa chỉ IPv4 có độ dài 32 bit (4 byte).
- Được viết theo ký pháp dấu chấm thập phân (dot-decimal notation): có nghĩa là 1 địa chỉ gồm 32 bit, cứ mỗi 8 bit ta đặt một dấu chấm phía sau, mỗi 8 bit đó ta đổi ra hệ thập phân => trước mỗi dấu chấm (trừ số cuối cùng) là một số có độ lớn từ 0 -> 255.
- 

