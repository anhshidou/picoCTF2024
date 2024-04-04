Ở bài này, liên quan đến việc đảo ngược bit như Little Endian và Big Endian. Đi search thử google thì em tìm ra được cái này

https://unix.stackexchange.com/questions/239543/is-there-a-oneliner-that-converts-a-binary-file-from-little-endian-to-big-endian

``` hexdump -v -e '1/4 "%08x"' -e '"\n"' challengefile | xxd -r -p > challengefile.jpg ```

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/6a1c24a6-13ef-432c-8df6-834326332253)

1 dòng là nằm...

![image](https://github.com/anhshidou/picoCTF2024/assets/120787381/e13d815f-388a-4097-8174-d9eae5c1653e)

