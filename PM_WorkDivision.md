Dưới đây là **hướng dẫn chi tiết từng bước, từng mục, từng dòng** cho 4 thành viên trong vai trò Quản lý Dự án (Project Management). Toàn bộ được thiết kế cho **môi trường trường công lập, ngân sách tối đa ~50.000 USD**, và **phạm vi chỉ giữ lại những gì cốt lõi nhất**, cắt bỏ mọi hệ thống phức tạp, mở rộng đắt đỏ.

---

# NGUYÊN TẮC CHUNG CHO CẢ 4 NGƯỜI

**1. Tinh thần "Công lập - Không tiền":**
- Không dùng AWS/Azure đắt tiền. Chỉ dùng 2-3 VPS giá rẻ (khoảng 50-80 USD/tháng) hoặc server vật lý đặt tại trường.
- Không thuê thêm người ngoài. Cả dự án chỉ có đúng 4 người các bạn.
- Không mua phần mềm bản quyền đắt tiền. Chỉ dùng open-source.
- Không làm app native (iOS/Android). Chỉ làm **Web Responsive** cho sinh viên, và **Web App/PWA** cho bảo vệ trên máy tính bảng cũ.
- Không LPR (nhận diện biển số tự động) vì camera + phần mềm LPR đắt. Bảo vệ sẽ nhập biển số bằng tay hoặc dùng QR.
- Không AI, không dự đoán, không tích hợp sạc xe điện, không SMS gateway, không Public API.

**2. Phạm vi công nghệ thực tế:**
- **Phần mềm:** 1 Web Admin (cho quản lý), 1 Web Portal (cho sinh viên/giảng viên), 1 Web App cho bảo vệ (chạy trên tablet cũ), 1 Backend API đơn giản, 1 CSDL PostgreSQL.
- **Phần cứng:** Tận dụng barrier sẵn có. Mua thêm 10 đầu đọc QR/RFID giá rẻ (khoảng 50-100 USD/cái), 5 máy tính bảng cũ (200 USD/cái), 2 kiosk cảm ứng cũ (500 USD/cái), 3-5 Raspberry Pi làm gateway (100 USD/cái) nếu bãi xa mất mạng.
- **Thông báo:** Chỉ dùng Email (dịch vụ miễn phí như Mailgun tier miễn phí hoặc SMTP trường). Không SMS.

**3. Ngân sách tổng đề xuất (~48.000 USD):**
- Nhân sự 4 người (stipend/part-time/lương thấp): 30.000 USD (trải 12-18 tháng).
- Phần cứng & thiết bị: 10.000 USD.
- Cloud/VPS/Domain/SSL/Công cụ: 3.000 USD.
- Dự phòng (Contingency): 5.000 USD.

---

# 1. K – NGƯỜI LÀM PROJECT CHARTER (ĐIỀU LỆ DỰ ÁN)

## Nhiệm vụ của K
K phải viết một tài liệu duy nhất, ngắn gọn (tối đa 8-10 trang A4), nhưng **đầy đủ để bất kỳ ai đọc cũng hiểu dự án làm gì, tại sao làm, bao nhiêu tiền, bao lâu, và ai quyết định**. Đây là tài liệu "sinh ra" dự án.

## Nội dung chi tiết K phải điền vào từng mục

### Mục 1: Thông tin cơ bản
- **Tên dự án:** Hệ thống Quản lý Giữ Xe Đại học (University Parking Management System - UPMS).
- **Mã dự án:** UPMS-2026.
- **Ngày lập:** [Điền ngày tháng].
- **Người lập:** K.
- **Người phê duyệt:** [Tên giảng viên hướng dẫn / Phó Hiệu trưởng phụ trách cơ sở vật chất / Trưởng phòng Công tác Sinh viên].
- **Phiên bản:** 1.0.

### Mục 2: Tóm tắt dự án (Project Summary)
- **Vấn đề hiện tại:** Trường có 10 bãi xe, 70.000 lượt ra/vào mỗi ngày. Hiện tại dùng vé giấy, thu tiền tay, không biết còn chỗ trống hay không. Thất thoát tiền nhiều. Sinh viên phàn nàn xếp hàng lâu.
- **Giải pháp:** Xây dựng phần mềm quản lý tập trung, dùng QR/RFID để vào ra, tính tiền tự động, giám sát số chỗ trống real-time qua web.
- **Kết quả mong đợi:** Giảm thời gian vào/ra xuống dưới 10 giây, giảm thất thoát doanh thu xuống dưới 2%, quản lý được 10 bãi trên 1 hệ thống duy nhất.

### Mục 3: Mục tiêu dự án (Project Objectives) – Viết theo kiểu SMART
- **Thời gian:** Hoàn thành triển khai 10 bãi trong 10-12 tháng.
- **Phạm vi:** Phần mềm web + tích hợp 10 điểm barrier hiện có + 10 đầu đọc QR/RFID.
- **Chi phí:** Không vượt quá 48.000 USD.
- **Chất lượng:** Uptime hệ thống >95%, dữ liệu doanh thu không được sai lệch >0.5%.
- **Người dùng:** 42.000 sinh viên + 4.200 cán bộ.

### Mục 4: Phạm vi dự án (Scope) – Phần quan trọng nhất

**In-Scope (Làm):**
- Phân hệ Quản lý Người dùng & Xe: Đăng ký xe máy/xe hơi, phân loại sinh viên/giảng viên/khách.
- Phân hệ Vé & Ra/Vào: Phát vé QR/RFID, quét vào, quét ra, tính giờ, tính tiền tự động.
- Phân hệ Giá & Thanh toán: Giá xe máy khác xe hơi, giá ngày khác đêm, vé tháng cơ bản, thanh toán tiền mặt (tại bảo vệ) và chuyển khoản/ví điện tử (online).
- Phân hệ Báo cáo: Doanh thu theo ngày/tuần/tháng, số lượt xe, số chỗ trống real-time.
- Phân hệ Bảo vệ: Web app trên tablet để mở barrier thủ công, xem báo cáo shift, ghi nhận vi phạm (chụp ảnh).
- Phân hệ Quản trị: Web admin để thêm/xóa bãi, điều chỉnh giá, xem dashboard.
- Phần cứng: Lắp 10 đầu đọc QR/RFID tại 10 bãi, kết nối barrier hiện có qua relay/Raspberry Pi, 5 tablet cho bảo vệ, 2 kiosk cảm ứng cũ.

