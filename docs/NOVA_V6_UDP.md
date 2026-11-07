# Máy chủ Nova V6 qua UDP

## Windows

Chạy trong PowerShell:

```powershell
.\mugoat-server.exe 47520 32
```

Giữ cửa sổ mở khi chơi. Chạy `ipconfig` trong cửa sổ PowerShell khác để xem IPv4 của Wi-Fi hoặc Ethernet. Hai iPhone mở **Online → Server UDP R007** trong launcher, nhập IP hoặc tên máy kèm cổng 47520, cùng tên phòng và cùng chọn PvP. Quay lại và bấm **Tự do → Chơi**. Để dùng lại relay cũ, mở mục server ở launcher và chọn **Dùng lại Nova City**.

Qua Internet, chạy server trên máy có địa chỉ UDP truy cập được. Nếu dùng PC ở nhà, router phải chuyển tiếp UDP 47520 tới PC đó và firewall phải cho phép gói tới cổng này. Nếu nhà mạng dùng CGNAT, cần một máy có IP công cộng hoặc dùng mạng riêng có định tuyến UDP giữa các thiết bị. Server mặc định không xác thực người chơi. Ai biết địa chỉ và tên phòng có thể thử tham gia.

## Linux hoặc macOS

Từ mã nguồn của Nova V6, build server bằng Rust:

```sh
cargo build --locked --release --manifest-path vendor/mugoat-r007/native-port/online-bridge/Cargo.toml --bin mugoat-server
vendor/mugoat-r007/native-port/online-bridge/target/release/mugoat-server 47520 32
```

Hai mức 32 và 64 người/phòng đã qua kiểm thử UDP loopback với client mô phỏng. Hiệu năng khi tất cả người chơi dùng voice trên Internet cần đo trên máy chủ thật.

Nguồn upstream: https://github.com/iOSVNNews/mugoat/tree/cbc1b4b675bb54687889a105a95e78d83306d7e3
