## Một chương trình Assembly chia ra thành 3 section : 
* Data section.
* Bss section.
* Text section.
### Data section.
* Phần **dữ liệu** được dùng để khai báo dữ liệu hoặc các hằng số đã khởi tạo. Dữ liệu này không thay đổi khi chạy. Bạn có thể khai báo nhiều giá trị hằng số, tên tệp hoặc kíck thước bộ đệm, .v.v trong section này.
* Cú pháp khai báo dữ liệu là `section .data`
### Bss section.
* Phần **bss** được dùng để khai báo các biến. Cú pháp khai báo các phần **bss** là `section .bss`
### Text section.
* Phần **text** được sử dụng để lưu trữ mã thực tế. Phần này phải bắt đầu bằng khai báo **global _start**, để cho **kernel** biết nơi bắt đầu thực thi chương trình.
* Cú pháp khai báo phần **text** là : 
<pre>section .text
   global _start
_start:</pre>
### Comments
* Bình luận ngôn ngữ lắp ráp bắt đầu bằng dấu chấm phẩy (;). Nó có thể chứa bất kỳ ký tự in được nào bao gồm cả khoảng trắng. Nó có thể xuất hiện trên một dòng riêng lẻ, như.<br>
`; This program displays a message on screen`
* Hoặc, trên cùng một dòng cùng với một hướng dẫn, như.<br>
`add eax, ebx     ; adds ebx to eax`
## Syntax of Assembly Language Statements
* Các câu lệnh ngôn ngữ **Assembly** được nhập một câu lệnh trên một dòng. Mỗi câu lệnh tuân theo định dạng sau.<br>
`[label]   mnemonic   [operands]   [;comment]`
* Các trường trong dấu ngoặc vuông là tùy chọn. Một lệnh cơ bản có hai phần, phần đầu tiên là tên lệnh (hoặc ký hiệu ghi nhớ) cần thực hiện, và phần thứ hai là các toán hạng hoặc tham số của lệnh.<br>
<pre>
INC COUNT        ; Tăng biến bộ nhớ COUNT lên 1

MOV TOTAL, 48    ; Chuyển giá trị của 48 vào biến `TOTAL` `MOV`
                 ; Hoặc là sao chép
					  
ADD AH, BH       ; Thêm nội dung của
                 ; thanh ghi BH vào thanh ghi AH
					  
AND MASK1, 128   ; Thực hiện phép toán AND trên
                 ; biến MASK1 và 128
					  
ADD MARKS, 10    ; Thêm 10 vào biến MARKS
MOV AL, 10       ; Chuyển giá trị 10 vào thanh ghi AL</pre>

## Thử code một chương trình Assembly để in ra "Hello, world!" ngoài màn hình : 
<pre>section .data
    hello db 'Hello, world!', 0x0A  ; Chuỗi cần in ra, 0x0A là ký tự xuống dòng

section .bss

section .text
    global _start

_start:
    ; Ghi "Hello, world!" ra màn hình
    mov eax, 4            ; syscall số 4 (sys_write)
    mov ebx, 1            ; file descriptor 1 (stdout)
    mov ecx, hello        ; địa chỉ của chuỗi "Hello, world!"
    mov edx, 14           ; số byte của chuỗi (14 bao gồm ký tự xuống dòng)
    int 0x80              ; gọi kernel

    ; Kết thúc chương trình
    mov eax, 1            ; syscall số 1 (sys_exit)
    xor ebx, ebx          ; mã thoát 0
    int 0x80              ; gọi kernel</pre>
### Giải thích 
* section .data:
Phần này chứa dữ liệu tĩnh của chương trình. Chúng ta khai báo chuỗi "Hello, world!" và thêm ký tự xuống dòng 0x0A vào cuối.
* section .bss:
Phần này được dùng cho các biến chưa được khởi tạo hoặc có kích thước thay đổi. Trong trường hợp này, chúng ta không sử dụng nó.
* section .text:
Phần này chứa mã lệnh thực thi.
* global _start:
Đánh dấu _start là điểm bắt đầu của chương trình.
* _start::
Điểm bắt đầu của chương trình.
* mov eax, 4:
Đặt số 4 vào thanh ghi eax để chỉ định syscall sys_write (viết dữ liệu ra màn hình).
* mov ebx, 1:
Đặt số 1 vào thanh ghi ebx để chỉ định file descriptor 1 (stdout).
* mov ecx, hello:
Đặt địa chỉ của chuỗi "Hello, world!" vào thanh ghi ecx.
* mov edx, 14:
Đặt số byte của chuỗi vào thanh ghi edx.
* int 0x80:
Gọi hàm hệ thống để thực thi lệnh sys_write.
* mov eax, 1:
Đặt số 1 vào thanh ghi eax để chỉ định syscall sys_exit (thoát chương trình).
* xor ebx, ebx:
Đặt mã thoát 0 (không có lỗi).
* int 0x80:
Gọi hàm hệ thống để thực hiện lệnh sys_exit.
## Để chạy Assembly trong NASM chúng làm theo các bước sau : 
* Mở Terminal trên máy ảo Linux chúng ta có thể dùng 2 trình soạn thảo nano && vim để code vd với nano : `nano hello.asm`
* Để biên dịch chương trình, hãy nhập `nasm -f elf hello.asm`
* Nếu có bất kỳ lỗi nào, **bạn sẽ được nhắc về lỗi đó ở giai đoạn này**. Nếu không, một tệp đối tượng của chương trình của bạn có tên `hello.o` sẽ được tạo.
* Để liên kết tệp đối tượng và tạo tệp thực thi có tên hello, hãy nhập `ld -m elf_i386 -s -o hello hello.o`
* Thực hiện chương trình bằng cách gõ `./hello`



