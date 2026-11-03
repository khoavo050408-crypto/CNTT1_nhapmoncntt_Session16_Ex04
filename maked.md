# BÁO CÁO ĐÁNH GIÁ QUY TRÌNH LÀM VIỆC DÀNH CHO DEVELOPER

## Phần 1: So sánh và Đánh giá

Bảng so sánh chi tiết giữa việc sử dụng **Incognito Mode** và **Dedicated Profile** theo 3 tiêu chí nghiệp vụ:

| Tiêu chí | Incognito Mode | Dedicated Profile |
| :--- | :--- | :--- |
| **1. Cách ly dữ liệu** | **Tạm thời:** Cách ly Session/Cookie khỏi Profile chính trong phiên làm việc. Tắt cửa sổ là toàn bộ Cookie, LocalStorage và Session state bị xóa sạch. | **Tuyệt đối & Lâu dài:** Tạo môi trường Sandbox hoàn toàn độc lập (Cookie, Cache, LocalStorage, Extension, History). Dữ liệu giữa các Profile không can thiệp lẫn nhau. |
| **2. Lưu giữ trạng thái** | **Không có:** Mất toàn bộ Session đăng nhập, History, và không thể lưu Bookmark hay tùy chỉnh Extension sau khi đóng trình duyệt. | **Rất tốt:** Lưu trữ cố định Cookie đăng nhập, Lịch sử truy cập, hệ thống Bookmark tài liệu và các Extension hỗ trợ Dev. |
| **3. Hiệu suất làm việc** | **Kém:** Phải lặp lại các thao tác đăng nhập, tìm kiếm URL/tài liệu kỹ thuật và cấu hình công cụ test mỗi khi mở lại phiên làm việc. | **Tối ưu:** Mở trình duyệt là làm việc ngay (*One-click access*), truy cập nhanh Bookmark dự án, tiết kiệm đáng kể thời gian thao tác thừa. |

---

## Phần 2: Giải pháp và Đề xuất Mô hình 3 Profile chuẩn Dev

### 1. Mô hình 3 Profile chuẩn Dev (Personal - Work - Sandbox)

Thay vì dùng **Incognito Mode**, giải pháp tối ưu là phân chia không gian làm việc thành 3 Profile độc lập trên trình duyệt:

1. **PERSONAL**
   - **Mục đích:** Nhu cầu cá nhân, giải trí, tra cứu ngoài dự án.
   - **Dữ liệu:** Gmail cá nhân, mạng xã hội, Bookmark học tập/cá nhân.

2. **WORK (Dự án LMS)**
   - **Mục đích:** Môi trường chính phát triển và quản lý hệ thống LMS.
   - **Dữ liệu:** Email công việc/trường, Git, Jira, Documentation, DevTools.

3. **SANDBOX (Môi trường Test)**
   - **Mục đích:** Đăng nhập tài khoản test (Student, Instructor, Admin).
   - **Dữ liệu:** Cookie test cố định, Bookmark sẵn đường dẫn Local/Staging.

---

### 2. Lập luận tại sao Dedicated Profile tối ưu hơn Incognito Mode

- **Giải quyết dứt điểm nỗi đau mất Bookmark & State:**  
  Với Dedicated Profile, toàn bộ tài liệu kỹ thuật, đường dẫn API doc hay các trang test của dự án LMS được lưu cố định trên cây Bookmark của Profile Work/Sandbox.

- **Tối ưu hóa thời gian và nhịp làm việc:**  
  Việc chuyển đổi giữa làm việc, test hệ thống và cá nhân chỉ tốn một cú click chuyển Window Profile (`Alt` + `Tab` hoặc chọn Profile icon).

- **Tích hợp công cụ hỗ trợ Lập trình:**  
  Incognito Mode mặc định chặn các Extension hoặc yêu cầu cấp quyền thủ công phức tạp. Dedicated Profile cho phép cài đặt riêng các DevTools phù hợp cho từng môi trường (ví dụ: Profile Work cài Git/DevTools, Profile Personal cài uBlock/Addons cá nhân).

- **Kiểm thử đa vai trò dễ dàng:**  
  Khi test phân quyền hệ thống LMS (ví dụ: Giảng viên tạo bài giảng, Học viên vào nộp bài), có thể mở song song Profile Work (role Giảng viên) và Profile Sandbox (role Học viên) cạnh nhau để kiểm tra real-time mà không bị xung đột Cookie.