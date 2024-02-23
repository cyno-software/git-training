# Câu hỏi thường gặp về Git cơ bản

Để thực hiện nâng cao khả năng xử lý với Git, một số tình huống xảy ra cần có phương pháp xử lý cụ thể.

## 1. Không thể lấy code Git dự án về

**Dự đoán:**
- Chưa làm theo mục 4 - Git cơ bản (thêm SSH key)
- Dự án muốn lấy về có thể không công khai hoặc không đủ quyền truy cập
- Mất kết nối tới github.com

**Cách xử lý**
- Đọc kết quả khi thử `git clone ...` để biết lý do tại sao

## 2. Tôi không thể đẩy code đã commit từ trên máy lên remote online GitHub.com?

**Dự đoán**
- Xung đột code giữa branch trên máy tính và branch online trên GitHub (cùng tên nhưng khác số commit)
- Mất kết nối tới github.com

**Cách xử lý**
- Thử mục 9 - phần 2 - Git cơ bản (push code với tên nhánh local khác nhánh remote)
