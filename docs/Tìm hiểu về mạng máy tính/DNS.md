
# DNS: Domain name systems.

---------------------
## I.  Nguồn gốc ra đời của DNS:
* Mỗi người được xác định theo nhiều cách: 
VD: 
- Tên (một cụm từ dễ nhớ)       
- Số CMTND (một đoạn số dài dòng nhưng lại phù hợp cho việc quản lý)
* Điều tương tự sảy ra với các thiết bị trong mạng internet
VD: 
- Host name  VD: microsoft.fr 
  * Một cụm từ viết bằng ngôn ngữ dễ nhớ ✔✔
  * đem lại ít thông tin XX chỉ có .fr cho ta biết server này ở pháp
	* Gồm nhiều kí tự dài dòng (chữ cái và chữ số) nên router khó sử lý XX
- Địa chỉ IP: 
  * một con số dài dòng có cấu trúc phân cấp ✔✔
	* Giá trị mỗi byte (VD ipV4) được đổi ra thành số thập phân (0-255) chia cách nhau bằng 1 dấu chấm
	* Duyệt địa chỉ từ trái sang phải ta được nhiều thông tin hơn về vị trí của máy tính đó trên mạng hơn ✔✔
  
=> cần một hệ thống để dung hòa giữa hai cách sác định này TỪ ĐÓ RA ĐỜI DNS: hoạt động để chuyển đổi từ tên dễ nhớ ra dòng số (địa chỉ IP).

-------------------------
## II. Hệ thống DNS:
 - ĐN: DNS là (1) một cơ sở dữ liệu phân tán được dặt trên một hệ thống giữ liệu phân cấp các máy phục vu tên nameserver và (2) giao thức thuộc tầng ứng dụng cho phép máy tính và máy chủ trao đổi thông tin, phục vụ mục đích sác định địa chi IP.
 -  DNS thường được các giao thức tầng ứng dụng khác như HTTP, SMTP, FTP.... để sác định IP từ của máy tính có tên mà người dùng cho vào.
 
### 1. Hoạt động:
  B1: Người dùng nhập tên máy chủ vào browser
  B2: DNS application chạy trên máy tính cá nhân sẽ lấy tên máy chủ trong đường link URL mà người dùng vừa nhập vào.
  B3: DNS client sẽ gửi một truy vấn (query) chứa tên máy tính tới DNS server.
  B4: DNS server nhận được query và trả lời bằng thông điệp chứa địa chỉ IP của trang web mà được yêu cầu.
  B5: DNS client nhận được thông điệp trả lời của server và lấy địa chỉ IP để truy cập trang web.
  
### 2. Một số dịch vụ khác của DNS:

- Đặt bí danh cho máy tính: (Host aliasing): Máy tính có tên phức tạp có thể đặt cho nhiều bí danh 
- Dịch vụ đặt bí danh cho mail server: (Mail server alising)
- Phân tán tải (Load distributions): Vì một trang web có thể được host trên nhiều server khác nhau (có nghĩa là nội dung như nhau nhưng địa chỉ IP khác nhau do nằm trên các server khác nhau) DNS có khả năng tác động đến địa chỉ người dùng truy cập để giảm tải cho một server nào đó.

### 3. Cơ chế hoạt động nâng cao:
- Với client dịch vụ DNS như là một "hộp đen"
- Client gửi truy vấn vào hộp đen đó và được nhận lại thông điệp trả lời chứa địa chỉ IP yêu cầu
- Với client DNS là một hệ thống đơn giản nhưng hệ thống vận hành nó lại vô cùng phức tạp.

----------------------------------
Để hiểu cách hoạt động của DNS ta xét các phương án:    

#### a. Phương án 1: Là một nameserver chứa tất cả các ánh xạ (một bản ghi DNS gồm địa chỉ Ip và tên của máy)
Thiết kế đơn giản này sẽ gặp phải một số vấn đề sau:
	- Single point of failure: khi tất cả dữ liệu đều tập trung trên cùng một điểm, thì khi server này hỏng dẫn đến hệ thống mạng internet ngưng hoạt động hoàn toàn.
	- Traffic volume: Một server duy nhất không thể sử lý được tất cả các yêu cầu cảu mọi người (các query)
	- Distance centralized database: là một server không thể ở gần tất cacr các máy tính được nên sẽ có máy kết nối chậm và sẽ có máy kết nối nhanh.
	- Maintenance: khó trong việc bảo trì.

=> không phù hợp cho một hệ thống lớn do đó phải sử dụng hệ thống phân tán.   
#### b. Phương án 2: 
 - Sử dụng nhiều name server phân tán và phân cấp trên toàn cầu.
 - Và không một server nào chứa tất cả tên của máy tính.
 
--------------------
#### c. Cơ chế hoạt động:
Phương án 2 chính là phương án được các kỹ sư lựa chọn để phát triển một hệ thống DNS hoàn chỉnh

