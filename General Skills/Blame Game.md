Ở bài này, ta cần phải đi tìm issue bên trong commit của một người nào đó đã khiến cho chương trình không thể hoạt động được

Ở bài này, một lần nữa chúng ta đi tìm commit bị lỗi bằng cách sử dụng git log, tuy nhiên vì form flag là picoCTF nên em có thể sử dụng grep để tìm flag nhanh hơn

``` git log | grep picoCTF{.*} ```

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/b15b747a-0f46-4a2c-b0e9-5d53345bd1c7)

# Hoặc
Khi ta cat message.py, ta thấy cấu trúc của dòng code python này có vấn đề khi chưa được đóng ngoặc, điều này sẽ dẫn đến lỗi, vì thế nên ta có thể biết được lỗi sẽ nằm trong file python này, vì thế nên ta sử dụng git log vào trong file python để tìm nhanh hơn nữa

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/6d66a1d4-a62f-4a20-811d-d33d13e7cabb)

``` git log -p message.py ```

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/e2c160cd-1cca-4f48-acaa-462831e451a5)

Flag: picoCTF{@sk_th3_1nt3rn_d2d29f22}
