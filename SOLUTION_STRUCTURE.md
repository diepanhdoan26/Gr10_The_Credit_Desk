# The Credit Desk - Solution Structure

## Conceptual Solution Chain

**User -> Input -> Process -> Output -> User Action**

Người chơi -> các trường thông tin hồ sơ + chỉ số được tính sẵn + trạng thái room -> áp dụng quyết định, cập nhật room/danh mục, phân loại so với khoảng quyết định hợp lý, giải thích -> consequence card -> phân bổ room còn lại cho hồ sơ tiếp theo.

## Initial Required Information

> Đây là danh sách ban đầu, chưa phải bản cuối cùng. W3 sẽ xác định định nghĩa và nguồn dữ liệu.

### Thông tin của mỗi hồ sơ

- Tuổi
- Nghề nghiệp và cờ đánh dấu mức độ ổn định thu nhập
- Thu nhập hàng tháng
- Chi phí sinh hoạt
- Nghĩa vụ nợ hiện tại
- Số người phụ thuộc
- Tình trạng hôn nhân
- Ghi chú về sức khỏe
- Ghi chú về lịch sử tín dụng
- Số tiền yêu cầu vay
- Thời hạn vay

### Các chỉ số được tính sẵn và hiển thị cho người chơi

- Thu nhập khả dụng ròng (net disposable income)
- Tỷ lệ nợ trên thu nhập hiện tại (existing debt-to-income)
- Khoảng khả năng chi trả được đề xuất (suggested affordability band)

### Trạng thái room

- Tổng room
- Room còn lại

### Thông tin ẩn của mỗi hồ sơ do nhóm xây dựng

- Khoảng quyết định hợp lý (defensible decision band)
- Bộ các red flags
- Nội dung giải thích hệ quả

## Early Specification Risk Seeds

- **Income:** Là lương gross, thu nhập net hay thu nhập khả dụng ròng (sau chi phí sinh hoạt và nợ hiện tại)? Chọn một cách định nghĩa ở W3.
- **Room và limit:** Room là ngân sách tín dụng của cán bộ tín dụng trong một vòng, trong khi limit/hạn mức là hạn mức được phê duyệt cho từng khách hàng. Không được đánh đồng hai khái niệm này.
- **Red flag:** Là yếu tố khiến hồ sơ bị từ chối hoàn toàn, yếu tố làm giảm hạn mức hay yếu tố khiến phải bổ sung điều kiện? Mỗi loại sẽ có cách xử lý khác nhau trong code. Cần ghi nhận từ bây giờ.

## Core Process Type

Mô phỏng/chuyển đổi trạng thái + phân loại + giải thích.

Việc tính toán diễn ra phía sau hệ thống để tạo ra các chỉ số được hiển thị; hành động của người chơi là phán đoán chứ không phải tính toán. Đây là yếu tố giúp duy trì nguyên tắc **"judgment, not arithmetic" - phán đoán, không phải tính toán**.

## MVP Flow

Bắt đầu vòng -> Room = ví dụ 5 tỷ -> Hồ sơ 1 (các trường thông tin + chỉ số + red flags) -> Ra quyết định (Đồng ý/Giảm hạn mức/Từ chối/Yêu cầu TSBĐ/Thêm điều kiện + đề xuất hạn mức) -> Cập nhật room + danh mục -> Phân loại quyết định so với khoảng quyết định hợp lý -> Consequence card -> Hồ sơ 2 (room lúc này đã bị giới hạn hơn) -> ... -> Tổng kết cuối vòng + giải thích.

## Target, Fallback, and Out of Scope

| Phạm vi | Nội dung |
|---|---|
| **Target (W6-7)** | Track KHCN; 5 hồ sơ có liên kết với nhau; một room tín dụng chung; 5 lựa chọn quyết định; consequence card cho từng hồ sơ; tổng kết cuối vòng; triển khai dưới dạng web. |
| **Fallback** | 3 hồ sơ; 3 lựa chọn gồm Phê duyệt/Giảm hạn mức/Từ chối; consequence card; phần tổng kết ở dạng văn bản thuần; loại bỏ tài sản bảo đảm/điều kiện bổ sung. |
| **Out of scope** | Track KHDN; DSCR/BCTC được lấy trực tiếp từ báo cáo tài chính thô; người chơi tự tính toán các chỉ số; đăng ký tài khoản; bảng xếp hạng/multiplayer; badge/coin là tính năng cốt lõi; chatbot. |

## Initial Route Hypothesis

> Route không đồng nghĩa với công nghệ đã được cố định.

Sử dụng web dựa trên code - đầu vào/đầu ra tương tác có trạng thái - kết hợp với một file logic riêng, sau đó triển khai trên GitHub Pages (định dạng K62, theo ghi chú W1 của Minh).

**Phương án dự phòng:** Prototype + file logic được tài liệu hóa nếu quá trình xây dựng gặp trở ngại.

Hướng này được lựa chọn vì nó làm rõ logic chuyển đổi trạng thái; một hướng triển khai che khuất quá trình suy luận sẽ tạo ra rủi ro.

## Responsibility by Output

Shared object: `dossier -> room/portfolio state -> decision -> consequence -> next state`

| Owner | Visible output | Consumed by |
|---|---|---|
| Diệp Anh (Product) | `PROJECT_PROPOSAL.md`, chuỗi giải pháp, phạm vi quyết định, output-vs-outcome | Whole team, checkpoint |
| Hà (Content/Data) | Đặc tả hồ sơ: 5 hồ sơ, schema các trường dữ liệu, red flags được tích hợp, nội dung consequence do nhóm xây dựng | Linh, Trang, Minh, testing |
| Linh (Credit) | Phác thảo logic quyết định: hồ sơ -> khoảng quyết định hợp lý + lý do red flag + nhóm hệ quả (giả thuyết, khóa ở W4) | Minh, output, testing |
| Minh (Tech) | `SOLUTION_STRUCTURE.md`, luồng chạy MVP, repository + mục tiêu triển khai, dependency map | Whole team, checkpoint |
| Trang (Design) | Màn hình quyết định + consequence được xây dựng từ một hồ sơ thực tế -> card | User review, demo |

## README Update (Entry Point)

- **The Credit Desk - một trò chơi ra quyết định dựa trên tình huống bằng tiếng Việt, nơi sinh viên thực hành đưa ra quyết định cho vay/không cho vay có cơ sở trong điều kiện room tín dụng bị giới hạn.**
- Liên kết: `W1 problem-validation.md` -> `W2 PROJECT_PROPOSAL.md` -> `W2 SOLUTION_STRUCTURE.md`.
- "What changed after W1" -> liên kết đến revision note.

## Issue/Task Board by Output (W2)

- Dossier spec v0 (Hà) -> cần cho Linh + Trang
- Decision-logic sketch v0 (Linh) -> cần cho Minh
- Consequence-card wireframe từ một hồ sơ thực tế (Trang) -> cần cho demo
- MVP run path + repo skeleton (Minh)
- Proposal + scope lock (Diệp Anh)
