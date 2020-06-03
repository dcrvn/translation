## Simple Payment Verification (SPV)

### SPV là gì?

Simple Payment Verification (SPV) cho phép người dùng của sử dụng phần mềm ví của Decred mà không cần phải download toàn bộ blockchain Decred. Khi hoạt động ở SPV mode nó chỉ cần download toàn bộ các block bao gồm các giao dịch liên quan đến nó(Ví dụ như các giao dịch mà liên quan đến các địa chỉ ví của ví đó). Trong một trường hợp điển hình điều này có nghĩa là chỉ download khoảng 10 MB thay vì nhiều GB. Điều này làm giảm các yêu cầu phần cứng và giảm rất nhiều thời gian tải đối với các ví mới khởi tạo.

SPV được xây dựng trực tiếp bên trong của `dcrwallet CLI` - cái mà Decredition và các ví chính thức của Decred sử dụng đằng sau nó - vậy nên tất cả người dùng của các ví chính thức đều có thể  kích hoạt SPV.

## Tại sao SPV được thêm vào dcrwallet?

Các yêu cầu phần cứng để chạy Decred wallet được giảm đi rất nhiều khi hoạt động dưới SPV mode. Yêu cầu lưu trữ và download cũng giảm bởi thay vì download toàn thể  blockchain, một SPV wallet sẽ chỉ download các block mà bao gồm các giao dịch liên quan thôi, và đối với các block khác trong chuỗi sẽ chỉ được đánh dấu là đã download. Số  lượng của sức mạnh xử lý được yêu cầu được giảm bởi vì thiết bị chạy SPV wallet sẽ chỉ xác thực proof-of-work và chuỗi header thay vì xác thực mỗi giao dịch trong mỗi block và đảm bao các nội dung trong block là thích hợp với các header.

Giống như kết của của việc giảm các yêu cầu, Decred wallet có thể  hoạt động trên một bộ các thiết bị rộng hơn - đặc biệt là các thiết bị di động. Smartphone và tablet thường bị giới hạn ở ít nhất một trong các trường hợp dung lượng CPU, dung lượng lưu trữ hoặc dung lượng tải xuống, và các hệ điều hành di động giới hạn số lượng các tiến trình nền (background work processing) mà mỗi một ứng dụng có thể thực hiện, cái mà khiến cho việc chạy full node không thực tế hoặc không khả thi.

Một lợi ích khác của SPV là giảm vô cùng nhiều thời gian cho một wallet mới có thể hoạt động được, cải thiện vô cùng lớn trải nghiệm người dùng.

## SPV hoạt động thế nào?

Mỗi khi một block được thêm vào blockchain Decred là 180 byte dữ liệu dành cho block header. Block header miêu tả thông tin chính về block bao gồm hash của block, Merkle root (tổng số  giao dịch hash trong block), và lần tính toán này bởi proof-of-work của miner(thợ đào). Một bộ lọc được xác định trước cũng được tạo cho mỗi block, dựa trên tất cả các giao dịch bên trong block.

Khi một SPV wallet khởi tạo nó sẽ kết nối đến mạng lưới của Decred sử dụng kết nối ngang hàng(peer-to-peer), và nó sẽ download tất cả các header và bộ lọc. Nó sau đó sẽ xác thực chuỗi header để đảm bảo rằng chuỗi và proof-of-work của nó là hợp lệ. Một khi điều này hoàn thành, wallet sẽ sử dụng các bộ lọc để địch danh một cách cục bộ block nào bao gồm các giao dịch của wallet đó mà không cần tải lên bất cứ dữ liệu bí mật nào đến các node. Wallet có thể sau đó sử dụng mạng ngang hàng để download các block đó, quét chúng cho các giao dịch liên quan và chọn chúng để cập nhật các lịch sử giao dịch cá nhân và dư lượng của nó.

## Điều này khác với một “light” wallet như thế nào?

Các “Light” wallet ví dụ như Exodus hoặc Atomic đã đem lại một số lợi ích của một SPV wallet - ví dụ: các wallet này cho phép gửi và nhận các giao dịch của Decred với thời gian bắt đầu tối thiểu và không cần download toàn bộ blockchain. Light wallet chắc chắn cung cấp rất nhiều tiện lợi nhưng thường có những hậu quả tinh tế vì chúng phụ thuộc vào API được cung cấp bởi một dịch vụ tập trung:

Light wallet phụ thuộc vào một dịch vụ từ xa để theo dõi các ví được sở hữu và cung cấp các thông báo khi các giao dịch được nhận bởi các địa chỉ. Các thông báo có thể bị bỏ lỡ hoặc đôi khi không chính xác.

