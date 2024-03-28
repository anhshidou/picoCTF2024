Bài này là 1 bài shell escape với giới hạn chữ số và không được dùng từ. Ở bài này, em đang một người bạn chỉ cách làm (anh Trần Hoàng Long CTV BCM) vì vậy nên cách làm của em khá giống với anh ấy, mong cả nhà thông cảm :))


Ở bài này, khi ta thử những câu lệnh bình thường của bash cmd như ls, cat hay gì đó, thì ta đều không làm được.
Vì vậy nên, tại sao ta lại không thử cat nhỉ.
Trước hết ta phải xem directory ở đây là gì bằng ~, vậy là ta thấy ctf-player

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/a6d63f68-8109-4c44-8348-309aad14ee95)

Tiếp theo, ta tạo biến bằng _1=(~) để tạo biến _1 cho dir
``` _1=(~)
${_1:6:1}${_1:12:1}${_1:7:1} */*
```
Sau đó ta xem các vị trí của tên dir để ghép lại thành cat

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/3f00a686-94e6-464e-b4a1-46e9c71fc032)

Flag: picoCTF{7h15_mu171v3r53_15_m4dn355_640b6add}
