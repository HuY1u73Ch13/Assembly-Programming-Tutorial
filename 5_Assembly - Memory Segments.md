# Three sections of an assembly program.
* 3 phần đã nhắc ỏ trên cũng đại diện cho nhiều phân đoạn bộ nhớ khác nhau.
* Thật thú vị, nếu bạn thay thế từ khóa section bằng segment, bạn cũng sẽ nhận được kết quả tương tự.
<pre> segment .text	   ;code segment
   global _start    ;must be declared for linker
_start:	           ;tell linker entry point
   mov edx,len	   ;message length
   mov ecx,msg     ;message to write
   mov ebx,1	   ;file descriptor (stdout)
   mov eax,4	   ;system call number (sys_write)
   int 0x80	   ;call kernel
   mov eax,1       ;system call number (sys_exit)
   int 0x80	   ;call kernel
segment .data      ;data segment
msg	db 'Hello, world!',0xa   ;our dear string
len	equ	$ - msg          ;length of our dear string </pre>
* Data segment - Nó được biểu diễn bằng phần .data và .bss. Phần .data được sử dụng để khai báo vùng bộ nhớ, nơi các phần tử dữ liệu được lưu trữ cho chương trình. Bộ nhớ đệm này được điền bằng 0.
* Data code - Được biểu diễn bằng phần .text. Phần này định nghĩa môt vùng bộ nhớ lưu trữ code. 
* Stack - Phân đoạn này chứa các giá trị dữ liệu được truyền tới các hàm và thủ tục trong chương trình. 