**Out-of-Scope (Không làm – Cắt giảm rõ ràng):**
- Không làm app native iOS/Android cho sinh viên (chỉ dùng web responsive).
- Không nhận diện biển số tự động (LPR). Bảo vệ nhập tay.
- Không tích hợp hệ thống ERP phức tạp của trường. Chỉ import/export file Excel/CSV nếu cần đồng bộ danh sách sinh viên.
- Không tích hợp trạm sạc xe điện.
- Không dùng AI, machine learning, dự đoán nhu cầu.
- Không SMS gateway. Thông báo qua email và thông báo trên web.
- Không hệ thống đỗ xe thông minh dẫn đường ( Indoor navigation).
- Không xây dựng mới barrier, chỉ tận dụng và điều khiển barrier cũ.

### Mục 5: Deliverables chính (Kết quả giao nộp)
1. Tài liệu Điều lệ dự án (Project Charter) – bản này.
2. Tài liệu Thiết kế CSDL & API.
3. Mã nguồn hệ thống (Backend + Web Admin + Web Portal + Web App Bảo vệ).
4. Hệ thống triển khai tại 10 bãi xe (production).
5. Tài liệu Hướng dẫn sử dụng cho Bảo vệ và Quản lý.
6. Báo cáo Tổng kết dự án (Lessons Learned).

### Mục 6: Các bên liên quan (Stakeholders)
| Bên liên quan | Vai trò | Mối quan tâm | Cách quản lý |
|---|---|---|---|
| Ban Giám hiệu / Phòng Tài chính | Sponsor | Tiền, doanh thu, minh bạch | Báo cáo tháng |
| Phòng Công tác Sinh viên | Cung cấp dữ liệu SV | Danh sách chính xác | Gửi file Excel định kỳ |
| Phòng Quản trị Cơ sở vật chất | Quản lý bãi | Vận hành ổn định, ít hỏng | Phối hợp khảo sát lắp đặt |
| Đội Bảo vệ | Người dùng trực tiếp | Dễ dùng, đỡ mệt | Đào tạo, lấy feedback |
| Sinh viên | Người dùng cuối | Nhanh, rẻ, không xếp hàng | Thông báo qua web |
| Giảng viên | Người dùng cuối | Vé tháng, ưu tiên | Thông báo qua web |
| Nhóm 4 người (K, N, HHC, H) | Thực hiện | Deadline, học hỏi, điểm số | Họp định kỳ |

### Mục 7: Ràng buộc (Constraints)
- **Ngân sách:** Tối đa 48.000 USD. Không có thêm.
- **Nhân sự:** Đúng 4 người. Không tuyển thêm.
- **Thời gian:** 10-12 tháng.
- **Kỹ thuật:** Phải dùng mã nguồn mở. Phải chạy được trên phần cứng cũ.
- **Pháp lý:** Tuân thủ bảo vệ dữ liệu cá nhân (không lưu hình ảnh khuôn mặt, chỉ lưu biển số và mã QR).

### Mục 8: Giả định (Assumptions)
- Trường cho phép lắp đặt thiết bị tại 10 bãi.
- Các bãi hiện có điện và mạng internet (wifi hoặc dây mạng).
- Barrier hiện có có thể điều khiển mở/đóng bằng tín hiệu điện (relay).
- Sinh viên và giảng viên đều có smartphone để quét QR.
- Trường cung cấp danh sách sinh viên/giảng viên định kỳ bằng Excel.

### Mục 9: Rủi ro cấp cao (High-level Risks)
1. **Thiếu kinh phí giữa chừng:** Trường cắt giảm ngân sách. *Mitigation:* Chia làm 3 giai đoạn, mỗi giai đoạn có mốc rõ ràng, chỉ chi tiền khi giai đoạn trước xong.
2. **Bảo vệ không chịu dùng công nghệ:** Họ quen thao tác tay. *Mitigation:* Thiết kế web app bảo vệ cực đơn giản (3 nút bấm), đào tạo tận tình, làm song song với cách cũ 1 tháng.
3. **Mạng internet tại bãi xa không ổn định:** *Mitigation:* Dùng Raspberry Pi làm gateway lưu trữ cục bộ, đồng bộ khi có mạng.
4. **Thay đổi yêu cầu từ lãnh đạo:** Giữa chừng đòi thêm LPR, thêm app native. *Mitigation:* Ghi rõ Out-of-Scope trong Charter, mọi thay đổi phải qua quy trình thay đổi (Change Control).
5. **Barrier cũ không tương thích:** Không có cổng điều khiển. *Mitigation:* Khảo sát kỹ trong tuần đầu, nếu không tương thích thì dùng giải pháp thay thế (ví dụ: còi báo + bảo vệ mở tay).

### Mục 10: Ngân sách tóm tắt (Summary Budget)
| Hạng mục | Số tiền (USD) | Ghi chú |
|---|---|---|
| Nhân sự 4 người (part-time/stipend) | 30.000 | 12-18 tháng |
| Phần cứng (đầu đọc, tablet, kiosk, Pi) | 10.000 | Mua mới hoặc refurbished |
| Cloud/VPS/Domain/Tools | 3.000 | 2 VPS + domain + SSL |
| Đào tạo & tài liệu | 2.000 | In ấn, cà phê họp |
| Dự phòng (Contingency 10%) | 5.000 | Phòng rủi ro |
| **Tổng** | **50.000** | **Không vượt quá** |

### Mục 11: Lịch trình tóm tắt (Summary Timeline)
- **Tháng 1-2:** Khảo sát, thiết kế, mua phần cứng thử nghiệm.
- **Tháng 3-6:** Xây dựng MVP (2 bãi: A và B).
- **Tháng 7-9:** Mở rộng 6 bãi (C, D, E, F, G, H).
- **Tháng 10-12:** Hoàn thiện 10 bãi, đào tạo, bàn giao.

