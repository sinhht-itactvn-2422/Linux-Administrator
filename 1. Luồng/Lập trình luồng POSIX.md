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

![quy trình UNIX](https://hpc-tutorials.llnl.gov/posix/images/process.gif)
Quy trình UNIX

![luồng trong quy trình UNIX](https://hpc-tutorials.llnl.gov/posix/images/thread.gif)
Luồng trong quy trình UNIX

#### 1.1.2 P-Thread

P-Thread được định nghĩa là một tập hợp các kiểu lập trình ngôn ngữ C và các lệnh gọi thủ tục, được triển khai bằng tệp pthread.h header/include và thư viện luồng - mặc dù thư viện này có thể là một phần của thư viện khác, chẳng hạn như libc, trong một số triển khai.

***Lý do chọn P-Thread***:

* ***Nhẹ***:
  * So với quy trình, luồng được tạo và quản lý với chi phí hệ thống thấp hơn nhiều.
  * Ví dụ: tạo luồng bằng pthread_create() nhanh hơn nhiều so với tạo quy trình bằng fork().

* ***Truyền thông và trao đổi dữ liệu hiệu quả***:
  * P-Threads cho phép đạt hiệu suất tối ưu trong môi trường điện toán hiệu năng cao.
  * Luồng chia sẻ cùng một không gian địa chỉ trong một quy trình, loại bỏ nhu cầu sao chép dữ liệu giữa các tiến trình.
  * Giao tiếp P-Threads có thể nhanh hơn nhiều so với giao tiếp MPI trên nút.
 
* ***Lợi ích khác***:
  * Chồng chéo CPU với I/O: các luồng khác có thể thực hiện công việc trong khi chờ I/O.
  * Lập kế hoạch ưu tiên/thời gian thực: ưu tiên các nhiệm vụ quan trọng hơn.
  * Xử lý sự kiện không đồng bộ: xen kẽ các nhiệm vụ với các sự kiện dịch vụ không xác định.
