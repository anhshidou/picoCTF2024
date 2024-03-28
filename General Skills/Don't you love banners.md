Bài này lỏ ác, khi mà ChatGPT solve đến 50% bài :)))

Trước hết, chúng ta kết nối vào server đầu tiên bằng netcat, khi connect vào, ta được như sau:

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/adcaa2fa-9e83-4f47-8f45-1852c3b0d4bf)

Khi thử copy xuống, ta sẽ được các dòng liên quan đến ssh-key

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/30602d73-26b1-4561-8f04-34724ce91980)

Em cảm giác nó không liên quan gì cho lắm nên em sẽ bỏ qua nó, và vì nó cảm giác không liên quan gì lắm nên em sẽ connect vào server tiếp theo

Ở đây, câu đầu tiên em gặp là password ? Vậy thì password là gì nhỉ, vì bài này mang thiên hướng guessing khá nhiều nên em đoán password ở đây sẽ là server mà ta vừa connect

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/bfe05b37-02bc-496e-8fab-4677c2fab0f6)

Password là gì nhỉ, vì bài này mang thiên hướng guessing khá nhiều nên em đoán password ở đây sẽ là server mà ta vừa connect

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/92ee9ed5-0963-4d61-b915-24f140e4213a)

Adu vậy nó có thật, tiếp đến câu số 2.

**What is the top cyber security conference in the world?** Ở câu này sẽ sử dụng google, tuy nhiên, google hiện update ra các kết quả ở 2024, vì vậy nên bạn sẽ không thể tìm ra nổi nếu như cứ ở mãi ở hiện tại, vậy thì thử quay về quá khứ cùng chatGPT xem

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/87ec0996-0d48-417d-b873-0b015cd249db)

Mởi đầu, em nghĩ nó sẽ là RSA vì ở server thứ nhất liên quan nhiều đến mã hóa, tuy nhiên khi thử thì lại không được, khi ta thử đến DEFCON thì nó lại được ? IDK why ?

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/8e3026b8-9ec8-46d7-851d-841b373b6435)

Như câu hỏi trước, ta lại tiếp túc sử dụng chatGPT để làm hộ, đáp án ở đây là John Draper

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/4bc35a8c-f6ad-4142-8363-870d29078891)

Khi đã thành công, ta xem thử hint và thấy 1 cái khá thú vị, đó là symlinks

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/bcbe4104-15f9-4a7c-823b-a6899cdc9e8e)

Hiểu đơn giản, symlinks là đường tắt mà có thể chỉ đến file gốc mà ta muốn, có thể hiểu hơn rằng nó là cổng không gian. Ở bài này, ta có 2 hướng, 1 hướng crack password và 1 hướng sử dụng symlinks. Ở picoCTF2024 thì em sử dụng hướng symlinks

# Hướng symlinks:
Để ý description bài, ta thấy flag nằm ở root dir, ta change dir vào root

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/a30eb153-5501-47c9-aa01-4a1835bd0136)

Thử cat flag.txt

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/82d646c5-0d0f-4ca3-a14c-99fd7f120380)

Không được, ta sẽ xem permission của nó như thế nào

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/474f093c-3b48-4e82-8e18-2cb84b9ddf1c)

Hmm, như ta có thể thấy, chỉ có quyền của Super User mới có full perm là rwx, còn của file script.py thì User và Group User đều có quyền read, vì vậy nên em sẽ xem thử script này có gì hot không

``` import os
import pty

incorrect_ans_reply = "Lol, good try, try again and good luck\n"

if __name__ == "__main__":
    try:
      with open("/home/player/banner", "r") as f:
        print(f.read())
    except:
      print("*********************************************")
      print("***************DEFAULT BANNER****************")
      print("*Please supply banner in /home/player/banner*")
      print("*********************************************")

try:
    request = input("what is the password? \n").upper()
    while request:
        if request == 'MY_PASSW@RD_@1234':
            text = input("What is the top cyber security conference in the world?\n").upper()
            if text == 'DEFCON' or text == 'DEF CON':
                output = input(
                    "the first hacker ever was known for phreaking(making free phone calls), who was it?\n").upper()
                if output == 'JOHN DRAPER' or output == 'JOHN THOMAS DRAPER' or output == 'JOHN' or output== 'DRAPER':
                    scmd = 'su - player'
                    pty.spawn(scmd.split(' '))

                else:
                    print(incorrect_ans_reply)
            else:
                print(incorrect_ans_reply)
        else:
            print(incorrect_ans_reply)
            break

except:
    KeyboardInterrupt 

```
Hóa ra, đây là script để chạy server này. Vì thế nên trước hết em sẽ thử cat file flag dưới tên của Super User

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/6a881586-7a16-4f34-b2d1-7a1deba29975)

Hmmm, ta đã hoàn toàn bị chặn lại bởi password, vì vậy nên em sẽ sử dụng cách dễ hơn là symlinks

``` ln -sf /root/flag.txt banner ```
-s là create symbolic link
-f là force

Khi đã tạo được, ta thoát ra và đăng nhập lại

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/09083fe6-8eba-4148-bda9-4729cbcf9d40)

Có flag: picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_ed6f9c71}

# Hướng Crack password

Cái này em xin phép trình bày mồm và ý tưởng chứ em chưa làm ra bằng cách này :)))
