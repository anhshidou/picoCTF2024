Để bắt đầu, ta đăng nhập vào server của pico

![Screenshot 2024-03-29 22:21:43](https://github.com/anhshidou/picoCTF2024/assets/120787381/4fab6919-a7e2-4291-a0e2-0055c5130011)

Sau đó sử dụng ls để xem các file có bên trong. Ở đây ta thấy có 1 file là checksum, 1 file decrypt và 1 dir là files. Ở bài này, ta chỉ cần làm theo đề bài là được

![Screenshot 2024-03-29 22:24:56](https://github.com/anhshidou/picoCTF2024/assets/120787381/ef4b19a7-4c51-4d5a-9a43-db8f1b8b0131)

Vậy là ta đã tìm được file hash, giờ thì chỉ cần decrypt nó và lấy flag

![Screenshot 2024-03-29 22:26:03](https://github.com/anhshidou/picoCTF2024/assets/120787381/1de64879-e97c-4151-8aa8-0cadf3db986b)

**Flag: picoCTF{trust_but_verify_87590c24}**