Có 4 nameserver (nhóm các server) trong một hệ thống DNS (theo [cloudflare](https://www.cloudflare.com/learning/dns/what-is-dns/))
Hãy nghĩ hệ thống DNS như một hệ thống quản lý sách trong thư viện:
 - **DNS recursor**: DNS recursive resolver (người thủ thư) là máy chủ được thiết kế để nhận truy vấn từ client qua các ứng dụng mạng như là trình duyệt, khi nhận được truy vấn của DNS client sẽ thực hiện thêm các truy vấn khác để thỏa mã truy vấn của client.
 - **DNS rootname server (root server)**: là trên thế giới chỉ có 13 root server và hầu hết chỉ ở bắc mỹ. (như là mục lục trong thư viện). Là bước đầu tiên trong việc đi tìm bản ghi DNS. Nó thường lưu trữ:
    - Bản ghi DNS nếu bản ghi này được cache lại trên server (phụ)
		- Địa chỉ của nơi tiếp theo mà cần truy vấn để đạt được bản ghi.
 - **TLD server (top level down NS)**: (một giá sách trong thư viện) là địa điểm tiếp theo trong con đường tìm được bản ghi DNS

		* dưới TOP LEVEL là SECOND LEVEL (SLD name server)
		* Dưới SLD là các subdomians.
		* qua hệ thống đặt tên qua Domains namespace
    (Có thể đọc thêm về domain namespace ở đây: [domain namespace](https://en.wikipedia.org/wiki/Domain_Name_System#Domain_name_space)).
    
 - **Authoritative name server:** là nơi chứa các bản ghi DNS (như quyển sách chứa các định nghĩa của từ). Một máy tính sẽ báo cáo tên và địa chỉ IP của mình cho 2 authoritative server.

#### d. Các kiểu truy vấn:
- **Mô hình đệ quy:** (Truy vấn kiểu đệ quy) khi máy tính A gửi truy vấn tới máy tính B thì máy tính B sẽ thay mặt A để nhận thông điệp chứa kết quả và gửi lại về A:
- **Mô hình tương tác:** (Truy vấn theo hình thức tương tác) Khi máy tính A gửi một yêu cầu tới máy tính B nếu B không có bản ghi DNS mà A cần thì B sẽ gửi lại cho A địa chỉ của máy tính tiếp theo mà A cần truy vấn VD là máy tính C và A sẽ trực tiếp gửi truy vấn đến C.
**Nhận xét**
+ Tất cả các ví dụ ở trên đều là truy vấn theo mô hình đệ quy.
+ Bên cạnh đó DNS còn cho phép truy vấn theo hình thức tương tác ở bất cứ giai đoạn nào (name server nào) trong hệ thống DNS: 
+ Truy vấn trong hệ thống có thể vừa là tương tác vừa là đệ quy. Nhưng ngoại trừ truy vấn từ TLD (local nameserver) tới các root server thì là tương tác, bởi root name server cần phải sử lý một lượng lớn yêu cầu nên điều này làm giảm tải cho root name server.
- **Truy vấn không đệ quy:** là truy vấn mà bản ghi nằm trong cache của một name server khác.


	1. DNS caching: một đặc tính quan trọng của DNS để tăng tốc quá trình truy vấn. Mỗi lần một bản ghi DNS đi qua một nameserver thì bản ghi này sẽ được lưu trữ lại trong bộ nhớ (RAM hay có thể là bộ nhớ trong) trong một khoảng thời gian, và khoảng thời gian này được định rõ trong bản ghi DNS. Nếu có yêu cầu đúng bản ghi này thì name server sẽ sác định được ngay và trả lời được yêu cầu mà không cần truy vấn đi các server khác.


	* caching còn có thể xảy ra tại browser, hệ điều hành (stub resolver)(DNS client), recursive name server.
	* recursive name server khi có các bản ghi loại NS hoặc các bản ghi khác có thể bypass một số bước trong quá trình giải quyết query.

### 4. Bản ghi DNS: 

#### a.Bản ghi DNS:


- Bản ghi DNS (bản ghi tài nguyên) (resource record): là các ánh xạ chứa tên máy/địa chỉ IP được các name server lưu trữ.
- Một bản ghi gồm 4 trường (Name, Value, Type, TTL): 
    + Name: tên máy tính. 
		+ TTL: Time to live là thời gian tồn tại của bản ghi khi nó được lưu trữ trong các bộ nhớ đệm.
		+ Ý nghĩa của trường Name và Value phụ thuộc vào trường Type:
* Type = A thì Name sẽ là tên máy và Value sẽ là địa chỉ IP (ánh xạ tên máy địa chỉ chuẩn)
* Tpye = NS (name server) thì Name là một tên miền và Value là tên các máy trong miền đó (ánh xạ dùng để truy vấn tiếp đến các máy khác)
* Type = CNAME bản ghi này cho phép sác định đầy đủ tên của một bí danh.
* Type = MX Name là tên mail server và value là tên bí danh của mail server.
- Đặc điểm: Khi máy tính là authoritative cho một máy tính nào đó thì nó sẽ chứa bản ghi loại A của các máy tính đó, khi không phải nó sẽ chưa bản ghi loại NS và đồng thời là bản ghi loại A của các name server trong miền tên  này.


### 5. Gồm hai loại trả lời và yêu cầu nhưng về khuôn dạng thì giống nhau:

Ý nghĩa: 
	* 12 byte đầu dành cho phần tiêu đề:
	* 16 bit đầu dành cho phần định danh để sác định đây là câu trả lời cho yêu cầu nào
	* có nhiều cờ trong mỗi trường, mỗi cờ tương ứng với 1 bit
  * Cờ truy vấn: (query/reply flag): xác định thông điệp yêu cầu là (0) hay thông điệp trả lời là (1)
	* Cờ authoritative được đặt trong thông điệp trả lời khi name server là auth server của máy tính
	* Cờ mong muốn đệ quy (Recursive-desire query): được đặt khi client muốn server tiếp tục truy vấn khi không có bẩn ghi DNS cần thiết.
	* Cờ chấp nhận đệ quy (Recursive-available flag): được đặt trong thông điệp trả lười nếu name server hỗ trợ đệ quy.


