## Fact about Registers
* Hoạt động của bộ xử lý chủ yếu liên quan đến việc xử lý dữ liệu. Dữ liệu này có thể được lưu trữ trong bộ nhớ và phải truy cập từ đó. Tuy nhiên việc đọc dữ liệu và lưu trữ dữ liệu có thể làm chậm bộ xử lý, vì nó chi đi qua cùng 1 kênh.
* Để tăng tốc hoạt động của bộ xử lý, bộ xử lý bao gồm một số vị trí lưu trữ nội bộ nhớ trong, gọi là thanh ghi. 
* Các thanh ghi lưu trữ các thành phần tử dữ liệu để xử lý mà không cần truy cập vào bộ nhớ. Một số lượng hạn chế các thanh ghi được tích hợp vào chip xử lý.
## Thanh ghi bộ xử lý
* Có mười thanh ghi bộ xử lý 32-bit và sáu thanh ghi bộ xử lý 16-bit trong kiến ​​trúc IA-32. Các thanh ghi được nhóm thành ba loại.
<pre>General registers,
Control registers, and
Segment registers. </pre>
## General registers được chia thành các nhóm sau.
* Thanh ghi dữ liệu,
* Thanh ghi con trỏ và
* Sổ đăng kí chỉ mục.
## Thanh ghi dữ liệu
* Bốn thanh dữ liệu 32-bit hoàn chỉnh : EAX, EBX, ECX, EDX.
* Một nữa dưới của các thanh ghi 32-bit có thể được sử dụng làm bốn thanh ghi dữ liệu 16-bit: AX, BX, CX, và DX.
* Một nửa dưới và một nửa trên của bốn thanh ghi 16-bit được đề cập ở trên có thể được sử dụng làm tám thanh ghi dữ liệu 8-bit: AH, AL, BH, BL, CH, CL, DH, và DL.
### Một số thanh ghi dữ liệu này có công dụng cụ thể trong các phép tính số học. 
* **AX "Accumulator" là bộ tích lũy chính** : Nó được sử dụng trong các lệnh nhập/xuất và hầu hết các lệnh số học. Ví dụ, trong phép nhân, một toán hạng được lưu trữ trong thanh ghi EAX hoặc AX hoặc AL theo kích thước của toán hạng.
* **BX "Base" được gọi là thanh ghi cơ sở** vì nó có thể được sử dụng trong việc định địa chỉ theo mục.
* **CX "Count" được gọi là thanh ghi đếm**, giống như ECX, thanh ghi CX lưu trữ số vòng lặp trong các hoạt động lặp lại.
* **DX "Data" được gọi là thanh ghi dữ liệu**  Nó cũng được sử dụng trong các hoạt động nhập/xuất. Nó cũng được sử dụng với thanh ghi AX cùng với DX cho các hoạt động nhân và chia liên quan đến các giá trị lớn.?
## Thanh ghi con trỏ
* Các thanh ghi con trỏ là các thanh ghi EIP, ESP và EBP 32 bit và các phần bên phải tương ứng là IP, SP và BP 16 bit. Có 3 loại thanh ghi con trỏ
<pre>
- Con trỏ lệnh (IP) − Thanh ghi IP 16 bit lưu trữ địa chỉ offset của lệnh tiếp theo sẽ được thực thi. IP kết hợp với thanh ghi CS (dưới dạng CS:IP) cung cấp địa chỉ đầy đủ của lệnh hiện tại trong đoạn mã.
- Con trỏ ngăn xếp (SP) − Thanh ghi SP 16 bit cung cấp giá trị bù trừ trong ngăn xếp chương trình. SP kết hợp với thanh ghi SS (SS:SP) đề cập đến vị trí hiện tại của dữ liệu hoặc địa chỉ trong ngăn xếp chương trình.
- Con trỏ cơ sở (BP) − Thanh ghi BP 16 bit chủ yếu giúp tham chiếu các biến tham số được truyền cho một chương trình con. Địa chỉ trong thanh ghi SS được kết hợp với offset trong BP để có được vị trí của tham số. BP cũng có thể được kết hợp với DI và SI làm thanh ghi cơ sở để định địa chỉ đặc biệt.
</pre>
## Index Registers

