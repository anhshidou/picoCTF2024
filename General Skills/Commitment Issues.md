Ở bài này sẽ liên quan đến git commit

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/c873caec-08cb-4514-9300-81dd03035885)

Trước hết, để bắt đầu vào 1 bài liên quan đến git, ta cần phải hiểu git là gì ?

Git là 1 VCS hay là viết tắt của Version Control System là hệ thống kiểm soát các phiên bản phân tán mã nguồn mở. Các VCS sẽ lưu trữ tất cả các file trong toàn bộ dự án và ghi lại toàn bộ lịch sử thay đổi của file. Mỗi sự thay đổi được lưu lại sẽ được và thành một version (phiên bản).

Vậy thì ở bài này, đọc tên bài ta sẽ thấy nó liên quan đến git commit, git commit sẽ liên quan đến dữ liệu mà bạn đã lưu ở trong một repos, khi ta unzip file challenge, ta sẽ được 1 repo sau:

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/b4ef8e40-d896-41d1-8a84-39daa3aa7bff)

Để xem commit, ta vào repo đó

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/e6118ab4-c4d3-4cd0-b0c4-821eb0974a1c)

Khi vừa vào, ta thấy 1 file message.txt, lúc này, ta sẽ sử dụng git log để xem log của git này

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/609ee4fc-7f27-4120-8027-26d6e71fa859)

Rõ ràng ta thấy 2 commit như sau: 1 commit xóa dữ liệu và 1 commit create dữ liệu, sử dụng lệnh git checkout để chuyển commit
``` git checkout -f 87b85d7dfb839b077678611280fa023d76e017b8 ```

Lúc này nó sẽ hiện như sau: 

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/353d8046-9676-44bb-bbc5-15306d4fee75)

Tức là hiện tại bạn đang ở commit create flag, lúc này chỉ cần cat file message là ta sẽ ra flag

Flag: picoCTF{s@n1t1z3_ea83ff2a}
