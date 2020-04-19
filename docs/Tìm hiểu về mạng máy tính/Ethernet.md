# Ethernet:
## 1. Khái niệm cơ bản của Ethernet:
- Ethernet là gì: 
Ethernet là một loạt các công nghệ mạng và hệ thống được sử dụng trong các mạng cục bộ (LAN), nơi các máy tính được kết nối trong một không gian vật lý chính.

- Lịch sử ra đời: 
Ethernet được phát triển bởi công ty Xerox PARC vào khoảng những năm 1973 và 1974. Bob Metcalfe  đã viết một bản ghi nhớ mô tả hệ thống mạng Ethernet mà ông đã phát minh ra để kết nối các máy trạm tiên tiến, cho phép gửi dữ liệu cho nhau và cho các máy in laser tốc độ cao.

Bản ghi nhớ Ethernet của Bob Metcalfe vào năm 1973 mô tả một hệ thống mạng dựa trên một thử nghiệm trước đó trong mạng được gọi là mạng Aloha Và còn một hệ thống khác là slotted Aloha.

Cuối năm 1972, Metcalfe và các đồng nghiệp Xerox PARC của ông đã phát triển hệ thống Ethernet thử nghiệm đầu tiên để kết nối Xerox Alto (máy tính đầu tiên của hãng có bộ sử lý đồ họa). Hệ thống này được đặt tên là Alto Aloha Network. 

Vào năm 1973, Metcalfe đã đổi tên thành "Ethernet, 'để làm rõ rằng hệ thống này có thể hỗ trợ bất kỳ máy tính nào không chỉ Altos, và chỉ ra rằng các cơ chế mạng mới của anh ta đã phát triển vượt ra ngoài hệ thống Aloha.

Năm 1976, Metcalfe đã vẽ sơ đồ sau (Hình 1.1), ... để trình bày về hệ thống Ethernet lần đầu tiên. Nó được sử dụng trong bài trình bày của ông trước Hội nghị máy tính quốc gia vào tháng 6 năm đó.

Cuối năm 1977, Robert M. Metcalfe, David R. Bogss, Charles P. Thacker và Butler W. Lampson đã nhận được bằng sáng chế 4,063,220 của "Ethernet Hệ thống chia sẻ dữ liệu đa điểm với khả năng phát hiện xung đột".

## 2. Các đặc điểm của Ethernet:
- Điểm mạnh của Ethernet so với các công nghệ khác:
  - Đơn giản để cài đặt và quản lý.
  - Giá thành rẻ.
  - Tính liên tác cao.
  - Linh hoạt và có khả năng mở rộng.
  
- Các loại cáp được sủ dụng trong ethernet:
-------------------------------------------------------
  - Cáp đồng trục (Coaxial): 
thường được viết tắt là coax, bao gồm một dây duy nhất được bao quanh bởi lớp cách nhiệt, lớp kim loại và vỏ nhựa. Lớp kim loại giúp bảo vệ chống nhiễu điện từ (EMI), có thể gây ra suy giảm, giảm cường độ và chất lượng của tín hiệu. EMI có thể được tạo ra bởi nhiều nguồn khác nhau, chẳng hạn như chấn lưu ánh sáng huỳnh quang, lò vi sóng, điện thoại di động và máy phát vô tuyến điện.

Theo đường dây:
- Thinnet: 
- Thicknet: 

Thicknet có bán kính to hơn, nhiều lớp vỏ hơn hỗ trợ đường dây dài hơn, nhưng lại không linh hoạt bằng thinnet, bởi vậy khó sử lý hơn.

Thicknet sử dựng vampier tap để kết nối thiết bị tới đường dây vật lý, còn thinnet sử dụng BNC. 
() () 
Coax thường được sử dụng để triển khai truyền hình cáp đến nhà và doanh nghiệp.

--------------------------------------------------------------------------------
 - Cáp soắn đôi (Twisted-pair).
 
Cáp xoắn đôi gồm hai hoặc bốn cặp dây đồng trong nhựa vỏ bọc. Các dây trong một cặp xoắn quanh nhau để giảm nhiễu xuyên âm (Crosstalk), một dạng EMI xảy ra khi tín hiệu từ một dây bị nhiễu hoặc gây nhiễu tín hiệu trên dây khác. Twisted-cặp là cáp Ethernet phổ biến nhất.


Có một số loại cáp xoắn đôi, được xác định bằng số xoắn trên mỗi inch của cặp đồng:

Category 3 hay Cat3 - ba vòng soắn mỗi inch.
- Cat5  - năm vòng mỗi inch.
- Cat5e - năm vòng mỗi inch. các cặp còn được quấn quanh nhau.
- Cat6  – sáu vòng mỗi inch, có tăng khả năng cách điện. 
- Cat7: Tương tự. 
()


--------------------------------------------------------------------------
 - Cáp quang (fiber-optic): Sử dụng ánh sáng để chuyền dẫn tín hiệu. Ethernet hỗ trợ hai chuẩn:
  - Sợi Singlemode - bao gồm một lõi thủy tinh rất nhỏ, chỉ cho phép một tia hoặc chế độ ánh sáng để truyền qua nó. Điều này làm giảm đáng kể sự suy giảm và phân tán tín hiệu ánh sáng, hỗ trợ cao băng thông trên khoảng cách rất dài, thường được đo bằng km.
  - Sợi muiltimode - bao gồm lõi lớn hơn, cho phép nhiều chế độ của ánh sáng để đi qua nó. Đa chế độ chịu sự phân tán lớn hơn singlemode, kết quả trong khoảng cách được hỗ trợ ngắn hơn.
Sợi Singlemode yêu cầu thiết bị điện tử chính xác hơn multimode, và do đó đắt hơn đáng kể Sợi đa chế độ thường được sử dụng cho tốc độ cao kết nối trong trung tâm dữ liệu.



















