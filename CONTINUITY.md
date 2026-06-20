# CONTINUITY

- Goal (incl. success criteria):
  - Chỉnh worklog tuần theo nội dung `format-worklog.yaml`, dùng `all-ui-tree.txt` để xác định đúng file đích.
  - Success: file tuần hiện tại và entry danh sách Worklog khớp với dữ liệu authoritative trong `format-worklog.yaml` ở cả VI/EN nếu file tồn tại.

- Constraints/Assumptions:
  - Chỉ dùng thông tin đã xác nhận trong ngữ cảnh hiện tại; thiếu thông tin thì ghi `UNCONFIRMED`.
  - Ledger canonical nằm tại `CONTINUITY.md`.
  - Không dựa vào lịch sử chat nếu chưa được phản ánh trong ledger.

- Key decisions:
  - Đọc `CONTINUITY.md` và cập nhật nó ở đầu mỗi lượt.
  - Ưu tiên sửa content worklog trước, rồi đồng bộ entry trên trang danh sách.

- State:
  - Done:
    - Đã đọc `rule/continuity-ledger-rule.mdc`.
    - Đã đọc `format-worklog.yaml`.
    - Đã đọc `all-ui-tree.txt`.
    - Đã xác định authoritative hiện tại là `Week: 6`.
    - Đã cập nhật `content/1-Worklog/1.6-Week6/_index.vi.md`.
    - Đã cập nhật `content/1-Worklog/1.6-Week6/_index.md`.
    - Đã cập nhật entry tuần 6 trong `content/1-Worklog/_index.vi.md`.
    - Đã cập nhật entry tuần 6 trong `content/1-Worklog/_index.md`.
    - Đã xác minh nội dung đã khớp với YAML bằng đọc file và grep.
    - Đã xóa các hàng trống khỏi bảng tuần 6 ở cả VI/EN để giao diện gọn hơn.
  - Now:
    - Chờ yêu cầu tiếp theo của người dùng.
  - Next:
    - Với mỗi lượt mới, đọc lại `CONTINUITY.md` rồi cập nhật nếu trạng thái thay đổi.

- Open questions (`UNCONFIRMED` if needed):
  - Không.

- Working set (files/ids/commands):
  - `rule/continuity-ledger-rule.mdc`
  - `CONTINUITY.md`
  - `format-worklog.yaml`
  - `all-ui-tree.txt`
  - `content/1-Worklog/1.6-Week6/_index.vi.md`
  - `content/1-Worklog/1.6-Week6/_index.md`
  - `content/1-Worklog/_index.vi.md`
  - `content/1-Worklog/_index.md`
