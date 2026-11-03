# Vấn đề :
Nam là thực tập sinh tại GreenLogistics. Nam nhận nhiệm vụ truy cập trang quản trị tại địa chỉ [**phong-dieu-phoi.greenlog.vn**](http://phong-dieu-phoi.greenlog.vn) để cập nhật lộ trình xe tải. Tuy nhiên, trình duyệt liên tục báo lỗi **"DNS_PROBE_FINISHED_NXDOMAIN"**. Nam khẳng định do máy chủ công ty bị sập nguồn.
# Yêu cầu :
-   **Chức năng 1 (Phân tích mạng):** Giải thích chi tiết tiến trình DNS Lookup từ khi Nam gõ tên miền đến khi trình duyệt tìm thấy địa chỉ IP máy chủ.
    
-   **Chức năng 2 (Chẩn đoán lỗi):** Phân biệt bản chất giữa lỗi DNS và lỗi 500 Internal Server Error để xác định lỗi này nằm ở phía Client hay Server.

# Cách làm :
### Phần 1 :Phân tích 

-   Input :phong-dieu-phoi.greenlog.vn
    
- Output : Địa chỉ IP của máy chủ đích
    
-   Sơ đồ luồng dữ liệu DNS (DNS Resolution Flow):
    
### Phần 2. Triển khai
1.  Kiểm tra nhóm mã lỗi không chạm tới máy chủ
        -   Nếu trình duyệt trả về các lỗi như DNS_PROBE_FINISHED_NXDOMAIN,  ERR_CONNECTION_REFUSED hoặc ERR_CONNECTION_TIMED_OUT:  Yêu cầu chưa chạm tới máy chủ 
       
3.-   Sai đường dẫn Đường dẫn cụ thể đến trang quản trị mà Nam nhập trên thanh địa chỉ bị gõ sai chính tả (.
    
-   Tài nguyên không tồn tại hoặc đã bị xóa: Trang quản trị, tệp tin, hoặc thư mục mà Nam đang cố gắng truy cập đã bị gỡ bỏ, đổi tên hoặc chưa từng được triển khai trên máy chủ.
    
-   Lỗi cấu hình định tuyến : Hệ thống mã nguồn trên máy chủ chưa được cấu hình đường dẫn  tương ứng cho URL mà Nam truy cập, dẫn đến việc máy chủ không biết phải phản hồi nội dung gì cho yêu cầu đó.