### Mục 12: Tiêu chí thành công (Success Criteria)
- Hệ thống vận hành được 10 bãi, xử lý 70.000 lượt/ngày.
- Thời gian vào/ra trung bình < 10 giây.
- Thất thoát doanh thu < 2%.
- Bảo vệ sử dụng thành thạo sau 2 tuần đào tạo.
- Hệ thống uptime > 95% trong giờ cao điểm.

### Mục 13: Chấp thuận & Ký tên
- Dòng chữ: *"Tôi đã đọc và đồng ý với nội dung Project Charter này. Dự án được phép bắt đầu."*
- Chữ ký của Sponsor (giảng viên/người phê duyệt).
- Chữ ký của K (người lập).
- Ngày ký.

---

# 2. N – NGƯỜI LÀM WBS (WORK BREAKDOWN STRUCTURE)

## Nhiệm vụ của N
N phải chia nhỏ toàn bộ dự án thành các **gói công việc (Work Packages)** có thể quản lý được. Mỗi gói phải gán được cho 1 người trong nhóm 4 người, ước tính được thời gian, và có kết quả giao (Deliverable) rõ ràng.

## Nguyên tắc chia WBS
- Chia theo **deliverable**, không chia theo giai đoạn thời gian.
- Mỗi Work Package nên tốn **8-80 giờ** làm việc (tương đương 1-10 ngày của 1 người).
- Mã số phân cấp: 1.0, 1.1, 1.1.1, 1.1.2...
- Cấp 1: Dự án. Cấp 2: Nhóm lớn. Cấp 3: Gói công việc. Cấp 4: Nhiệm vụ chi tiết (nếu cần).

## Cấu trúc WBS chi tiết N phải xây dựng

### 1.0 Quản lý Dự án & Hành chính
- **1.1 Lập kế hoạch dự án**
  - 1.1.1 Viết Project Charter (K thực hiện, K phê duyệt nội bộ) -> Deliverable: Project Charter v1.0.
  - 1.1.2 Xây dựng WBS & WBS Dictionary (N thực hiện) -> Deliverable: WBS Document.
  - 1.1.3 Lập lịch trình & Gantt (HHC thực hiện) -> Deliverable: Gantt Chart.
  - 1.1.4 Thiết lập Baseline (H thực hiện) -> Deliverable: Baseline Report.
- **1.2 Quản lý họp & giao tiếp**
  - 1.2.1 Họp khởi động dự án (Kick-off) -> Deliverable: Biên bản họp.
  - 1.2.2 Họp định kỳ 2 tuần/lần (Sprint Review) -> Deliverable: Biên bản họp hàng tuần.
  - 1.2.3 Báo cáo tiến độ tháng cho Sponsor -> Deliverable: Status Report.
- **1.3 Quản lý thay đổi & rủi ro**
  - 1.3.1 Theo dõi rủi ro hàng tuần -> Deliverable: Risk Log cập nhật.
  - 1.3.2 Xử lý Change Request (nếu có) -> Deliverable: Change Log.

### 2.0 Phân tích Yêu cầu & Thiết kế Hệ thống
- **2.1 Khảo sát hiện trạng**
  - 2.1.1 Khảo sát 10 bãi xe (chụp ảnh, đo đạc, vẽ sơ đồ bãi) -> Deliverable: Site Survey Report (10 trang).
  - 2.1.2 Khảo sát barrier hiện có (mẫu, năm sản xuất, cổng điều khiển) -> Deliverable: Barrier Compatibility Sheet.
  - 2.1.3 Phỏng vấn bảo vệ trưởng & quản lý bãi -> Deliverable: User Interview Notes.
- **2.2 Thiết kế Cơ sở dữ liệu**
  - 2.2.1 Thiết kế ER Diagram (bảng Users, Vehicles, Zones, Transactions, Payments, Passes, Violations) -> Deliverable: Database Schema v1.0.
  - 2.2.2 Viết migration scripts (SQL) -> Deliverable: Flyway/Baseline SQL files.
- **2.3 Thiết kế API & Luồng nghiệp vụ**
  - 2.3.1 Định nghĩa API endpoints (REST, JSON) cho Entry, Exit, Payment, Report -> Deliverable: API Specification (Swagger/OpenAPI).
  - 2.3.2 Vẽ luồng nghiệp vụ (BPMN hoặc flowchart text): Vào ra, tính tiền, vé tháng -> Deliverable: Process Flow Document.
- **2.4 Thiết kế Giao diện (UI/UX)**
  - 2.4.1 Wireframe Web Admin (Figma hoặc giấy scan) -> Deliverable: Admin Wireframes.
  - 2.4.2 Wireframe Web Portal User -> Deliverable: Portal Wireframes.
  - 2.4.3 Wireframe Web App Bảo vệ (3 màn hình chính: Dashboard, Mở barrier, Ghi vi phạm) -> Deliverable: Guard App Wireframes.

### 3.0 Phát triển Phần mềm
- **3.1 Backend API (Node.js/Python)**
  - 3.1.1 Setup project, cấu trúc thư mục, Docker -> Deliverable: Code repo khởi tạo.
  - 3.1.2 API Authentication (JWT, phân quyền RBAC: Admin, Guard, User) -> Deliverable: Auth module.
  - 3.1.3 API Quản lý Người dùng & Xe (CRUD, import Excel) -> Deliverable: User/Vehicle API.
  - 3.1.4 API Quản lý Bãi & Chỗ trống (real-time slot count) -> Deliverable: Zone API.
  - 3.1.5 API Ra/Vào (Entry/Exit, ghi log, chống vào 2 lần không ra) -> Deliverable: Transaction API.
  - 3.1.6 API Tính tiền (Pricing Engine: xe máy/xe hơi, ngày/đêm, miễn phí giờ đầu, giới hạn ngày) -> Deliverable: Pricing API.
  - 3.1.7 API Thanh toán (ghi nhận tiền mặt, chuyển khoản, ví điện tử, vé tháng) -> Deliverable: Payment API.
  - 3.1.8 API Báo cáo (doanh thu, lượt xe, vi phạm) -> Deliverable: Report API.
  - 3.1.9 API Bảo vệ (override barrier, ghi vi phạm, xem shift report) -> Deliverable: Guard API.
  - 3.1.10 Tích hợp Email thông báo (SMTP, template email) -> Deliverable: Notification Service.