Người dùng thường được yêu cầu để upload một public key đến máy chủ tập trung nên nó nhận thức tất cả các địa chỉ mà nó sở hữu, có khả năng xâm phạm quyền riêng tư của người dùng.

Light wallet không hề xác thực thông tin mà chúng nhận được bằng việc kiểm tra blockchain trực tiếp -  chúng phải tin tưởng mù quáng vào thông tin mà máy chủ tập trung cung cấp.

Những lo ngại này không áp dụng cho SPV wallet vì chúng kết nối trực tiếp với phi tập trung, mạng ngang hàng của Decred. Chúng không upload dữ liệu bí mật đến các node từ xa và chúng khám phá các giao dịch của chúng bằng việc kiểm tra trực tiếp blockchain.

## Có nhược điểm nào không?

SPV không hỗ trợ việc voting wallet. Voting wallet có trách nhiệm để bỏ phiếu cho tính hợp lệ của block cuối cùng, và wallet không thể chắc chắn tính hợp lệ trừ phi nó xác thực toàn thể blockchain dẫn đến block đó. Nó là khả dĩ để mua các ticket và phân phối quyền bỏ phiếu cho một đơn vị cung cấp dịch vụ bỏ phiếu (Voting Service Provider). Xin lưu ý rằng nếu VSP không thu hồi vé bị bỏ lỡ, nó không thể thu hồi ticket bị mất cho đến khi đạt đến độ sâu xác nhận của ticket hết hạn.

SPV wallet chỉ download các block mà có các giao dịch liên quan đến các địa chỉ của nó, cái mà có thể  có tiềm năng tiết lộ thêm một số thông tin  về ví đó nhiều hơn nếu nó download mỗi block. Điều này chỉ làm giảm sự riêng tư, nhưng dù sao nó cũng giảm. Điều này có thể  giảm nhẹ bằng các download các block từ nhiều `peer` khác nhau nên không một `peer` nào có khả năng thấy toàn bộ các block được download bởi ví đó. Ngay cả khi một người quan sát thụ động trên mạng lưới có khả năng để xem block nào được download bởi một wallet, chúng không có khả năng để định danh giao dịch nào trong block đó là liên quan.

Các wallet hoạt động trong SPV mode chỉ có thể xác thực các block header mà chúng download và không là các bộ lọc. Điều này khiến cho  tấn công “false-negative” trở nên khả thi, theo đó một `peer` độc hại mà biết một wallet đang đợi cho một giao dịch riêng biệt sẽ có thể gửi cho wallet một bộ lọc giả cái mà không bao gồm giao dịch trên, kết của là wallet sẽ không download block đó và do đó không nhận thức rằng giao dịch tồn tại. Giao dịch này sẽ vẫn được thấy bởi các node và wallet được xác thực toàn bộ, và nó sẽ vẫn xuất hiện trên trình block explorer. Một cách để ngăn trặn lỗ hổng này là thêm vào hash của bộ lọc một phần của block header mà PoW đã xác thực, cho phép SPV wallet dễ dàng kiểm tra tính xác thực của các bộ lọc mà không phải download block của chúng. Một đề xuất để làm thay đổi này đã được đề nghị, tuy nhiên một hard fork là được yêu cầu để tạo sự thay đổi này cho định dạng block header. Một bối cảnh “false-positive” là không khả thi. Nếu một node độc hại cung cấp một bộ lọc giả mà bao gồm một giao dịch không tồn tại, wallet sẽ đơn giản download toàn bộ block, so sánh nó với bộ lọc và khám phá ra rằng bộ lọc đó không thành thật.

## Tôi sử dụng SPV như thế nào?

dcrwallet CLI

Để kích hoạt SPV mode trong dcrwallet đơn giản cung cấp cờ `--spv` khi bắt đầu tiến trình. Cũng có một tùy chọn `--spvconnect` cái mà 
vô hiệu hóa việc tìm kiếm các địa chỉ peer và cho phép bạn chỉ định IP của một full node mà bạn muốn đồng bộ từ đó.  `--spvconnect` có thê chỉ định nhiều lần để đồng bộ từ nhiều peer khác nhau.

Decrediton

Khi Decrediton khởi chạy lần đầu tiên, một màn hình chuyên dụng được hiển thị trong trình hướng dẫn thiết lập để hỏi bạn có muốn bật chế độ SPV không.

Nếu Decrediton đã được sử dụng trước đó, nó là khả thi để thay đổi SPV mode thông qua tab setting. Cũng có một mục nhập “SPV Connect” ở trong tab này, cái mà sẽ cho phép bạn chỉ định địa chỉ IP của một full node mà bạn muốn đồng bộ.