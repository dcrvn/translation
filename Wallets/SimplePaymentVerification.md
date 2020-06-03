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

SPV does not support voting wallets. Voting wallets have the responsibility to vote on the validity of the last block, and a wallet cannot be sure of the validity unless it fully validates the whole blockchain leading up to that block. It is possible to purchase tickets and allocate the voting rights to a Voting Service Provider. Be aware that if a VSP fails to revoke a missed ticket, it is not possible for an SPV wallet to revoke the missed ticket until it has reached the confirmation depth of an expired ticket.

SPV wallets only download blocks which have transactions related to their owned addresses, which could potentially reveal more information about the wallet than if it downloaded every single block. This only presents a very minor decrease in privacy, but it is a decrease nonetheless. This can be mitigated by downloading blocks from multiple peers so no single peer is able to see the full list of blocks downloaded by a wallet. Even if a passive observer on the network is able to see which blocks are downloaded by a wallet, they are not able to identify which transactions in those blocks are relevant.

Wallets operating in SPV mode are only able to validate the block headers they download and not the filters. This makes a “false-negative” attack possible, whereby a malicious peer that knows a wallet is waiting for a particular transaction could send the wallet a fake filter which does not include the transaction, resulting in the wallet not downloading the block and so not becoming aware of the transactions existence. This transaction would still be visible to all fully validating nodes and wallets, and it will still appear in the block explorer. One way to prevent this vulnerability is to add the hash of the filter into the part of the block header that is PoW validated, enabling SPV wallets to easily check the validity of the filters without having to download their blocks. A proposal to make this change has already been suggested, however a hard fork will be required to make the required change to the block header format. A “false-positive” scenario is not possible. If a malicious node provides a fake filter which includes a non-existent transaction, the wallet will simply download the full block, compare it to the filter and discover that the filter is not genuine.

How do I use SPV?
dcrwallet CLI
To enable SPV mode in dcrwallet simply provide the --spv flag when starting the process. There is also an optional --spvconnect flag which disables DNS seeding and allows you to specify the IP of a full node you wish to sync from. --spvconnect can be specified multiple times to sync from multiple peers.

Decrediton
When Decrediton is started for the first time, a dedicated screen is displayed during the setup wizard which asks if you would like to enable SPV mode.

If Decrediton has already been used before, it is possible to change to SPV mode through the settings tab. There is also a “SPV Connect” textbox on this tab, which will allow you to specify the IP address of a full node you wish to sync from.