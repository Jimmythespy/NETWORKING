# Các mô hình mạng:
Các mô hình được giới thiệu: OSI (Open systems interconnection), và TCP/IP.

## 1. Định nghĩa của một mô hình mạng:
Mô hình mạng là một mô hình mang tính khái niệm được đưa ra để chuẩn hóa và đặc trưng hóa các chức năng của một hệ thống viễn thông hoặc một hệ thống máy tính mà không quan tâm tới cở sở hạ tầng bên trong hoặc công nghệ được áp dụng. Mục tiêu của một mô hình mạng là tăng tính liên tác giữa các hệ thống thông tin liên lạc sử dụng các giao thức liên lạc khác nhau. (nguồn Wiki)
(Nghĩa là đưa một mô hình mạng chuẩn để có thể phân loại các thành phần trong một mạng viễn thông bất kỳ).
## 2. Mô hình OSI:

### Lịch sử phát triển của mô hình:
- Vào đầu và giữa những năm 1970 mạng máy tính hầu hết được phát triển từ nguồn: do nhà nước tài trợ (NPL ở Anh, ARPANET ở Mỹ, CYCLADES ở Pháp) hoặc nguồn thứ hai do các nhà cung cấp dịch vụ phát triển các hệ thống mạng với những chuẩn riêng tự phát triển (IBM). Nhưng mạng dữ liệu công cộng tại thời điểm này mới bắt đầu xuất hiện và sử dụng chuẩn X.25.
- Vào đầu những năm 1977 tổ trức ISO (International Organization for Standardization) tổ trức một dự án để phát triển những chuẩn chung và những phương thức mạng. 
- Mô hình OSI được thực hiện phần lớn bởi hai nhà nghiên cứu Mike Canepa và Charlie Bachman tại công ty Honeywell Information Systems. Với mục đích để phát triển một bản thiết kế nguyên mẫu cùng một bản kế hoạch phát triển sản phẩm. Họ là người tham dự những phiên họp đầu tiên với tổ trức ANSI để trình bày mô hình 7 tầng của mình và ngay lập tức được chọn để đề suất cho tiểu ban của ISO.
- Mô hình này được công bố vào tháng 3/1978 và phiên bản kết tiếp vào 6/1979.

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
![]()

### Giao diện giữa các tầng:
- Trên cùng một máy tính, hai tầng kề nhau trao đổi dữ liệu với nhau qua các giao diện (interface). Hay theo thuật ngữ mạng ta gọi là điểm truy cập dịch vụ (Service Access point-SAP) vì tầng trên yêu cầu dịch vụ tầng dưới qua nó.
- Giao diện định nghĩa cách thức và khuôn dạng dữ liệu được trao đổi giữa hai tầng kề nhau trên cùng một thiết bị. Định nghĩa giao diện một cách rõ ràng cho phép thay đổi cách thức triển khai tại một tầng mà không ảnh hưởng tới các tầng khác.

### Tổ trức của các tầng
- Có nhiều cách để phân chia 7 tầng này nhưng ta sẽ phân chia như sau:
- 7 tầng được chia vào 3 nhóm:
  - Nhóm hỗ trợ mạng gồm: tầng vật lý, liên kết dữ liệu, tầng mạng. Chịu trách nghiệm về mặt liên quan đến khía cạnh vật lý khi chuyền dữ liệu.
  - Nhóm hỗ trợ người dùng gồm: phiên, trình diễn, ứng dụng. Chúng tạo khả năng liên tác giữa các phần mềm khác nhau.
  - Tầng giao vận & liên kết dữ liệu: đảm bảo chuyền dữ liệu đầu cuối tin cậy. 
