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
Các thanh ghi chỉ mục 32-bit, ESI và EDI, và các phần cực phải 16-bit của chúng. SI và DI, được sử dụng để định địa chỉ theo chỉ muc và đôi khi được sử dụng trong phép cộng và phép trừ. Có hai bộ con trỏ chỉ mục 
* Chỉ mục nguồn (SI) - Được sử dụng làm chỉ mục nguồn cho các hoạt động chuỗi.
* Chỉ mục đích (DI) - Được sử dụng làm chỉ mục đích cho các hoạt động chuỗi.
## Control Registers
* Thanh ghi con trỏ lệnh 32-bit và thanh ghi cờ 32-bit kết hợp được coi là thanh ghi điều khiển 
* Nhiều lệnh bao gồm các phép so sánh và tính toán toán học và thay đổi trạng thái của các cờ, trong khi một số lệnh có điều kiện khác kiểm tra giá trị của các cờ trạng thái này để đưa luồng điều khiển đến vị trí khác. 
### Các bit flag phổ biến là : 
* **Overflow Flag** - Cờ này chỉ ra sự tràn của một bit bậc cao (bit ngoài cùng bên trái) dữ liệu sau một phép toán số học có dấu.
* **Direction Flag** - Xác định hướng trái phải hoặc để di chuyển hoặc so sánh dữ liệu chuỗi. Khi giá trị DF là 0, thao tác chuỗi sẽ theo hướng từ trái sang phải và khi giá được đặt thành 1, thao tác chuỗi sẽ theo hướng từ phải sang trái. 
* **Interrupt Flag** - Nó xác định các xem các ngắt bên ngoài như nhập bàn phím, v.v., có bị bỏ qua hay không. Nó vô hiệu hóa ngắt bên ngoài khi và cho phép ngắt khi khi được đặt thành 1.
* **Trap Flag** - Cho phép thiết lập hoạt động của bộ xử lý ở chế độ một bước. Chương trình DEBUG mà chúng tôi sử dụng sẽ thiết lập Trap Flag, do đó chúng tôi có thể thực hiện từng lệnh một.  
* **Sign Flag** - Nó hiển thị dấu của kết quả của một phép toán số học. Cờ này được thiết lập theo dấu của một mục dữ liệu sau phép toán số học. Dấu được chỉ định bằng bit cao nhất bên trái. Một kết quả dương sẽ xóa giá trị của SF thành 0 và kết quả âm sẽ đặt nó thành 1.
* **Zero Flag** - Biểu thị kết quả của phép toán số học hoặc phép so sánh. Kết quả khác số không sẽ xóa cờ số không thành 0 và kết quả số không sẽ đặt cờ số không thành 1. 
* **Auxiliary Carry** - Nó chứa lệnh từ bit-3 đến bit-4 sau một phép toán số học, được sử dụng cho phép toán số học chuyên biệt. AF được đặt khi một phép toán số học 1-byte gây ra lệnh từ bit-3 đến bit-4.
* **Parity Flag** - Biểu thị tổng số bit 1 trong kết quả thu được từ phép toán số học. Số bit 1 chẵn sẽ xóa cờ chẵn lẻ thành số 0 và số bit-1 lẻ sẽ đặt cờ thành 1.
* **Carry Flag** - Nó chứa số nhớ 0 và 1 từ một bit bậc cao (bên trái nnhất) sau một phép toán số học. Nó cũng lưu trữ nội dung của bit cuối cùng của một phép dịch chuyển hoặc xoay. 
![image](https://github.com/user-attachments/assets/4e8529ec-4160-446d-aaef-60f17b90f9b2)
## Segment (Thanh Ghi phân đoạn)
* **Code Segment** - Nó chứa tất cả các lệnh được thực hiện. Code segment register 16-bit hoặc thanh ghi DS lưu trữ địa chỉ bắt đầu của đoạn Code.
* **Data Segment** - Chứa dữ liệu, hằng số và vùng làm việc. Thanh ghi phân đoạn dữ liệu 16-bit hoặc thanh ghi DS lưu trữ địa chỉ bắt đầu của phân đoạn dữ liệu. 
* **Stack Segment** - Chứa dữ liệu và địa chỉ trả về của các thủ tục hoặc chương trình con. Được triển khai như một cấu trúc dữ liệu 'Stack'. Thanh ghi phân đoạn ngăn xếp hoặc thanh ghi SS lưu trữ địa chỉ bắt đầu của Stack.

  



