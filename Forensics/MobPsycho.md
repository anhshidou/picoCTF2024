Bài này phần nhiều là guessing, thế nên em xin phép sử dụng 1 câu lệnh để ra flag, vì em đã tốn 1 tiếng để tìm cái file chết tiệt này

![Screenshot 2024-03-29 23:12:26](https://github.com/anhshidou/picoCTF2024/assets/120787381/3da39f54-72c9-4272-9a27-25911223f3ee)

Unzip file xong, ta sử dụng các câu lệnh như sau:

``` find */* -name flag.txt```
``` cat res/color/flag.txt ```

Nó sẽ ra 1 dòng base chết tiệt nào đó, lúc này lên cyberchef để decode là ta ra flag

![Screenshot 2024-03-29 23:15:58](https://github.com/anhshidou/picoCTF2024/assets/120787381/c5278e27-c9cf-42f9-a091-be751a1e20d0)

**Flag: picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_5e67ea5e}**
