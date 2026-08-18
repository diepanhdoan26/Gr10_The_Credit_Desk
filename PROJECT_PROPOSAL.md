# The Credit Desk - Project Proposal

## Problem Direction

Sinh viên năm 3-4 ngành Tài chính và Ngân hàng FTU đang chuẩn bị cho các vị trí tín dụng/quản trị rủi ro có thể học thuộc lý thuyết thẩm định, nhưng chưa từng thực sự đưa ra quyết định cho vay/không cho vay. Khoảng cách nằm ở khả năng phán đoán trong điều kiện bị giới hạn, trong khi hiện chưa có công cụ luyện tập bằng tiếng Việt, miễn phí và dành cho sinh viên Việt Nam nào phù hợp. Finsimco thì có phí, chỉ bằng tiếng Anh và hướng đến đối tượng doanh nghiệp.

## Target User and User Task

- **Người dùng:** Sinh viên năm 3-4 ngành Ngân hàng/Tài chính tại FTU, có kiến thức lý thuyết ở mức đã học qua các môn chuyên ngành nhưng chưa có kinh nghiệm thực hành thẩm định, đang hướng tới các công việc trong lĩnh vực tín dụng/quản trị rủi ro.
- **Nhiệm vụ:** Với một hồ sơ khách hàng, người chơi phải quyết định có cho vay hay không, cho vay bao nhiêu và với những điều kiện nào, trong bối cảnh room tín dụng chung bị giới hạn - bằng cách đọc hồ sơ, phát hiện các dấu hiệu cảnh báo (red flags) và bảo vệ/lý giải cho quyết định của mình.

## Desired User Outcome

Người chơi có thể tự tin và có cơ sở để lập luận khi đưa ra quyết định tín dụng, qua đó thu hẹp khoảng cách giữa lý thuyết và khả năng phán đoán thực tế.

## Product Statement

The Credit Desk là một trò chơi ra quyết định dựa trên tình huống bằng tiếng Việt (scenario-decision game), tập trung vào khách hàng cá nhân (KHCN). Người chơi vào vai cán bộ tín dụng, phân bổ một room tín dụng cố định cho nhiều hồ sơ khách hàng. Sau mỗi quyết định, người chơi nhận được một thẻ giải thích hệ quả (consequence card), cho biết quyết định đó có hợp lý/có thể bảo vệ được hay không và tại sao.

## Main Output

Sau mỗi hồ sơ, hệ thống trả về một decision-consequence card, bao gồm:

1. Quyết định có nằm trong khoảng quyết định hợp lý/có thể bảo vệ được hay không:
   - Trong phạm vi (in-range)
   - Quá chặt (too tight)
   - Quá nới lỏng (too loose)
   - Đáng lẽ phải từ chối (should have rejected)
2. Thay đổi trạng thái sau quyết định:
   - Room tín dụng đã sử dụng
   - Room tín dụng còn lại
   - Mức thay đổi của rủi ro danh mục
3. Lý do: Những red flags và sự đánh đổi (trade-offs) nào đã dẫn đến kết quả đó.
4. Lưu ý về giới hạn: Đây là một quy trình thẩm định được đơn giản hóa, không phải một quyết định tín dụng thực tế.

**Đầu ra hỗ trợ (được hạ mức ưu tiên):** Tổng kết danh mục cuối vòng, bao gồm độ chính xác, rủi ro danh mục và hiệu quả sử dụng room.

## Product Pattern

Sản phẩm sử dụng mô hình trò chơi ra quyết định dựa trên tình huống. Đầu ra chính là consequence card cho từng hồ sơ; đầu ra hỗ trợ là tổng kết danh mục cuối vòng, bao gồm độ chính xác, rủi ro danh mục và hiệu quả sử dụng room.

## Feasibility and Open Questions

- **Độ rộng của khoảng quyết định:** Khoảng quyết định hợp lý nên rộng đến mức nào trước khi sản phẩm không còn mang tính giáo dục? Giải quyết ở W4.
- **Số lượng hồ sơ:** Bao nhiêu hồ sơ sẽ tạo ra một sự đánh đổi room tín dụng thực sự trong vòng 7 tuần? Giả thuyết hiện tại là 5 hồ sơ và sẽ được kiểm chứng trong quá trình xây dựng.
- **Cơ sở xác định red flag:** Vẫn cần được kiểm chứng dựa trên thực tiễn tín dụng cá nhân tại Việt Nam hoặc với một chuyên gia tín dụng. Bằng chứng ở W3.
- **Nội dung giải thích hệ quả:** Do nhóm tự xây dựng, vì vậy phải công khai rằng đây là mô phỏng/đơn giản hóa. Giả định ở W3.