- **3.2 Web Admin (React/Vue)**
  - 3.2.1 Layout & Navigation (Sidebar, Header, Dashboard tổng quan) -> Deliverable: Admin shell.
  - 3.2.2 Màn hình Quản lý Bãi (thêm/sửa zone, công suất, giờ mở cửa) -> Deliverable: Zone Management UI.
  - 3.2.3 Màn hình Quản lý Người dùng (tìm kiếm, phân loại, khóa/mở) -> Deliverable: User Management UI.
  - 3.2.4 Màn hình Quản lý Giá (bảng giá theo giờ, vé tháng, khuyến mãi) -> Deliverable: Pricing UI.
  - 3.2.5 Màn hình Báo cáo Doanh thu (bảng, lọc theo ngày, xuất Excel/PDF) -> Deliverable: Revenue Report UI.
  - 3.2.6 Màn hình Giám sát Real-time (bản đồ 10 bãi, số chỗ trống, cảnh báo đỏ/vàng) -> Deliverable: Live Dashboard UI.
  - 3.2.7 Màn hình Quản lý Vi phạm (duyệt ảnh, phạt, kháng cáo) -> Deliverable: Violation UI.
- **3.3 Web Portal cho Sinh viên/Giảng viên**
  - 3.3.1 Trang Đăng ký/Đăng nhập (dùng mã sinh viên/email trường) -> Deliverable: Auth Portal.
  - 3.3.2 Trang Quản lý Xe cá nhân (thêm biển số, loại xe, sửa/xóa) -> Deliverable: My Vehicles page.
  - 3.3.3 Trang Mua vé tháng (chọn loại vé, thanh toán online) -> Deliverable: Pass Purchase page.
  - 3.3.4 Trang Lịch sử Giao dịch (vé đã mua, tiền đã nộp, biên lai) -> Deliverable: History page.
  - 3.3.5 Trang Nạp tiền/Ví điện tử (nạp qua ngân hàng, QR) -> Deliverable: Wallet page.
- **3.4 Web App cho Bảo vệ (PWA, responsive, chạy trên tablet)**
  - 3.4.1 Màn hình Đăng nhập (đơn giản, nhớ mật khẩu) -> Deliverable: Guard Login.
  - 3.4.2 Màn hình Dashboard Shift (số xe vào ra shift hiện tại, doanh thu shift) -> Deliverable: Shift Dashboard.
  - 3.4.3 Màn hình Mở barrier thủ công (nút bấm lớn, chọn lý do: VIP, hỏng thẻ, cứu thương) -> Deliverable: Manual Override UI.
  - 3.4.4 Màn hình Quét QR/Vé (camera tablet quét QR in hoặc trên điện thoại SV) -> Deliverable: Scan Ticket UI.
  - 3.4.5 Màn hình Ghi Vi phạm (chọn loại vi phạm, chụp ảnh, ghi biển số) -> Deliverable: Violation Capture UI.
  - 3.4.6 Màn hình Xem chỗ trống (số liệu real-time của bãi mình) -> Deliverable: Bay Count UI.
- **3.5 Cơ sở dữ liệu & DevOps đơn giản**
  - 3.5.1 Setup VPS/Server (Ubuntu, Docker, Docker Compose) -> Deliverable: Server ready.
  - 3.5.2 Setup PostgreSQL + Redis (cache) -> Deliverable: Database server.
  - 3.5.3 Setup CI/CD cơ bản (GitHub Actions build + deploy lên VPS) -> Deliverable: CI/CD pipeline.
  - 3.5.4 Backup tự động (script backup DB hàng ngày lên cloud storage miễn phí/cheap) -> Deliverable: Backup script.

### 4.0 Triển khai Phần cứng & Tích hợp
- **4.1 Chuẩn bị phần cứng**
  - 4.1.1 Mua 10 đầu đọc QR/RFID (USB/RS232) -> Deliverable: Thiết bị về kho.
  - 4.1.2 Mua 5 tablet cũ (Android, màn 10 inch) -> Deliverable: Tablet tested.
  - 4.1.3 Mua 2 kiosk cảm ứng cũ (cho khách tự đăng ký) -> Deliverable: Kiosk tested.
  - 4.1.4 Mua 3-5 Raspberry Pi 4 (8GB) + case + thẻ nhớ -> Deliverable: Pi flashed OS.
- **4.2 Lắp đặt tại bãi**
  - 4.2.1 Lắp đầu đọc tại 2 bãi MVP (A, B) -> Deliverable: Hardware installed at Zone A&B.
  - 4.2.2 Kết nối đầu đọc với Raspberry Pi, test quét thẻ/QR -> Deliverable: Signal test passed.
  - 4.2.3 Kết nối Raspberry Pi với barrier (relay module, test mở/đóng) -> Deliverable: Barrier control working.
  - 4.2.4 Lắp đặt tại 6 bãi tiếp theo (C, D, E, F, G, H) -> Deliverable: Hardware installed at 6 zones.
  - 4.2.5 Lắp đặt tại 2 bãi cuối (I, J) -> Deliverable: Hardware installed at 10 zones.
- **4.3 Cấu hình Mạng & Edge**
  - 4.3.1 Cấu hình WiFi/Ethernet cho từng bãi -> Deliverable: Network config sheet.
  - 4.3.2 Cài đặt Edge Gateway trên Pi (lưu trữ cục bộ khi mất mạng) -> Deliverable: Edge software deployed.
  - 4.3.3 Test đồng bộ dữ liệu từ Pi lên server trung tâm -> Deliverable: Sync test passed.

### 5.0 Kiểm thử, Đào tạo & Bàn giao
- **5.1 Kiểm thử**
  - 5.1.1 Unit Test các module tính tiền, thanh toán -> Deliverable: Test report.
  - 5.1.2 Integration Test (end-to-end: vào bãi -> ra bãi -> tính tiền đúng) -> Deliverable: Integration Test Report.
  - 5.1.3 UAT với 5 bảo vệ và 10 sinh viên tình nguyện -> Deliverable: UAT Sign-off.
  - 5.1.4 Load Test đơn giản (dùng script giả lập 100 request/giây) -> Deliverable: Load Test Result.
