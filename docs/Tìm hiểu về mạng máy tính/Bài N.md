# Bài N: Các nguyên tắc chuyền dữ liệu tin cậy:

-----------------------------
## I. Xây dụng nguyên tắc truyền dữ liệu tin cậy:
  Phần này sẽ chình bày tổng quan dịch vụ truyền dữ liệu tin cậy. Dịch vụ này có thể nằm ở tầng giao vận, tầng ứng dụng, tầng mạng, liên kết dữ liệu. Dưới đây là các nguyên tắc chung của chuyền dữ liệu tin cậy, được xây dụng theo độ phức tạp tăng dần.
  
  Ta gọi giao thức truyền dữ liệu tin cậy này là (rdt) (reliable data transfer).
  
--------------------------
### 1. rdt 1.0: chuyền dữ liệu tin cậy trên kênh chuyền tin cậy hoàn toàn:
-  Ta sẽ mô tả trạng thái của bên nhận và bên gửi bằng kỹ thuật hữu hạn trạng thái (FSM)(Finite state machine). Đây là một cách để biểu diễn trạng thái của một máy trong quá trình chuyền.

  CHI TIẾT:
-  Phía gửi: công việc là nhận dữ iệu từ tầng trên, tạo ra gói dữ liệu (packet), và gửi gói dữ liệu lên kênh truyền. 
-  Phía nhận: Nhận gói dữ liệu, lấy dữ liêu ra khỏi gói, đưa dữ liệu lên tầng trên 
()
(Trong giao thức đơn giản này tất cả gói dữ liệu chuyển đi đã đến được tới nơi nhận, không cần thiết phải phản hồi cho phía gửi do không thể có sai xót nào trên đường chuyền).

-------------------------------
### 2. rdt 2.0: Truyền dữ liệu trên kênh chuyền bị lỗi:
  Các lỗi có thể sảy ra: Các bit bị lỗi (0 thành 1, 1 thành 0)
-  Để giải quyết tình trạng này giao thức rdt 2.0 sử dụng một kĩ thuật khác: phản hồi tích cực ACK (positive acknowledgement), và phản hồi tiêu cực NAK (negative acknowledgement). Giao thức sẽ gửi cho bên gửi một thông điệp điều khiển báo cho bên gửi biết dữ liệu nào đúng dữ liệu nào bị lỗi để yêu cầu chuyền lại. 

-  Các giao thức sử dụng phương thức này được gọi là các giao thức AQR (automatic reREQUEST): các giao thức này cần có các khả năng:
    -  Phát hiện lỗi (error correction): bằng cách sử dụng trường checksum (Sử dụng một đoạn dữ liệu thừa thêm vào các gói dữ liệu).
    -  Phản hồi (reciver feedback): Báo nhận đúng hay sai.
    -  Truyền lại (retransmission): gói dữ liệu sẽ được chuyền lại.
  CHI TIẾT:
-  Phía gửi: có hai trạng thái:
    - Trạng thái 1: phía gửi đợi dữ liệu từ tầng trên.
    - trạng thái 2: phía gửi đợi ACK NAK của bên nhận.
    (phía nhận chỉ nhận thêm khi có ACK của gói trước)
- Phía nhận: chỉ có một trạng thái. Nhận được gói, phản hồi ACK hoặc NAK phụ thuộc vào gói được gửi.
()()

----------------------
### 3. rdt 2.1: Áp dụng cách giải quyết trên:
  Giao thức rdt 2.0 vẫn còn nhược điểm: Chưa tính đến gói NAK hoặc ACK bị lỗi.
  Giải pháp:
  - Thêm trường checksum cho ACK và NAK: giải quyết được cho các kênh chuyền trung gian nhưng không thể sử lí được tình trạng gói dữ kiệu bị mất.
  - Gửi lại nếu thấy NAK hoặc ACK bị lỗi: cách giải quyết này gây ra hiện tượng trùng lặp gói dữ liệu (duplication), do bên nhận không biết gói gửi là gói gửi lại hay gửi tiếp.
  => giải pháp: Thêm một trường đánh số thứ tự cho các gói dữ liệu, bên gửi sẽ đánh số các gói dữ liệu để bên nhận chỉ cần kiểm tra số thứ tự của gói dữ liệu để biết được gói là chuyển lại hay gói mới.
  ()()
  - Đánh giá: bên gửi và bên nhận đều có trạng thái tăng gấp đôi, vì giao thức phải có khả năng biểu diễn được gói dữ liệu đã gửi (tại máy gửi), và gói dữ liệu nhận (tại bên nhận)  có thứ tự là 0 hay 1. 
  
