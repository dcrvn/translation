# Proof-of-Work (PoW) Mining

## 1. Giới thiệu

Proof-of-work mining hay được gọi là bằng chứng công việc **POS** là một thuật toán đồng thuận nhằm đảm bảo các trao đổi trong mạng lưới blockchain được hoạt động ổn định và chính xác. Nó hoạt động dựa trên sức mạnh phần cứng, tốc độ mạng để xác nhận các giao dịch, tạo ra các block mới và giúp hình thành nên chuỗi block lớn trong hệ thống.

Khi một khối hợp lệ được tạo ra thành công, miner sẽ nhận được phí giao dịch từ tất cả giao dịch trong khối đó và phần thưởng của một block mới được tạo ra. Phần thưởng block sẽ bị giảm theo hệ số 100/101 sau 6,144 blocks (~21.33 ngày).

Khi proof-of-stake tickets được gọi để voting, họ có khả năng tước lấy phần thưởng từ miner của block được khai thác trước đó nếu trong trường hợp block này không hợp lệ, ví dụ block này là empty khi có giao dịch đang chờ xử lý ở mempool.

Decred sử dụng BLAKE-256 để hash, cũng có thể sử dụng GPUs, tuy nhiên kể từ khi được ra mắt, độ khó PoW đã trở nên đủ cao khiến việc khai thác GPU không mang lai hiệu qủa cao.

## 2. Solo Mining or Pool Mining

### - Solo Mining

Tốc độ hash của mạng lưới Decred thường lên đến 10,000Gh/s, nên khai thác đơn lẻ thường không được khuyến khích.

### - Pool Mining

Khai thác theo nhóm là tập hợp của các thợ mỏ **miner**, mỗi miner sẽ đóng góp sức mạnh (Hashrate hay Hashpower) để cùng khai thác các block và cùng chia sẻ lợi nhuận theo tỷ lệ đóng góp. Bạn có thể kiếm được lượng phần thường ổn định thay vì tiêu chí "có tất cả hoặc không có gì" của solo mining.

## 3. Đăng ký Pool Mining

Đề xuất một số Pool Mining:

- [BeePool](https://beepool.org/)
- [F2Pool](https://www.f2pool.com/)
- [Poolin](https://www.f2pool.com/)
- [UUpool](https://uupool.cn/dcr/)
- [Luxor](https://mining.luxor.tech/decred)
- [Coinmine](https://www2.coinmine.pl/dcr/)
- [Suprnova](https://dcr.suprnova.cc/)

Tất cả các nhóm đều hoạt động ít nhiều giống nhau, bạn có thể đăng ký nhiều pool khác nhau và tìm pool nào phù hợp với mình nhất.

## 4. GPU Drivers/Software

GPU Drivers là nơi chứa những thư viện cần thiết để khai thác. Nếu gặp khó khăn trong khi chạy phần mềm, bạn có thể cài đặt lại và đặc biệt kiểm tra thư viện OpenCL (AMD) or CUDA (NVIDIA) đã được chọn hay chưa.

## 5. Phần mềm khai thác

### - Official Decred Miner (gominer)

Official Decred Miner là công cụ khai thác được phát triển và hỗ trợ bởi Decred team. Đây được xem là phần mềm dễ sử dụng vì vậy được khuyến khích cho tất cả người dùng.

Bạn có thể tải: [https://github.com/decred/decred-binaries/releases/tag/v1.0.0](https://github.com/decred/decred-binaries/releases/tag/v1.0.0).
Vui lòng chọn đúng hệ điều hành, cũng như phiên bản GPU.
Click vào link [gominer Pool-Mining
](https://docs.decred.org/mining/proof-of-work/pool-mining/gominer/) để xem hướng dẫn chi tiết hơn nhé.

### - Một số phần mềm khác

- cgminer: Đây là công cụ khai thác cho **AMD** GPUs khá phổ biến trong việc mining nhiều loại coin khác nhau. Tui nhiên nó khó sử dụng hơn Gominer.
- ccminer: Đây là công cụ khai thác cho **NVIDIA** GPUs khá phổ biến trong việc mining nhiều loại coin khác nhau. Tui nhiên nó khó sử dụng hơn Gominer.
- sgminer: Sử dụng cho máy có card đồ họa **AMD** và hệ điều hành Windows.

## 6. Chạy phần mềm

- Tải, giải nén và cài đặt.
- Open a command prompt to that path (todo)
- Thiết lập bằng cách thực hiện theo các hướng dẫn Pool Mining.
- Chạy phần mềm.

## Kết luận

Trên đây là những thông tin cơ bản nhất việc khai thác DCR, hy vọng mang lại cho mọi người kiến thức bổ ích.

From: [https://docs.decred.org/mining/overview](https://docs.decred.org/mining/overview/)