- **5.2 Đào tạo**
  - 5.2.1 Viết tài liệu HDSD cho Bảo vệ (hình ảnh, ít chữ) -> Deliverable: Guard Manual.
  - 5.2.2 Viết tài liệu HDSD cho Quản lý Bãi -> Deliverable: Admin Manual.
  - 5.2.3 Đào tạo bảo vệ tại 2 bãi MVP -> Deliverable: Training Record (biên bản).
  - 5.2.4 Đào tạo quản lý bãi dùng Web Admin -> Deliverable: Training Record.
- **5.3 Triển khai & Bàn giao**
  - 5.3.1 Go-live 2 bãi MVP (chạy song song 2 tuần) -> Deliverable: Go-live Checklist.
  - 5.3.2 Go-live 6 bãi tiếp -> Deliverable: Go-live Checklist.
  - 5.3.3 Go-live 10 bãi toàn trường -> Deliverable: Go-live Checklist.
  - 5.3.4 Bàn giao tài liệu, mã nguồn, mật khẩu cho trường -> Deliverable: Handover Document.

## WBS Dictionary (Bảng giải thích WBS)
N phải làm thêm 1 bảng giải thích cho **từng Work Package ở cấp 3** (ví dụ 3.1.1, 3.1.2...). Mỗi dòng gồm:
- **Mã WBS:** 3.1.1
- **Tên:** Setup Backend Project
- **Mô tả:** Tạo repo Git, cấu trúc thư mục, cài Express/FastAPI, Docker, kết nối DB test.
- **Deliverable:** Link repo + README.
- **Người phụ trách:** [Tên thành viên].
- **Giờ dự kiến:** 8 giờ.
- **Tiền dự kiến:** 0 (dùng tool miễn phí).

---

# 3. HHC – NGƯỜI LÀM GANTT CHART (LỊCH TRÌNH DỰ ÁN)

## Nhiệm vụ của HHC
HHC phải chuyển WBS của N thành **lịch trình có thời gian cụ thể**, xác định thứ tự công việc (trước/sau), phụ thuộc (dependencies), đường găng (critical path), và phân bổ nguồn lực 4 người. Vì không vẽ biểu đồ, HHC sẽ **mô tả bằng bảng text chi tiết** và giải thích logic lập lịch.

## Các bước HHC thực hiện

### Bước 1: Xác định thời lượng (Duration) cho từng Work Package
Dựa trên WBS của N, HHC gán số ngày/tuần cho mỗi việc. Quy ước: 1 người làm 1 việc, 4 giờ/ngày (vì part-time hoặc vừa học vừa làm).

### Bước 2: Xác định Dependencies (quan hệ trước/sau)
- **Finish-to-Start (FS):** A xong mới làm B. Ví dụ: Thiết kế CSDL xong mới viết Backend API.
- **Start-to-Start (SS):** A và B bắt đầu cùng lúc. Ví dụ: Web Admin và Web Portal có thể code song song từ tuần 3 nếu API contract đã có.
- **Finish-to-Finish (FF):** A và B phải xong cùng lúc. Ví dụ: Đào tạo bảo vệ và Go-live bãi A phải cùng ngày.

### Bước 3: Xác định Milestones (Cột mốc)
Những sự kiện có ý nghĩa, không tốn thời gian, đánh dấu giai đoạn.

### Bước 4: Phân bổ nguồn lực (4 người)
HHC phải ghi rõ **tuần này ai làm gì**, đảm bảo không giao 1 người 2 việc nặng cùng lúc.

## Nội dung tài liệu Gantt của HHC

### Phần 1: Bảng Lịch trình Tổng thể (Master Schedule)