------------------------
### 4. rdt 2.2: giao thức không áp dụng NAK:
  Thay vì sử dụng NAK để thông báo ch bên gửi gói dữ liệu gửi bị sai, bên nhận gửi lại ACK cho gói dữ liệu cuối cùng nhận đúng (giả sử là N), khi nhận được 2 ACK cho gói dữ liệu N, bên gửi sẽ biết được gói dữ liệu thứ N+1 đã bị lỗi.
   Giao thức rdt 2.2 còn sử dụng sự kiện "ba lần ACK" trùng nhau (triple ACK duplications) để khởi động lại việc gửi lại dữ liệu. (cần bởi trong mỗi gói có một trường bit thừa cho máy gửi có khả năng tự sửa lại gói dữ liệu).
   ()()

Tóm tắt: Checksum, số thứ tự biên nhận, biên nhận ACK NAK, chuyền lại....

------------------
### 5. rdt 3.0: kênh truyền  có gói dữ liệu bị lỗi và mất.
Giả sử bên gửi là nơi phát hiện mất gói dữ liệu, có hai trường hợp:
-  Gói dữ liệu bị mất trên đường chyền.
-  Gói dữ liệu đến được nhưng gói ACK phản hồi bị mất trên đường chuyền.
=> Trong cả hai tình huống bên gửi không nhận được biên nhận.
=> giải pháp: gửi lại sau một khoảng thời gian bên gửi không nhận được ACK.

  Thời gian gửi lại: phải đủ thời gian cho gói dữ liệu chuyền tới nơi nhận và gói ACK lại đến nơi gửi. Thực tế sẽ chọn một khoảng thời gian cụ thể nào đó mặc dù không đảm bảo gói dữ liệu có chuyền đến hay không.
  Để thực hiện được điều này bên gửi phải có một bộ đếm ngược (countdown timer): bên gửi phải có các khả năng
  - Khởi tạo timer.
  - Ngắt timer. (để gửi lại gói)
  - Dừng timer. (khi nhận được ACK)
  
=> gây ra hiện tượng: trùng lặp ACK=> đặt thêm một trường số thứ tự vào các gói ACK (acknowledgement number).
()()

=> Từ các giao thức trên ta đã có một giao thwusc truyền dữ liệu tin cậy hoàn chỉnh.

---------------------
## II. Giao thức truyền dữ liệu tin cậy liên tục: (pipeline).
Cốt lõi của giao thức rdt 3.0 là hành vi "dừng và chờ" (stop and wait). Mặc dù hoạt động đúng nhưng hiệu quả không cao: tầm 0.0015%
=> Giải pháp là cho phép phía gửi gửi đồng thời niều gói dữ liệu mà không cần phải trờ gói biên nhận. Kỹ thuật gửi liên tục này gọi là Pipeline (kỹ thuật đường ống). Nó đòi hỏi những yêu cầu.

-  Khoảng số thứ tự phải tăng: Vi nhiều gói dữ liệu tồn tại liên tiếp trên đường chuyền, để chánh trùng lặp gói dữ liệu. 
-  Phía gửi và nhận phải có một bộ đệm: để chứa các gói dữ liệu.
()()
=> Có hai cách tiếp cận chính ở đây: GO-back-N, SelectiveRepeat.

------------------------
### 1. GO-BACK-N:
()
Trong giao thức này ta cần chú ý một số khoảng giá trị số thứ tự:
- (0,base-1):             Số các gói dữ liệu chuyền đi và đã được biên nhận.
- (base, nextsequence-1): Ứng với các gói dữ liệu đã được gửi đi nhưng chưa biên nhận.
- (nextsequence,base+N):  Ứng với số các gói sẽ được gửi nếu dữ liệu từ tầng trên xuống.
- (base+N,..):            Chưa được sử dụng cho tới khi các gói trước được biên nhận.
  N được là khoảng số thứ tự cho phép các gói dữ liệu đã gửi nhưng chưa được biên nhận, có thể xem là một "cửa sổ" có kích thước xác định khi vận hành cửa sổ này có thể chượt trên toàn bộ khoảng số thứ tự. N thường được gọi là (window size). Giao thức GBN gọi là sliding window.

 
  
