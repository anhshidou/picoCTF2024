Là 1 người Forensics, việc đầu tiên em làm khi có một bài nào đó như này là xem hex bằng công cụ HxD, nhưng trước hết, ta cứ phải bật file pdf này lên để xem có gì hot không đã

![Screenshot 2024-03-29 22:57:04](https://github.com/anhshidou/picoCTF2024/assets/120787381/6c2fcade-68c2-43b5-82b9-c4ba93682634)

Ồ, vậy là ta có 1 mảnh đầu của flag này. Ta tiếp tục xem định dạng file ở đây là gì

![Screenshot 2024-03-29 23:00:09](https://github.com/anhshidou/picoCTF2024/assets/120787381/78bc4822-bfbf-4ff2-a962-a75ae9adbea1)


Ở đây, theo file signature thì là file 1 file PNG, trong khi đuôi file ban đầu của file này là PDF, ta sẽ thử đổi đuôi file về thành PNG

![Screenshot 2024-03-29 22:53:55](https://github.com/anhshidou/picoCTF2024/assets/120787381/de29aefe-40aa-4053-abb9-6221ce6ce9ec)

Ghép 2 mảnh vào và ta được flag