| STT | Mã WBS | Tên công việc | Ngày bắt đầu | Ngày kết thúc | Thời lượng (tuần) | Người làm | Tiền đề (Predecessors) | Milestone |
|---|---|---|---|---|---|---|---|---|
| 1 | 1.1.1 | Viết Project Charter | Tuần 1 | Tuần 2 | 2 | K | - | M1: Charter phê duyệt (Tuần 2) |
| 2 | 1.1.2 | Xây dựng WBS | Tuần 2 | Tuần 3 | 2 | N | 1.1.1 | - |
| 3 | 1.1.3 | Lập Gantt Chart | Tuần 3 | Tuần 4 | 2 | HHC | 1.1.2 | - |
| 4 | 1.1.4 | Thiết lập Baseline | Tuần 4 | Tuần 4 | 1 | H | 1.1.3 | M2: Baseline phê duyệt (Tuần 4) |
| 5 | 2.1.1 | Khảo sát 10 bãi | Tuần 2 | Tuần 4 | 3 | K+N | 1.1.1 | - |
| 6 | 2.1.2 | Khảo sát barrier | Tuần 3 | Tuần 4 | 2 | HHC+H | 1.1.1 | - |
| 7 | 2.2.1 | Thiết kế CSDL | Tuần 4 | Tuần 6 | 3 | N | 5,6 | M3: CSDL phê duyệt (Tuần 6) |
| 8 | 2.3.1 | Định nghĩa API | Tuần 5 | Tuần 7 | 3 | K | 7 | - |
| 9 | 2.4.1 | Wireframe Web Admin | Tuần 5 | Tuần 6 | 2 | H | 7 | - |
| 10 | 2.4.2 | Wireframe Portal | Tuần 5 | Tuần 6 | 2 | HHC | 7 | - |
| 11 | 2.4.3 | Wireframe Guard App | Tuần 6 | Tuần 7 | 2 | H | 7 | M4: Thiết kế UI hoàn thành (Tuần 7) |
| 12 | 3.1.1-3.1.5 | Backend API Core (Auth, User, Zone, Transaction) | Tuần 7 | Tuần 12 | 6 | N+HHC | 8 | - |
| 13 | 3.1.6-3.1.9 | Backend API Payment, Report, Guard | Tuần 11 | Tuần 16 | 6 | N+HHC | 12 | - |
| 14 | 3.5.1-3.5.2 | Setup Server & DB | Tuần 6 | Tuần 8 | 3 | K | 7 | - |
| 15 | 3.2.1-3.2.3 | Web Admin cơ bản | Tuần 8 | Tuần 13 | 6 | H | 9,12 | - |
| 16 | 3.2.4-3.2.7 | Web Admin nâng cao (Giá, Báo cáo, Dashboard) | Tuần 12 | Tuần 17 | 6 | H | 15 | - |
| 17 | 3.3.1-3.3.3 | Web Portal (Auth, Vehicle, Pass) | Tuần 9 | Tuần 14 | 6 | K | 10,12 | - |
| 18 | 3.3.4-3.3.5 | Web Portal (History, Wallet) | Tuần 13 | Tuần 17 | 5 | K | 17 | - |
| 19 | 3.4.1-3.4.3 | Guard App Core (Login, Dashboard, Override) | Tuần 10 | Tuần 14 | 5 | HHC | 11,12 | - |
| 20 | 3.4.4-3.4.6 | Guard App (Scan, Violation, Bay Count) | Tuần 13 | Tuần 17 | 5 | HHC | 19 | - |
| 21 | 4.1.1-4.1.4 | Mua phần cứng | Tuần 3 | Tuần 6 | 4 | K+N | - | - |
| 22 | 4.2.1 | Lắp đặt 2 bãi MVP | Tuần 14 | Tuần 16 | 3 | H+HHC | 21 | - |
| 23 | 4.3.1-4.3.3 | Cấu hình Network & Edge | Tuần 15 | Tuần 17 | 3 | H | 22 | - |
| 24 | 5.1.1-5.1.2 | Unit & Integration Test | Tuần 16 | Tuần 18 | 3 | N+H | 13,16,18,20 | - |
| 25 | 5.1.3 | UAT | Tuần 18 | Tuần 19 | 2 | K+HHC | 24 | M5: UAT Pass (Tuần 19) |
| 26 | 5.2.1-5.2.4 | Đào tạo | Tuần 18 | Tuần 20 | 3 | K+H | 24 | - |
| 27 | 5.3.1 | Go-live 2 bãi MVP | Tuần 20 | Tuần 20 | 1 | Cả nhóm | 25,26 | M6: MVP Go-live (Tuần 20) |
| 28 | 4.2.2 | Lắp 6 bãi tiếp | Tuần 21 | Tuần 26 | 6 | H+HHC | 27 | - |
| 29 | 5.3.2 | Go-live 6 bãi | Tuần 27 | Tuần 27 | 1 | Cả nhóm | 28 | M7: 8 bãi vận hành (Tuần 27) |
| 30 | 4.2.3 | Lắp 2 bãi cuối | Tuần 28 | Tuần 30 | 3 | H+HHC | 29 | - |
| 31 | 5.3.3 | Go-live 10 bãi | Tuần 31 | Tuần 31 | 1 | Cả nhóm | 30 | M8: Toàn trường Go-live (Tuần 31) |
| 32 | 5.3.4 | Bàn giao & Tổng kết | Tuần 32 | Tuần 33 | 2 | K | 31 | M9: Dự án kết thúc (Tuần 33) |

### Phần 2: Critical Path (Đường găng)
HHC phải xác định và giải thích:
- **Đường găng:** 1.1.1 -> 2.2.1 (CSDL) -> 2.3.1 (API) -> 3.1.1-3.1.5 (Backend Core) -> 3.1.6-3.1.9 (Backend còn lại) -> 5.1.1-5.1.2 (Test) -> 5.1.3 (UAT) -> 5.3.1 (Go-live MVP).
- **Ý nghĩa:** Nếu bất kỳ công việc nào trên đường găng trễ 1 tuần, toàn bộ ngày go-live MVP sẽ trễ 1 tuần. Không có buffer.
- **Các công việc không nằm trên đường găng (float):** Mua phần cứng (có thể trễ 2 tuần nếu shipping chậm mà không ảnh hưởng go-live vì lắp đặt bắt đầu tuần 14).

### Phần 3: Phân bổ Nguồn lực Chi tiết theo Tuần (Resource Loading)
HHC phải vẽ/mô tả **lịch làm việc của 4 người theo từng tuần**:

**Ví dụ mẫu (Tuần 7-12):**
- **K:** 50% thời gian vào Backend API hỗ trợ (đặc biệt Auth & User), 50% loại thủ tục hành chính và đối ngoại với trường.
- **N:** 80% Backend API Core (Zone, Transaction, Entry/Exit), 20% review DB.
- **HHC:** 50% Backend API Core hỗ trợ, 50% bắt đầu Guard App.
- **H:** 80% Web Admin cơ bản, 20% setup server.

### Phần 4: Quản lý Buffer
- **Buffer dự phòng thời gian:** Mỗi giai đoạn dài có 1 tuần buffer ẩn. Ví dụ: Giai đoạn Backend dự kiến 6 tuần, nhưng HHC lập lịch 7 tuần để có buffer 1 tuần.
- **Buffer nguồn lực:** Không ai làm >30 giờ/tuần (vì đây là dự án học tập/part-time).

### Phần 5: Giả định khi lập lịch
- Mỗi người làm 4-5 ngày/tuần, 4-6 giờ/ngày.
- Không làm việc vào ngày lễ lớn (nghỉ 1 tuần vào dịp Tết/Noel nếu có).
- Nếu 1 người ốm/trễ, HHC phải có kế hoạch "Crash" đơn giản: Kéo người khác hỗ trợ hoặc cắt giảm tính năng không quan trọng (ví dụ: bỏ màn hình Dashboard đẹp, chỉ giữ báo cáo bảng).

---

# 4. H – NGƯỜI LÀM BASELINE + TIME PLAN

## Nhiệm vụ của H
H phải tổng hợp tất cả tài liệu của K, N, HHC để tạo ra **bộ Baseline (Đường cơ sở)**. Baseline là phiên bản "đóng đinh" của kế hoạch. Sau khi baseline được phê duyệt, mọi thay đổi đều phải được ghi nhận và so sánh với baseline này. H cũng viết **Time Plan chi tiết** – cách thức quản lý thời gian trong suốt dự án.

