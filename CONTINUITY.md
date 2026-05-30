# CONTINUITY

- Goal (incl. success criteria):
  - Chỉnh sửa worklog chi tiết tuần 3 và tiêu đề ngoài theo dữ liệu trong `format-worklog.yaml`.
  - Duy trì áp dụng `rule/continuity-ledger-rule.mdc` cho mọi yêu cầu tiếp theo.
  - Success: Nội dung tuần 3 (VI/EN nếu có) khớp dữ liệu nguồn và phần tiêu đề ngoài được cập nhật đúng.

- Constraints/Assumptions:
  - Chỉ dùng thông tin đã xác nhận trong ngữ cảnh hiện tại; thiếu thông tin thì đánh dấu `UNCONFIRMED`.
  - Ledger canonical nằm tại `CONTINUITY.md`.

- Key decisions:
  - Tuân thủ quy trình đọc/cập nhật `CONTINUITY.md` ở đầu mỗi lượt.
  - Nguồn sự thật cho tuần 3 là `format-worklog.yaml`.

- State:
  - Done:
    - Đã đọc `rule/continuity-ledger-rule.mdc`.
    - Đã khởi tạo `CONTINUITY.md` theo format yêu cầu.
    - Đã đọc skill `ui-ux-pro-max` theo yêu cầu người dùng.
    - Đã xác định vị trí worklog tuần 3: `content/1-Worklog/1.3-Week3/`.
    - Đã cập nhật tiêu đề ngoài và nội dung chi tiết tuần 3 trong:
      - `content/1-Worklog/1.3-Week3/_index.vi.md`
      - `content/1-Worklog/1.3-Week3/_index.md`
    - Đã kiểm tra lại nội dung sau chỉnh sửa bằng đọc file trực tiếp.
    - Đã cập nhật tiêu đề tuần 3 ở trang danh sách Worklog:
      - `content/1-Worklog/_index.vi.md` (`Tuần 3: Làm các bài Lab`)
      - `content/1-Worklog/_index.md` (`Week 3: Lab Practice`)
    - Đã xác minh lại bằng `rg` các chuỗi tiêu đề và nội dung tuần 3.
    - Đã loại bỏ phần lặp `Tiêu đề tuần/Week Title` trong nội dung tuần 3 để tránh trùng với `title` trang.
    - Đã xóa dòng Day 4 bị thiếu nội dung trong bảng tuần 3 và đánh số lại ngày liên tục (1..5) ở cả VI/EN.
  - Now:
    - Đã tinh chỉnh bảng task theo phản hồi người dùng.
  - Next:
    - Chờ người dùng xác nhận hiển thị bảng đã đúng.

- Open questions (`UNCONFIRMED` if needed):
  - Không.

- Working set (files/ids/commands):
  - `rule/continuity-ledger-rule.mdc`
  - `CONTINUITY.md`
  - `format-worklog.yaml`
  - `content/1-Worklog/1.3-Week3/_index.vi.md`
  - `content/1-Worklog/1.3-Week3/_index.md`
  - `content/1-Worklog/_index.vi.md`
  - `content/1-Worklog/_index.md`
  - `Get-Content -LiteralPath ...\\1.3-Week3\\_index.vi.md`
  - `Get-Content -LiteralPath ...\\1.3-Week3\\_index.md`
  - `rg -n "Week 3|Tuần 3|Làm các bài Lab|Lab Practice|title:" ...`
