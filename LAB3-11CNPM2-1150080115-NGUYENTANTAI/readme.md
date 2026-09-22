# LAB3 – Nhận diện và ứng phó các mối đe dọa đến an toàn thông tin

## Thông tin sinh viên
- **Họ và tên:** Nguyễn Tấn Tài
- **MSSV:** 1150080115
- **Lớp:** 11CNPM2
- **Môn:** An toàn bảo mật hệ thống thông tin

## Tên bài Lab
Lab3 – Identifying and Responding to Information Security Threats

## Phiên bản môi trường
- **Máy ảo:** Windows Server 2025 Datacenter Evaluation, OS Build 26100.1742
- **Nền tảng ảo hóa:** VMware Workstation, Network Adapter = Host-only
- **Python:** 3.13.15
- **Wireshark:** 4.6.8
- **Npcap:** 1.89
- **Sysmon:** 15.22
- **Autoruns:** 14.3
- **Process Explorer:** 17.14
- **Defender:** AntivirusEnabled = True, RealTimeProtectionEnabled = True

## Cách dựng môi trường
1. Tạo VM Windows Server 2025 trên VMware Workstation, cấu hình Network Adapter = Host-only.
2. Cài Python 3.13, Wireshark 4.6.8 và Npcap 1.89.
3. Tải bộ Sysinternals (Sysmon, Autoruns, Process Explorer) từ download.sysinternals.com.
4. Giải nén gói `LAB3_Threats_Assets.zip` vào `C:\LAB3`.
5. Tạo thư mục `C:\LAB3\Evidence` để lưu bằng chứng.

## Các tình huống đã thực hiện

| Tình huống | Nội dung | Kết quả |
|-----------|----------|---------|
| TH1 | Risk Register + phân loại 5 nguồn đe dọa | PASS |
| TH2 | EICAR + Defender detection/quarantine | PASS |
| TH3 | Password attack + Event Log 4624/4625/4648 | PARTIAL (thiếu 4624 do runas lỗi) |
| TH4 | Persistence lành tính + HTTP listener 127.0.0.1:8080 | PASS |
| TH5 | Sniffing HTTP loopback (HTTPS bỏ qua) | PASS |
| TH6 | DoS local test + DDoS dataset + Mail bombing analysis | PASS |
| TH7 | Phishing offline + Social Engineering classification | PASS |
| Cleanup | Xóa persistence, listener, lab3user; verify Defender | PASS |

## Bằng chứng đã thu thập
- Ảnh chụp: H1–H11 (đã chèn vào báo cáo Word).
- Log/output: thư mục `evidence/`.
- Hash SHA-256: `evidence_sha256.csv`.

## Lỗi gặp phải và cách khắc phục
1. **Python không vào PATH** → dùng đường dẫn đầy đủ `C:\Users\motha\AppData\Local\Programs\Python\Python313\python.exe`.
2. **runas không nhận password** → dùng `net use` với password sai để sinh event 4625.
3. **Autoruns không hiện LAB3_Run_Demo** → dùng PowerShell output (Get-ItemProperty + Get-ScheduledTask) làm bằng chứng thay thế.
4. **Process Explorer bị đứng** → chờ 30 giây hoặc dùng PowerShell để xác minh PID.

## Lưu ý khi kiểm tra
- File báo cáo: `11CNPM2-LAB3_1150080115-NguyenTanTai.docx`
- Ảnh chụp trực tiếp từ VM, không dùng ảnh của người khác.
- Không upload installer, executable Sysinternals/Wireshark/Python hoặc file bị Defender quarantine.
- Không chứa mật khẩu, token, email thật hoặc dữ liệu cá nhân.

-Evidence nằm trong thư mục `evidence/`.