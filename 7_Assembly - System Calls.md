* System call là APIs cho giao diện giữa user space và kernel space. Chúng ta đã sử dụng system call. Sys_write và sys_exit, để ghi vào màn hình và thoát khỏi chương trình. 
## Linux system call.
* Bạn cũng có thể gọi Linux system call trong system assembly của mình. **Bạn cần thực hiện các bước sau để sử dụng lệnh gọi hệ thống Linux trong chương trình của mình.**
<pre>
  B1 : Đặt số lệnh gọi hệ thống vào thanh ghi EAX.
  B2 : Lưu trữ các đối số cho lệnh gọi hệ thống trong các thanh ghi EBX, ECX,v.v.
  B3 : Gọi ngắt có liên quan (80h).
  B4 : Kết quả thường được trả về trong thanh ghi EAX.
</pre>
* Có 6 thanh ghi lưu trữ các đối số của lệnh gọi hệ thống được sử dụng. Đây là EBX, ECX, EDX, ESI, EDI và EBP. Các thanh ghi này lấy các đối số liên tiếp, bắt đầu bằng thanh ghi EBX. Nếu có nhiều hơn 6 đối số, thì vị trí bộ nhớ của đối số đầu tiên được lưu trữ trong thanh ghi EBX.
* Đoạn mã sau đây cho thấy việc sử dụng lệnh gọi hệ thống sys_exit
<pre>
  mov eax,1
  int 0x80
</pre>
* Đoạn mã sau đây cho thấy cách sử dụng lệnh gọi hệ thống Sys_write
<pre>
  mov edx,4 
  mov ecx,msg
  mov ebx,1
  mov eax,4
  int 0x80
</pre>
* Tất cả các lệnh syscall được liệt kê trong /usr/include/asm/unistd.h cùng với số của nó. Bạn cần đưa giá trị vào EAX trước khi bạn gọi 80h.
* Bảng sau đây hiển thị một số lệnh gọi hệ thống được sử dụng trong hướng dẫn này. 
![image](https://github.com/user-attachments/assets/f4a11a0f-d858-4b80-b4e1-a53d2009b554)
