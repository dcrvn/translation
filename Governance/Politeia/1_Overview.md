# Politeia

**Politeia** đã được đề cập trong phần **Off-Chain Voting**, là việc bỏ phiếu cho các quyết định liên quan đến định hướng của dự án như chi tiêu quỹ, sửa đổi chính sách... được đưa ra thông qua các đề xuất Politeia. Bài viết hôm này chúng ta sẽ nói rõ hơn về **Politeia** nhé, bắt đầu nào!

## 1. Politeia là gì?

Politeia là một nền tảng hỗ trợ việc quản trị mạng lưới Decred.

Bạn có thể theo dõi tại [https://proposals.decred.org](https://proposals.decred.org) là nơi người dùng gửi đề xuất, theo dõi, thảo luận về các vấn đề liên quan đến quản trị Decred. Tuy nhiên việc voting không được thực hiện tại đây, vì nó yêu cầu chữ ký từ ví DCR của bạn.

Có hai loại đề xuất:

- Đề xuất kỹ thuật, định hướng cho dự án như hướng phát triển phần mềm, áp dụng một số chính sách...
- Đề xuất trong việc sử dụng quỹ **Treasury funds**, ngân sách được rút ra để tiến hành một định hướng phát triển nào đó...

## 2. Politeia hoạt động như thế nào?

Để bỏ phiếu, stakeholders phải mua tickets, trong thời gian tickets còn hợp lệ, họ có thể tiến hành bầu chọn đồng ý hoặc phản đối trên mỗi đề xuất đang mở của Politeia.

Bất kỳ ai cũng có thể đề xuất một sự thay đổi và họ cần trả một khoản phí để hạn chế khả năng spam (0.1 DCR). Ngoài ra cần trả thêm một khoản phí khi đăng ký Politeia để hạn chế lượng bình luận spam.

### - Quá trình kiểm duyệt minh bạch

Khi một đề xuất được gửi, chúng sẽ được kiểm duyệt bởi đội ngũ quản trị của Politeia, những đề xuất spam hoặc không hợp lệ sẽ bị kiểm duyệt.

Politeia được xây dựng theo quan niệm kiểm duyệt minh bạch sử dụng dcrtime. Khi người dùng đăng ký, sẽ có một cặp mật mã (pub/pri) được tạo ra, nó dùng để nhận dạng, định danh người dùng khi họ gửi một đề xuất. Nếu người dùng bị kiểm duyệt, mã này được sử dụng để chứng minh đề xuất này được gửi đi lúc nào, thời gian, cách thức...

### - Vòng đời của một đề xuất (proposal)

1. Gửi proposal

2. Đề xuất được xem xét bởi các quản trị viên Politeia. proposal spam sẽ bị kiểm duyệt.

3. Đề xuất hợp lệ sẽ xuất hiện công khai trên Politeia. Chúng được mở để thảo luận và có thể chỉnh sửa theo ý kiến chung của cộng đồng.

4. Nếu chủ đề xuất **proposal owner** không còn cho phép mọi người thảo luận, bắt đầu bỏ phiếu, quản trị viên **admin** có thể đánh dấu "Abandoned", và proposal sẽ được hiển thị tại Abandoned tab, proposal này vẫn được cho xem công khai nhưng không được chỉnh sửa, bình luận hoặc bỏ phiếu.

5. Proposal owner đề xuất cho phép bỏ phiếu để bắt đầu. Admin kích hoạt bắt đầu bỏ phiếu.

6. Thời gian bỏ phiếu trong vòng 1 tuần.

7. Khi thời gian bỏ phiếu kết thúc, Proposal chính thức có kết quả phê duyệt hay từ chối, với lượng đồng ý >= 60%

8. Khi một Proposal được phê duyệt đồng ý, công việc sẽ được tiến hành theo đề xuất đó. Proposal owner có thể tiếp tục gửi một đề xuất về ngân sách khi Proposal hoàn thành.

9. Việc thanh toán sẽ được tiến hành thủ công bởi DHG.

## 3. Politeia Data

Tất cả dữ liệu (đề xuất, bình luận, voting) sẽ được lưu trên blockchain bằng cách sử dụng dcrtime và được lưu trữ trên git. Tất cả mọi người đều có quyền truy cập và kiểm tra.

## Kết luận

Bài viết này đã đúc kết những thông tin cơ bản nhất về Politeia, hy vọng mang lại cho mọi người kiến thức bổ ích.

From: [https://docs.decred.org/governance/politeia/overview](https://docs.decred.org/governance/politeia/overview/)
