# LAB1 – Examining SSH & Telnet in Wireshark

- NGUYỄN TẤN TÀI
- 1150080115
- 11CNPM2

## Nội dung đã thực hiện
- Dựng mô hình Packet Tracer: Router 1841 (10.0.0.1 – Server), PC3 (10.0.0.2 – Client), PC4 (10.0.0.3 – Attacker), Switch 2960.
- Cấu hình Telnet trên Router: `line vty 0 4`, `password 14520123`, `login`, `transport input telnet`.
- PC3 telnet tới `10.0.0.1` thành công → vào `Server>`.
- Quan sát gói TELNET bằng Simulation Mode (Packet Tracer không hỗ trợ Wireshark tích hợp).
- PC4 ping được PC3 nhưng không bắt được lưu lượng Telnet do switch chỉ forward unicast đúng port.

## Kết quả
- Telnet hoạt động, truyền dữ liệu plaintext → không an toàn.
- SSH mã hóa payload → an toàn hơn Telnet.
- Máy Attacker trong Packet Tracer không mô phỏng được MITM thực tế.

## Lưu ý để kiểm tra
- Chạy lại: mở file `.pkt` → từ PC3 gõ `telnet 10.0.0.1` → password `14520123`.