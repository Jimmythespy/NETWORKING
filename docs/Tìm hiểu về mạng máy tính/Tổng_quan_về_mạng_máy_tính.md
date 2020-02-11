# 1.Tổng quan về mạng máy tính:
-------------------------
## a.Giới thiệu chung:
Khái niệm:
- **Truyền thông máy tính (computer comunication)**: Là quá trình chuyền dữ liệu từ thiết bị này sang thiết bị khác. Thiết bị có thể là máy tính, là các end-system (thiết bị đầu cuối) như là điện thoại di động, máy tính bảng, một thiết bị....
Hoặc truyền thông mạng máy tính cũng có thể được định nghĩa là quá trình chuyền dữ liệu, chỉ dẫn hoặc thông tin giữa hai hay nhiều máy tính hoặc thiết bị khác nhau.
- **Mạng**: Chỉ khái niện kết nối hai thiết bị lại với nhau nhằm mục đích chia sẻ thông tin.
  Khái niệm mạng còn liên quan đến những vấn đề:
  - **Giao thức truyền thông (protocols)**: Mô tả những nguyên tắc mà tất cả những thành phần của mạng cần tuân thủ để có thể trao đổi được với nhau ()
  - **Topo** (mô hình ghép nối mạng/hình trạng mạng): là cách các thiết bị nối với nhau.
  - **Địa chỉ**: Mô tả cách thức định vị một đối tượng trên mạng.
  - **Định tuyến**: (routing) mô tả cách thức chuyền dữ liệu từ thiết bị này sang thiết bị khác. (nói chung chung)
  - **Tính tin cậy**: (reliability): Tính toàn vẹn của dữ liệu khi chuyền qua mạng, là tính chính sác của dữ liệu nhận, dữ liệu nhận giống dữ liệu gửi.
  - **Khả năng liên tác**: Chỉ mức độ các sản phẩm và phần mềm và phần cứng của các hãng sản suất với nhau có thể làm việc được với nhau.
  - **An ninh** (security): tính an toàn của các thành phần của mạng.
  - **Chuẩn** (standard): Các quy tắc được thiết lập cụ thể mà cần tuân theo.
----------------------
## b.Mạng máy tính:
**Định nghĩa**: Mạng máy tính là một hệ thống thông tin liên lạc điện tử để chia sẻ tài nguyên giữa các nodes (các thiết bị có khả năng tính toán), sử dụng chung các công nghệ thông tin liên lạc. (theo wikipedia)
Thành phần: gồm nhiều thành phần các thành phần được nối với nhau theo một cách thức nào đó và sử dụng chung một ngôn ngữ. Bao gồm:
- Các thiết bị đầu cuối: (end systems): Theo thuật ngữ của mạng thì end-system là một thiết bị được kết nối tới một mạng máy tinh, hay được gọi là một (end-system) hay là (end-stations), nó được gọi như vậy vì các thiết bị này thường nằm ở RÌA của mạng, được các end-user sử dụng để tương tác với mạng.
  VD: máy tính, các thiết bị có thể kết nối vào mạng....
- Môi trường chuyền: (media): Là một môi trường vật lý sử dụng để chuyền dẫn dữ liệu.
  Được chia làm hai loại:
  - Cáp (cable): cáp soắn đôi (twisted-pair), đồng trục (coaxial), cáp quang (optic-fiber).....
  - Không dây (wireless): radio, wifi, bluetooth, bức xạ hồng ngoại (IR)(infrared).
- Giao thức (Protocols): Ngôn ngữ được sử dụng bởi các thực thể trong mạng để chúng có thể hiểu nhau. Từ cách hiểu này ta có thể định nghĩa: Giao thức là các thủ tục quy tắc chính thức đã được chấp nhận nhằm xác định hành vi của và cách trao đổi giữa các bên. Giao thức như là "keo dán" của cả hệ thống mạng.
  VD: TCP,UDP,IP,HTTP,SMTP,MSNP.....
--------------------------
## c.Phân loại mạng:
Có ba cách phân loại mạng:
- Theo diện hoạt động.
- Theo cấu hình (topo).
- Theo kiểu đường chuyền sử dụng.

**1. Theo diện hoạt động:** xác định bằng bán kính địa lý
LAN: (local area network): Liên kết các tài nguyên máy tính trong một vùng hạn chế. Bán kính từ và chục mét đến vài kilomet.
  Một số công nghệ của LAN: Ethernet, Token ring, FDDI (fiber distributed data interface).
WAN: (Wide area network): Liên kết trong một vùng địa lý rộng, bán kính có thể trên 100km.
  Một số công nghệ WAN: ISDN (intergrate service data network), SMDS (Switched multimegabit data network), ATM (Asynchronous transfer mode).
