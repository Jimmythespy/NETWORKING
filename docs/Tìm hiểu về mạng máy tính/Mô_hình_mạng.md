# Các mô hình mạng:
Các mô hình được giới thiệu: OSI (Open systems interconnection), và TCP/IP.

## 1. Định nghĩa của một mô hình mạng:
Mô hình mạng là một mô hình mang tính khái niệm được đưa ra để chuẩn hóa và đặc trưng hóa các chức năng của một hệ thống viễn thông hoặc một hệ thống máy tính mà không quan tâm tới cở sở hạ tầng bên trong hoặc công nghệ được áp dụng. Mục tiêu của một mô hình mạng là tăng tính liên tác giữa các hệ thống thông tin liên lạc sử dụng các giao thức liên lạc khác nhau. (nguồn Wiki)
(Nghĩa là đưa một mô hình mạng chuẩn để có thể phân loại các thành phần trong một mạng viễn thông bất kỳ).
## 2. Mô hình OSI:
### Đặc điểm:
- Kiến trúc OSI gồm 7 tầng theo thứ tự từ dưới lên là: Tầng vật lý, tầng liên kết dữ liệu, tầng mạng, tầng giao vận, tầng phiên, tầng trình diễn, tầng ứng dụng.
!(OSI)[]
- Khi phát triển các mô hình các nhà thiết kế đã phân tích quá trình chuyền dữ liệu ra các trức năng cơ bản nhất và nhóm các chức năng này vào các nhóm riêng gọi là một tầng (layer). Bằng cách khoanh vùng và xác định các trức năng trong mô hình, nhà thiết kế đã đưa ra một kiến trúc đạt được cả tính hoàn thiện và linh hoạt. Quan trọng nhất, mô hình OSI tạo ra tính trong suốt hoàn toàn giữa hai hệ thống không tương thích với nhau.
### Đặc điểm của các tầng:
- Tại các thiết bị đầu cuối, mỗi tầng sử dụng các dịch vụ do tầng dưới cung cấp và đến lượt minh cung cấp dịch vụ cho tầng dưới nó nữa. Giữa các máy tính tầng thứ N của một máy lại giao tiếp với tầng thứ N của một máy khác (thiết bị khác). Việc giao tiếp này được tiến hành theo các quy tắc và quy ước đã được thảo thận trước, các quy ước này được gọi là giao thức.
!(OSI)[].
- Tại tầng cuối cùng của mô hình, truyền thông diễn ra trực tiếp. Nhưng đối với các tầng cao hơn, dữ liêu được chuyển dần xuống bên dưới, đi ra khỏi máy gửi tại tầng vật lý. Khi dữ liệu đến máy nhận, nó sẽ được chuyển lên trên đi ngược con đường lúc đến.
- Tại mỗi tầng, dữ liệu của từng tầng sẽ được thêm vào dữ liệu nguyên bản. Các thông tin thêm vào này được gọi là: header (nếu thêm vào đầu dữ liệu), hoặc trailer (Thêm vào cuối dữ liệu). Header được thêm vào tại các tầng 6,5,4,3,2; trailer được thêm vào tại tầng 2.
- Tại tâng 1, gói dữ liệu được chuyển thành dạng tín hiệu có thể truyền qua môi trường vật lý là dây dẫn.

### Giao diện giữa các tầng:
- Trên cùng một máy tính, hai tầng kề nhau trao đổi dữ liệu với nhau qua các giao diện (interface). Hay theo thuật ngữ mạng ta gọi là điểm truy cập dịch vụ (Service Access point-SAP) vì tầng trên yêu cầu dịch vụ tầng dưới qua nó.
- 






