Phân tích ca sử dụng Create Administrative Report
Mô tả ngắn gọn
Ca sử dụng Create Administrative Report cho phép Payroll Administrator tạo báo cáo quản trị dựa trên các tiêu chí về giờ làm việc hoặc tổng thu nhập năm cho nhân viên.

Xác định các lớp
Boundary Classes:

PaymentSelectionUI: giao diện cho người dùng chọn hình thức thanh toán. Control Classes:
PaymentController: lớp điều khiển xử lý lựa chọn hình thức thanh toán. Entity Classes:
PaymentMethod: lớp chứa các phương thức thanh toán.
Employee: thực thể chứa thông tin về nhân viên (để liên kết thanh toán với nhân viên cụ thể).
Payment: thực thể chứa thông tin thanh toán cụ thể (tiền lương, hình thức thanh toán).
