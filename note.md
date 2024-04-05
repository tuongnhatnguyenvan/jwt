Front End: React
Back End: Laravel
API -> Authentication -> Token(JWT)
Request get data: Gửi Token thông qua Header(Authorization: Bearer <token>)
Serve -> kiểm tra Token có hợp lệ hay không -> Decode Payload -> Truy vấn 
Database trả về dữ liệu

#bảo mật token
Access token => đánh cắp => Hacker dựa vào đó để khai thác data 
-> Giải pháp: Hạ thấp thời gian sống của Access token -> gây phiền phức ng dùng
-> Cần bổ sung: RefreshToken -> thời gian sống lâu hơn -> Dùng để cấp lại AccessToken mới khi AccessToken cũ hết hạn

-> Khi logout -> thêm token vào Blacklist -> Khi authorization -> Cần kiểm tra xem token có trong blacklist hay không
+ Tính hợp lệ 
+ Thời gian sống
+ Có trong Blacklist hay không

##Các vấn đề khi sử dụng Refresh Token
+ Refresh Token hết hạn => Client xử lý logout -> call API/logout
+ Cấp lại Access Token bằng refresh token -> accessToken cũ vẫn hoạt động được
==> Giải pháp: Khi cấp lại token mới, thêm accessToken cũ vào Blacklist