MAN: (Metropolitan AN) Mạng đô thị. 
PAN: (personal AN) mạng cá nhân.
SAN: (Storage AN) mạng lưu trữ.
GAN: (Global AN) mạng toàn cầu.

**2. Theo cấu hinh ghép nối:**
Có hai loại: 
- **Điểm tới điểm** (point to point): mỗi nút chỉ liên lạc với nút liền kề qua đường liên kết trực tiếp. Việc chuyền dữ liệu thông qua các nứt liền nhau được gọi là bridging hoặc routing.
  Có hai kiểu phổ biến:
  - **Hình cây** (Tree): Là một mô hình phân cấp gồm một nút gốc hoặc một hub, nối đến các nút hai hoặc hub mức hai, các nút hoặc hub này lại được nối tiếp đến các mức 3 và 4....
  ().
  - **Hình sao** (star): Đặc điểm chính là một hub sử lý trung tâm, hub chuyền tin cho tất cả các nút. Nếu hub dừng hoạt động thì mạng sập.
  ().
- **Điểm tới nhiều điểm** (boardcast): Gồm các nút sử dụng chung một kênh chuyền thông , khi gửi sẽ gửi đến tất cả các nứt tham gia kênh chuyền thông đó. Các máy trong mạng sẽ kiểm tra xem mình có phải đích đến của dữ liệu đó không, chỉ có máy đúng sẽ nhận thông điệp.
  Các kiểu phổ biến: 
  - **Bus**: đường chuyền chung trong ảnh được gọi là bus. (thêm ảnh).
  ()
  - **Ring**: Trong cấu trúc này tất cả nút được nối đến một vòng (một kênh dùng chung). (thêm ảnh).
  ()
  - **Vệ tinh**: (thêm ảnh)
  ()
  Mô hình: unicast, boardcast, multicast....

**3. Theo kiểu chuyền:**
Có hai kiểu chuyền thông dụng: Chuyền mạch ảo (circuit-switched) và mạng chuyển gói (packet-switched).
-  Chuyển mạch ảo: Phải thiết lập một mạch chuyền vật lý giữa nút nguồn và nút đích trước khi chuyền dữ liệu thực sự. Mạch này tồn tại trong suốt thời gian chuyền dữ liệu. Sau khi thực hiện xong việc chuyền dữ liệu kết nối được giải phóng và được cấp phát cho một đường chuyền khác. Sử dụng cách này, một đường chuyền có thể sử dụng cho nhiều phiên trao đổi thông tin khác nhau.
()
-  Chuyển mạch kiểu gói: Thông điệp đầu tiên được chia thành các gói nhỏ (packet), sau đó các packet lần lượt được chuyền tới nút nhận qua các mạng lưới các thiết bị chuyển mạch trung gian. Mỗi packet mang địa chỉ của nút đích cùng số thứ tự của mình, khi nó đến các thiết bị trung gian, nó sẽ căn cứ vào địa chỉ đích mà chọn đi theo hướng nào kế tiếp. Các packet có thể đến đích theo các con đường khác nhau. Mạng internet hiện nay sử dụng công nghệ chuyển mạch gói này.
()
-----------------------
## d. Các chuẩn của mạng:
-  Chuẩn chính thức: Được công nhận bởi những tổ chức chuẩn hóa chuyên nghiệp VD: Hiệp hội truyền thông quốc tế ITU (international telecommunication union), EIA (Electronic industry association), IEEE (institute for electrical and electronic engineers).
-  Chuẩn thực tế: Chuẩn tồn tại trong thực tế chứ không được tạo ra bởi một tổ chức nào (hầu như là các ứng dụng được sử dụng nhiều và phổ biến rồi thành chuẩn). VD: Network File System của Sun microsystems, Java cũng của Sun microsytems.
-  Chuẩn riêng của hãng: Là những quy định cụ thể của một nhà sản xuất nào đó, các đặc tả (chuẩn) này không được công khai mà chỉ được tuân theo và chấp thuận bởi những chính hãng sản xuất ra nó. VD: SNA của IBM (Kiến trúc hệ thống mạng của IBM).
-  Chuẩn hiệp hội: bản chất là chuẩn chính thức nhưng các chuẩn này được thiết kế và thỏa thuân bởi một nhóm các nhà sản xuất (tạo thành hiệp hội) với mục đích, mục tiêu chung. Các nhà sản xuất cam kết hỗ trợ các chuẩn được phát triển bởi hiệp hội.
VD: Fast Ethernet, ATM (Asynchronous Transfer Mode), Gigabit ethernet, 4K (của samsung), 8k.....


(SỐ ẢNH: 7)




