Ở bài này, ta sử dụng 2 công cụ là ExiftoolGUI và HxD

Trước hết, ta xem xem ở bài này có cái gì hot. Trước hết, ta xem thử metadata của bức ảnh bằng exiftool

![Screenshot 2024-03-31 15:40:56](https://github.com/anhshidou/picoCTF2024/assets/120787381/f317f3ee-776f-4e59-9337-ae15d83b1da7)

Như ta thấy thì đây là 1 bức ảnh khá bình thường, vì thế nên ta quay lại đề bài để xem xem có cái gì không

![Screenshot 2024-03-31 15:41:43](https://github.com/anhshidou/picoCTF2024/assets/120787381/43c4d7af-84a9-490d-a486-77377d95d4c7)

Hmmm, vậy là ta phải chuyển những cái time thành đúng format của nó. Trước hết, ta sẽ thử xem khi connect 2 server kia sẽ có gì

![Screenshot 2024-03-31 15:45:32](https://github.com/anhshidou/picoCTF2024/assets/120787381/fe60301f-f010-47b9-ab42-efb94da175bd)

Ồ, vậy là ta sẽ có 1 server để submit ảnh và 1 server để kiểm tra xem ảnh có đúng không. Ở server kiểm tra ảnh, ta thấy nó có 7 tags, tag thứ nhất liên quan đến Modify Date. Lúc này ta sử dụng ExiftoolGUI để chỉnh sửa.

![Screenshot 2024-03-31 15:47:42](https://github.com/anhshidou/picoCTF2024/assets/120787381/afc0027a-66d2-4038-a87e-5666a9d665da)

Đây là giao diện của ExifToolGUI, ở đây ta sẽ thay đổi các mục thời gian bằng việc cho nó vào workspace để đổi. Trước hết, ở Tag 1, ta đổi về thành format time mà đề bài yêu cầu.

![Screenshot 2024-03-31 15:50:20](https://github.com/anhshidou/picoCTF2024/assets/120787381/594392df-9b41-4d4f-820d-d1c85a34ee67)

Đây là khi ta đã đổi xong, khi hoàn thành thì ta chỉ cần lặp lại các bước như ban đầu, submit ảnh và check ảnh bằng 2 servers mà đề bài cho.

![Screenshot 2024-03-31 15:51:37](https://github.com/anhshidou/picoCTF2024/assets/120787381/413cf031-d658-4f10-809a-634b795cfa04)

Ở tag thứ 2, ta cũng làm như tag thứ 1. 

![Screenshot 2024-03-31 15:52:42](https://github.com/anhshidou/picoCTF2024/assets/120787381/791b62f0-c694-4c57-ab28-1be1a898ffca)

Tiếp tục submit và làm

![Screenshot 2024-03-31 15:54:44](https://github.com/anhshidou/picoCTF2024/assets/120787381/944ab491-26d5-44db-a2ea-68abbbb6b284)

Tag thứ 3:

![Screenshot 2024-03-31 15:56:40](https://github.com/anhshidou/picoCTF2024/assets/120787381/5527a41e-c889-4395-b844-bfb21283c70f)

Tag thứ 4:

![Screenshot 2024-03-31 15:58:05](https://github.com/anhshidou/picoCTF2024/assets/120787381/0e13cf47-323c-4dc7-ab3c-ebab26fac5d1)

Tag thứ 5:

![Screenshot 2024-03-31 15:58:33](https://github.com/anhshidou/picoCTF2024/assets/120787381/c7a7026f-ce8d-4c24-9128-a222d3bf34a3)

Tag thứ 6:

![Screenshot 2024-03-31 15:59:01](https://github.com/anhshidou/picoCTF2024/assets/120787381/084e1676-b93d-45ff-a50f-46c493fa090a)

Vậy là ta đã xong 6 tags, còn tag thứ 7 là timestamp. Lúc này ta lên epoch converter để convert giờ

![Screenshot 2024-03-31 16:00:13](https://github.com/anhshidou/picoCTF2024/assets/120787381/880e2953-8421-4863-b122-62fc29441268)

Vậy là timestamp ở đây là 0. Lúc này ta sử dụng HxD để xem liệu rằng có thể chỉnh sửa nó ở trong không

![Screenshot 2024-03-31 16:06:32](https://github.com/anhshidou/picoCTF2024/assets/120787381/9a117063-653b-49c9-883f-a76c40b66615)

Nhìn dòng này rất quen, khi ta thử đem nó lên epoch converter, ta thấy rằng nó chính là thời gian ban đầu của bức ảnh, lúc này ta chỉ cần chuyển nó về giống như thời gian mà ta đã thử convert ở trong epoch và sử dụng đúng format là **0000000000001**

![Screenshot 2024-03-31 16:10:25](https://github.com/anhshidou/picoCTF2024/assets/120787381/bd32f9c0-9c2e-440b-ae01-677c37adfdf0)

Done.




