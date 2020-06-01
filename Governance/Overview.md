# Quyền quản trị mạng lưới

Các thợ mỏ **miner** sở hữu máy đào sẽ quyết định sự vận hành của mạng lưới. Thợ mỏ càng sở hữu nhiều sức mạnh máy đào, hoặc các thợ mỏ liên kết với nhau thì họ “có thể" kiểm soát cả mạng lưới. Lúc này tính phi tập trung của Blockchain sẽ không còn.

## Giải pháp của Decred là gì?

Tại thời điểm ra mắt, cơ chế đồng thuận lai PoW và PoS chính là điểm độc đáo và sự khác biệt của Decred. Nó giải quyết được vấn đề về việc quyền vận hành, quản trị cần được trao cho cả cộng đồng và chính họ mới là những người có quyền đưa ra tiếng nói cũng như thay đổi liên quan tới hệ thống.

Việc thêm cơ chế đồng thuận PoS giúp cho cả quyền quản trị của mạng lưới **governance** được chia ra cho cộng đồng.

Những người nắm giữ đủ DCR coin đều có thể mua vé **tickets** và tham gia vào việc quản trị hệ thống bao gồm việc bỏ phiếu cho **on-chain** và **off-chain**

- On-chain: Bầu chọn và duyệt cho các thợ đào khi có một coin mới được tạo ra.

- Off-chain: Bầu chọn cho những vấn đề khác của cộng đồng như việc chi tiêu quỹ **Treasury funds**, hay sửa đổi chính sách cộng động Decred ...

Những thợ mỏ với máy đào thông qua giao thức PoW sẽ tham gia vào quá trình tạo khối mới và sẽ được nhận 60% phần thưởng khối mới, những người tham gia vào quá trình bỏ phiếu PoS sẽ được nhận 30% phần thưởng khối mới, 10% còn lại được giữ bởi Decred Treasury.

### 1. On-Chain Voting

Với mỗi coin mới được tạo ra, có 5 vé được gọi ngẫu nhiên để voting, holder dùng vé này để bầu chọn, vote phê duyệt cho công việc xác thực coin mới của miner **Block Voting** đồng thời cũng có quyền biểu quyết Yes/No khi có bất kỳ đề xuất thay đổi bên trong mạng lưới Decred **Consensus Rule Voting**. Nếu vote thành công thì sẽ holdler sẽ nhận được phần thưởng

- Block Voting: Ticket để phê duyệt hoặc từ chối khi có block mới được tạo bởi công cụ khai thác PoW. Ít nhất ba trong số năm vé được gọi phải bỏ phiếu phê duyệt. Nếu đa số ticket từ chối, minner đã tạo ra block đó sẽ không nhận được phần thưởng và các giao dịch từ block đó được trả lại cho mempool.

- Consensus Rule Voting: Một thay đổi được đề xuất phải nhận được 75% sự chấp thuận thì mới có hiệu lực, nó sẽ tự động được kích hoạt mà không cần đế sự can thiệp của người nếu cử tri chấp nhận thay đổi.

### 2. Off-Chain Voting

Bỏ phiếu cho các quyết định liên qua đến định hướng của dự án như việc chi tiêu quỹ, sửa đổi chính sách ... được đưa ra thông qua các đề xuất Politeia.

Politeia voting không được ghi vào chuỗi nhưng vẫn được mã hoá nhằm ngăn chặn các cuộc tấn công.

- Politeia voting: Bất kỳ ai cũng có thể đề xuất một sự thay đổi và họ chỉ cần trả một khoản phí nhỏ cho việc xử lý kỹ thuật như ngăn chặn đề xuất rác. Thời gian bỏ phiếu kéo dài trong 1 tuần, người giữ ticket có quyền bỏ phiếu ủng hộ hay phản đối đề xuất này.

## Kết luận

Bài viết này đã đúc kết những thông tin cơ bản nhất mà bạn cần biết về quyền quản trị mạng lưới của Decred, hy vọng mang lại cho mọi người kiến thức bổ ích.

From: [https://docs.decred.org/governance/overview/](https://docs.decred.org/governance/overview)
