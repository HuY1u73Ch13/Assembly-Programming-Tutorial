# Cách setup môi trường Assembly.
* Mở Linux và nhập whereis nasm
* Nếu đã cài đặt nó sẽ hiện lên dòng : /usr/bin/nasm, nếu không bạn sẽ chỉ thấy nasm. 
### Để cài đặt NASM, làm theo các bước sau :
* Kiểm tra trang web "The netwide assembler (NASM)" để biết phiên bản mới nhất.
* Tải xuống kho lưu trữ mã nguồn Linux nasm-X.XX.ta.gz, trong đó X.XXcó số phiên bản NASM.
* Giải nén tệp lưu trữ vào một thư mục tạo ra một thư mục con nasm-X. XX.
* cd đến nasm-X.XXvà nhập ./configure . Tập lệnh shell này sẽ tìm trình biên dịch C tốt nhất để sử dụng và thiết lập Makefiles cho phù hợp.
* Nhập make để xây dựng các tệp nhị phân nasm và ndisasm.
* Gõ make install để cài đặt nasm và ndisasm trong /usr/local/bin và để cài đặt các trang hướng dẫn.
### Còn nếu đang trong version cũ. 
* Gõ nasm --version để kiểm tra.
* sudo apt-get update
* sudo apt-get upgrade
* sudo apt install nasm
