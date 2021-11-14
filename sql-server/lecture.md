### HƯỚNG DẪN CÀI ĐẶT SQL SERVER TRÊN DOCKER
1. Tải docker: https://www.docker.com/get-started (tải bản desktop để dùng trên máy nhé)
![docker](/sql-server/Docker.png)
2. Tải Azure Data Studio: https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15
![azure](/sql-server/azure.png)

3. Cài đặt sql server lên docker:
	* Mọi người có thể làm theo hướng dẫn này: https://hub.docker.com/_/microsoft-mssql-server
	* Hoặc theo các bước sau:
		+ Mở cmd
		+ Kiểm tra docker có đang chạy không: ```docker -v``` -> kiểm tra phiên bản docker
		+ Nhập lệnh: ```docker pull mcr.microsoft.com/mssql/server:2019-latest``` -> pull image (tạm gọi là 1 bản sao) của sql server về máy. Kiểm tra image bằng docker destop hoặc cmd: ```docker image ls```
	
		+ Chờ máy pull xong image về, run image bằng lệnh: ```docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<thay mật khẩu login sql vào đây>" -p 8001:1433 -d mcr.microsoft.com/mssql/server:2019-latest```
    
    *ghi chú:
	mật khẩu phải có đủ ít nhất 8 ký tự bao gồm: chữ thường, chữ IN HOA, ký tự đ@c biệt, và 5ố nha! vd: Pa$$w0rd chỗ 8001 là port sẽ mở trên máy để connect, mn có thể sửa thành port khác miễn là hợp lệ, còn 1433 là của image, không cần sửa*
	+ Kiểm tra đã run được container chưa trong docker desktop, hoặc cmd: ```docker container ls```
	
4. Connect đến SQL server trên docker
	* Mở Azure Data Studio
	* Chọn biểu tượng connections -> New Connection -> điền các thông tin như hình dưới:
  
    ![connectsql](/sql-server/connectsql.png)

		*	lưu ý port và password cho đúng nhé
	* Connect thành công:

    ![ok](/sql-server/connectok.png)

	* Vậy là mn có thể sử dụng dc SQL server như thông thường rồi :3
	* Có 1 lưu ý là mỗi lần cần dùng thì phải run container này lên nhé: vào docker desktop -> tìm tên container -> click run là được
    
    ![run container](/sql-server/runcontainer.png)
	
	