## Nội dung tài liệu của H

### PHẦN A: BASELINE (ĐƯỜNG CƠ SỞ)

#### A.1. Scope Baseline (Đường cơ sở Phạm vi)
- **Project Scope Statement:** Copy từ Project Charter của K, nhưng chi tiết hơn. Ghi rõ từng chức năng IN và OUT.
- **WBS:** Tham chiếu đến tài liệu WBS của N (phiên bản đã phê duyệt).
- **WBS Dictionary:** Tham chiếu đến bảng giải thích của N.
- **Điều kiện chấp nhận (Acceptance Criteria):** Ví dụ: "Web Admin phải hiển thị đúng số chỗ trống real-time với độ trễ < 5 giây." "Bảo vệ phải mở được barrier bằng 1 nút bấm trong < 2 giây."

#### A.2. Schedule Baseline (Đường cơ sở Thời gian)
- **Gantt Chart đã phê duyệt:** Tham chiếu đến tài liệu của HHC.
- **Ngày baseline:** Ngày 30 tháng [X] năm 2026 (ngày cả nhóm ký duyệt).
- **Các Milestone ngày cụ thể:**
  - M1: Charter phê duyệt – Ngày 15/09/2026
  - M2: Baseline phê duyệt – Ngày 30/09/2026
  - M3: CSDL phê duyệt – Ngày 15/10/2026
  - M4: UI hoàn thành – Ngày 30/10/2026
  - M5: UAT Pass – Ngày 15/02/2027
  - M6: MVP Go-live – Ngày 01/03/2027
  - M7: 8 bãi vận hành – Ngày 15/05/2027
  - M8: 10 bãi Go-live – Ngày 15/07/2027
  - M9: Kết thúc – Ngày 30/07/2027
- **Critical Path:** Liệt kê lại đường găng từ HHC.
- **Buffer quản lý:** Tổng cộng 3 tuần buffer phân tán (1 tuần cho thiết kế, 1 tuần cho dev, 1 tuần cho triển khai).

#### A.3. Cost Baseline (Đường cơ sở Chi phí) – Cực kỳ quan trọng với ngân sách nhỏ
H phải lập **S-curve mô tả bằng text** (chi tiết từng tháng):

| Tháng | Chi phí tích lũy (USD) | Nội dung chi tiêu chính |
|---|---|---|
| Tháng 1 | 3.000 | Cloud setup, mua thiết bị khảo sát, stipend tháng 1 |
| Tháng 2 | 6.000 | Mua đầu đọc QR/RFID, tablet, stipend tháng 2 |
| Tháng 3 | 10.000 | Stipend, thuê VPS năm, mua kiosk |
| Tháng 4 | 14.000 | Stipend, mua Raspberry Pi |
| Tháng 5 | 18.000 | Stipend |
| Tháng 6 | 22.000 | Stipend |
| Tháng 7 | 26.000 | Stipend |
| Tháng 8 | 30.000 | Stipend |
| Tháng 9 | 34.000 | Stipend |
| Tháng 10 | 38.000 | Stipend, chi phí đào tạo |
| Tháng 11 | 42.000 | Stipend, chi phí in ấn tài liệu |
| Tháng 12 | 46.000 | Stipend, dự phòng còn lại |
| **Tổng** | **48.000** | |

- **Cost Accounts:** Gán mã chi phí cho từng nhóm WBS:
  - CA-100: Quản lý dự án ($2.000)
  - CA-200: Thiết kế ($3.000)
  - CA-300: Phát triển phần mềm ($15.000)
  - CA-400: Phần cứng & Triển khai ($12.000)
  - CA-500: Test & Đào tạo ($6.000)
  - CA-600: Dự phòng ($5.000)
  - CA-700: Cloud/Tools ($5.000)

#### A.4. Resource Baseline (Đường cơ sở Nguồn lực)
- **Danh sách nguồn lực cố định:** 4 người, không thay đổi.
- **Bảng phân bổ % thời gian theo giai đoạn:**
  - Giai đoạn Thiết kế (Tháng 1-3): K 40%, N 40%, HHC 10%, H 10%.
  - Giai đoạn Dev MVP (Tháng 4-7): K 20%, N 40%, HHC 30%, H 10%.
  - Giai đoạn Dev Full (Tháng 8-10): K 10%, N 30%, HHC 30%, H 30%.
  - Giai đoạn Triển khai (Tháng 11-12): K 30%, N 10%, HHC 30%, H 30%.
- **Giả định nguồn lực:** Không ai nghỉ quá 2 tuần liên tiếp. Nếu nghỉ, công việc được chia cho người còn lại hoặc dời milestone.

#### A.5. Quality Baseline (Đường cơ sở Chất lượng)
- **Tiêu chí kỹ thuật tối thiểu:**
  - API phản hồi < 500ms trong điều kiện bình thường.
  - Hệ thống uptime > 95% (cho phép downtime 1.2 giờ/tuần).
  - Số lỗi nghiêm trọng (Critical) = 0 trước mỗi lần go-live.
  - Số lỗi trung bình (Major) < 5 trước go-live.
  - Tài liệu hướng dẫn bảo vệ phải có hình minh họa, không quá 10 trang.
- **Tiêu chí nghiệp vụ:**
  - Tính tiền 100% chính xác (test với 1000 scenario).
  - Không mất dữ liệu giao dịch khi mất điện/mất mạng (nhờ edge gateway).

#### A.6. Risk Baseline (Đường cơ sở Rủi ro) + Contingency Reserve
- **Top 5 rủi ro đã định lượng:**
  1. Rủi ro thiếu kinh phí giữa chừng: Xác suất 20%, Tác động 40.000 USD. Contingency: 5.000 USD.
  2. Rủi ro barrier không tương thích: Xác suất 30%, Tác động 3.000 USD (mua bộ điều khiển mới). Contingency: 1.000 USD.
  3. Rủi ro bảo vệ từ chối dùng: Xác suất 40%, Tác động delay 1 tháng. Contingency: 1 tuần buffer + chi phí đào tạo thêm 500 USD.
  4. Rủi ro mất dữ liệu: Xác suất 10%, Tác động nghiêm trọng. Contingency: Backup daily + 200 USD lưu trữ dự phòng.
  5. Rủi ro thay đổi yêu cầu (scope creep): Xác suất 60%, Tác động 2 tuần. Contingency: Quy trình Change Control nghiêm ngặt.
