## 1. TRỪU TƯỢNG
### 1.1 Luồng
#### 1.1.1 Định nghĩa

***Luồng là gì?***: Về mặt kỹ thuật, luồng là một đơn vị thực thi độc lập được hệ điều hành lên lịch để chạy. Nói cách khác, nó là một "thủ tục" có thể chạy song song với chương trình chính.

***Hình dung đa luồng***: Hãy tưởng tượng một chương trình có nhiều thủ tục. Với đa luồng, tất cả các thủ tục này có thể được thực thi đồng thời và độc lập bởi hệ điều hành.

***So sánh luồng và quy trình***: Luồng sử dụng tài nguyên của quy trình (như bộ nhớ và CPU) nhưng được hệ điều hành lên lịch và chạy như các thực thể riêng biệt. So với quy trình, luồng nhẹ hơn vì nó chỉ sao chép các tài nguyên thiết yếu để thực thi độc lập.

***Đặc điểm của luồng trong môi trường UNIX***:
* Tồn tại trong một quy trình và sử dụng tài nguyên của quy trình đó.
* Có luồng điều khiển độc lập riêng.
* Chỉ sao chép các tài nguyên thiết yếu để có thể lập kế hoạch độc lập.
* Có thể chia sẻ tài nguyên quy trình với các luồng khác.

***Hệ quả của việc chia sẻ tài nguyên***
* Thay đổi do một luồng thực hiện đối với tài nguyên hệ thống được chia sẻ sẽ ảnh hưởng đến tất cả các luồng khác.
* Dữ liệu được truy cập bởi nhiều luồng cần được đồng bộ hóa để tránh xung đột.