- Phần trên của mô hình OSI thường được triển khai bằng phần mềm, trong khi các tầng dưới là sự triển khai của cả phần cứng lẫn phần mềm.
----------------------------
### Chức năng các tầng:
#### 1. Tầng vật lý:
Tầng vật lý liên quan đến và giải quyết những vấn đề:
- Đặc điểm vật lý và môi trường giao tiếp và chuyền thông: xác định đặc điểm, đặc tính giao diện giữa thiết bị và môi trường chuyền dẫn.
- Biểu diễn bit: dữ liệu xuống tầng vật lý phải được mã hóa dưới dạng bit liên tục để chuyền đi, nó phải xác định được phương thức mã hóa.
- Tốc độ chuyền dữ liệu: Tốc độ chuyền dẫn -số bit gửi đi trong một đơn vị thời gian.
- Đồng bộ hóa các bit: máy gửi và máy nhận phải được đồng bộ hóa ở mức bit.
- Cấu hình đường truyền: liên quan đến việc kết nối thiết bị vào môi trường chuyền thông.
- Topo (mô hình ghép nối vật lý): cách thức các ghép nối các thiết bị vào với nhau để tạo thành mạng.
- Chế độ chuyền dẫn: song công (full-duplex), bán công (half-duplex).

#### 2. Tầng liên kết dữ liệu:
Nhiệm vụ: truyền thông giữa hai nút nối trực tiếp với nhau.
- Framing - đóng gói dữ liệu: tầng liên kết dữ liệu chia luồng bit nhận được từ tầng mạng thành các đơn vị dữ liệu gọi là frame.
- Định địa chỉ vật lý: 
- Kiểm soát lưu lượng: tầng dữ liệu thực hiện việc kiểm soát lưu lượng khi tốc độ nhận bé hơn tốc độ gửi, để ngăn ngừa việc quá tải tại nơi nhận.
- Kiểm soát lỗi: tầng liên kết dữ liệu làm tăng tính tin cậy của tầng vật lý bằng cách sử dụng ký thuật phát hiện và chuyền lại gói tin.
- Kiểm soát truy cập.

#### 3. Tầng mạng:
Nhiệm vụ của tầng mạng:
- Định địa chỉ logic.
- Định tuyến: khi mạng hoặc các nút riêng rẽ được nối với nhau tạo thành một liên mạng, các thiết bị kết nối chung gian phải xác đinh tuyến đường đi cho gói dữ liệu để đến đích.

#### 4. Tầng giao vận:
Nhiệm vụ của tầng giao vận:
- Truyền thông liên tiến trình.
- Phân mảnh và tái hợp nhất gói tin.
- Kiểm soát kết nối.
- Kiểm soát lưu lượng.
- Kiểm soát lỗi.

#### 5. Tầng phiên:
Nhiệm vụ của tầng phiên: tầng phiên đóng vai trò kiểm soát viên của mạng với nhiệm vụ thiết lập, duy trì, đồng bộ hóa tính liên tác giữa hai bên của đoạn hội thoại. 

#### 6. Tầng trình diễn:
Tầng trình diễn có nhiệm vụ biểu diễn cú pháp và ngữ nghĩa của các thông tin và dữ liệu được trao đổi giữa hai hệ thống. 

#### 7. Tầng ứng dụng:
Nhiệm vụ: cho phép người dùng (con người hoặc phần mềm) truy cập vào mạng bằng cách cung cấp giao diện người sử dụng, hỗ trợ các dịch vụ như: thư điện tử , truy cập và chuyền file từ xa....

## 3. Mô hình TCP/IP:
![]()
Bộ giao thức này (được sử dụng cho internet) ra đời trước khi có mô hình OSI. Nó mang tên TCP/IP do sử dụng hai giao thức nền tảng là giao thức giao vận TCP (Transmission control protocols), và giao thức mạng IP (internet protocols).

Không giống hệt OSI mô hình này gồm 5 tầng: vật lý, liên kết dữ liệu, giao vận, mạng và ứng dụng.
Bốn tầng đầu tiên cung cấp các chuẩn vật lý, giao tiếp mạng, liên mạng và chức năng giao cận tương ứng như 4 tầng đầu của mô hình OSI. Tuy nhiên 3 tầng trên cùng của TCP/IP được nhập thành tầng ứng dụng trong mô hình internet.

TCP/IP là mô hình phân cấp được tạo thành bởi các module độc lập, mỗi module cung cấp một trức năng nhất định, tuy vậy mỗi module không nhất thiết phải độc lập với nhau.