- **Tổng Contingency Reserve:** 5.000 USD (10% ngân sách), nằm trong tài khoản riêng, chỉ dùng khi rủi ro xảy ra và được cả 4 người đồng ý.

### PHẦN B: TIME PLAN (KẾ HOẠCH QUẢN LÝ THỜI GIAN CHI TIẾT)

#### B.1. Phương pháp theo dõi tiến độ
- **Công cụ:** Không dùng MS Project đắt tiền. Dùng **Notion/ClickUp miễn phí** hoặc **Google Sheets** để cả nhóm cập nhật % hoàn thành hàng tuần.
- **Chỉ số theo dõi:**
  - **Planned Value (PV):** % công việc dự kiến hoàn thành theo baseline.
  - **Earned Value (EV):** % công việc thực tế đã hoàn thành (dựa trên WBS).
  - **Actual Cost (AC):** Số tiền thực chi.
  - **SPI (Schedule Performance Index):** EV/PV. Nếu SPI < 0.9, dự án chậm. Nếu SPI > 1.1, nhanh hơn kế hoạch.
  - **CPI (Cost Performance Index):** EV/AC. Nếu CPI < 0.9, vượt ngân sách.

#### B.2. Lịch họp định kỳ (Meeting Schedule)
| Loại họp | Tần suất | Thời lượng | Người tham gia | Nội dung |
|---|---|---|---|---|
| Daily Standup | Hàng ngày (từ tháng 4) | 15 phút | Cả 4 người | Hôm qua làm gì, hôm nay làm gì, có bị kẹt không |
| Sprint Planning | 2 tuần/lần | 1 giờ | Cả 4 người | Chọn việc làm 2 tuần tới từ WBS |
| Sprint Review | 2 tuần/lần | 30 phút | Cả 4 + Sponsor (nếu rảnh) | Demo sản phẩm |
| Retrospective | 1 tháng/lần | 1 giờ | Cả 4 người | Cái gì tốt, cái gì cần cải thiện |
| Steering Committee | 1 tháng/lần | 30 phút | K + Sponsor | Báo cáo tiến độ, xin quyết định |

#### B.3. Quy trình cập nhật tiến độ
- **Thứ 6 hàng tuần:** Mỗi người cập nhật % hoàn thành các Work Package của mình lên sheet chung.
- **Ngày đầu tháng:** H tổng hợp SPI/CPI, so sánh với Baseline.
- **Nếu chậm < 1 tuần:** Tự điều chỉnh, làm thêm giờ cuối tuần.
- **Nếu chậm > 1 tuần:** Kích hoạt **Change Request** để xem xét cắt giảm tính năng (ví dụ: bỏ màn hình Dashboard biểu đồ đẹp, chỉ giữ báo cáo bảng Excel-like).

#### B.4. Change Control Process (Quy trình thay đổi Baseline)
- **Bước 1:** Ai phát hiện nhu cầu thay đổi (thêm tính năng, đổi thời gian, đổi ngân sách) phải điền **Change Request Form** (mẫu do H tạo sẵn).
- **Bước 2:** Họp 4 người trong 24 giờ để đánh giá tác động về thời gian, chi phí, chất lượng.
- **Bước 3:** Nếu tác động < 5% ngân sách và < 3 ngày thời gian: Cả 4 người đồng ý là thực hiện ngay, H cập nhật Baseline.
- **Bước 4:** Nếu tác động > 5% ngân sách hoặc > 3 ngày: Phải đưa lên Sponsor phê duyệt.
- **Bước 5:** Nếu đồng ý: H cập nhật Baseline, ghi vào **Change Log** (số thứ tự, ngày, nội dung, lý do, tác động, người phê duyệt).

#### B.5. Kế hoạch xử lý trễ (Schedule Recovery)
- **Fast Tracking:** Làm song song các công việc vốn dĩ nối tiếp. Ví dụ: Vừa code Backend vừa code Frontend nếu API contract đã ổn định 80%.
- **Crashing:** Tăng giờ làm. Vì chỉ có 4 người, crashing = làm thêm cuối tuần. Giới hạn: Tối đa 2 tuần liên tiếp làm thêm, tránh burnout.
- **Cutting Scope:** Nếu không kịp, cắt các tính năng "đẹp" giữ lại tính năng "sống". Thứ tự cắt:
  1. Bỏ Dashboard biểu đồ đẹp -> chỉ giữ báo cáo bảng.
  2. Bỏ tính năng nạp ví online -> chỉ giữ thanh toán tiền mặt và chuyển khoản thủ công.
  3. Bỏ Web Portal cho sinh viên -> chỉ giữ đăng ký xe qua bảo vệ/admin.
  4. Bỏ 2 bãi nhỏ nhất (I, J) -> triển khai sau.

#### B.6. Bàn giao Time Plan
H phải kết luận tài liệu của mình bằng:
- **Cam kết:** "Bộ Baseline này được cả 4 thành viên đồng ý và sẽ là thước đo duy nhất cho tiến độ, chi phí, và phạm vi của dự án UPMS."
- **Chữ ký/nhận xét:** Dòng ký tên của K, N, HHC, H, và Sponsor (nếu có).
- **Ngày hiệu lực:** Ngày Baseline chính thức có hiệu lực.

---

**Kết luận cho cả 4 người:** Các tài liệu trên phải được viết thành 4 file riêng biệt (hoặc 4 chương trong 1 báo cáo lớn), có mục lục, có số trang, có tham chiếu chéo (ví dụ: WBS của N tham chiếu đến Scope trong Charter của K; Gantt của HHC tham chiếu đến WBS của N; Baseline của H tham chiếu đến cả 3). Đây là bộ tài liệu quản lý dự án hoàn chỉnh, đủ để trình bày và đủ để thực thi.
