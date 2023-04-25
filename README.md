# team-project-n1_11

1, Quy trình mô hình hoá dịch vụ REST:

![Picture1](https://user-images.githubusercontent.com/101632970/228398948-7d7d0ebd-0f4b-4977-b8d3-4baaada0c1dc.png)

 
Bước 1, Phân tách quy trình thành các hành động chi tiết:
  - Bắt đầu quy trình đặt vé
  - Lấy thông tin rạp (gồm danh sách phim, suất chiếu, vị trí ghế)
  - Khách hàng chọn phim, suất chiếu, số ghế theo nhu cầu
  - Xác định xem sự kiện có hợp lệ hay không?
  - Nếu sự kiện không hợp lệ (VD: ghế đã được đặt,…) thì quay lại bước 2
  - Xác định xem khách hàng có xác nhận hành động đặt vé và thanh toán không?
  - Nếu khách hàng từ chối xác nhận thì kết thúc chương trình
  - Xác minh từ chối thủ công
  - Gửi email chứa thông tin vé về email khách hàng đăng ký
  - Xác nhận chấp nhận thủ công
  - Cập nhật lại dữ liệu rạp phim trong cơ sở dữ liệu
  - Kết thúc quy trình
  
Bước 2, Lọc bỏ các hành động không phù hợp:
  - Bắt đầu quy trình đặt vé
  - Lấy thông tin rạp (gồm danh sách phim, suất chiếu, vị trí ghế)
  - Khách hàng chọn phim, suất chiếu, số ghế theo nhu cầu
  - Xác định xem sự kiện có hợp lệ hay không?
  - Nếu sự kiện không hợp lệ (VD: ghế đã được đặt,…) thì quay lại bước 2
  - Xác định xem khách hàng có xác nhận hành động đặt vé và thanh toán không?
  - Nếu khách hàng từ chối xác nhận thì kết thúc chương trình
  - Gửi email chứa thông vé về email khách hàng đăng ký
  - Cập nhật lại dữ liệu rạp phim trong cơ sở dữ liệu
  - Kết thúc quy trình
  
Bước 3, Xác định các ứng viên dịch vụ thực thể:
Từ bước 2, xác định các hành động bất khả tri. Các hành động bất khả tri là các ứng viên khả năng dịch vụ tương ứng với các ứng viên dịch vụ. Từ đó, ta xác 
định được các ứng viên dịch vụ như sau:
  - Ứng viên dịch vụ Rạp phim:
  
  ![image](https://user-images.githubusercontent.com/101632970/229849483-5f37df83-c59b-4809-a2e3-84f345db69ce.png)


 - Ứng viên dịch vụ Vé:
 
  ![image](https://user-images.githubusercontent.com/101632970/229850936-09f36595-6d4d-4625-80c2-5b807ee48adc.png)


 - Ứng viên dịch vụ Khách Hàng:
 
  ![image](https://user-images.githubusercontent.com/101632970/229851153-95b465b3-b2af-4cb3-aba9-816dd6b2d172.png)

 Bước 4: Xác định logic cụ thể của quy trình:
 Các hành động KHÔNG bất khả tri dành riêng cho quá trình "Đặt vé xem phim":
  - Bắt đầu quy trình đặt vé
  - Xác định xem sự kiện khách hàng đặt vé có hợp lệ không, nếu không quay lại bước lấy thông tin rạp
  - Xác định xem khách hàng có xác nhận hành động đặt vé và thanh toán không, nếu không kết thúc quy trình
  
 Hành động 2 và 3 được xác định là logic bên trong của dịch vụ thực thể Đặt vé xem phim.
 Do đó, ứng viên dịch vụ tác vụ Đặt vé xem phim:
 
 ![image](https://user-images.githubusercontent.com/101632970/229856595-0c68aad5-6091-4256-aefb-6878ac67ff23.png)

 Bước 5: Liên kết khả năng dịch vụ với tài nguyên và phương pháp:
 
  - Ứng viên dịch vụ tác vụ Đặt vé xem phim:
  
  ![image](https://user-images.githubusercontent.com/101632970/229863779-85cf3c3a-bbe9-474d-9707-85bd989cd238.png)

 - Ứng viên dịch vụ thực thể Rạp phim:
 
 ![image](https://user-images.githubusercontent.com/101632970/229863890-73ac1dbb-dc42-40b2-bdb9-18d4732566e8.png)

 - Ứng viên dịch vụ thực thể Vé:
 
 ![image](https://user-images.githubusercontent.com/101632970/229864020-c3e086a0-9eac-43c7-8605-f348796d9602.png)

 - Ứng viên dịch vụ thực thể Khách hàng:
 
 ![image](https://user-images.githubusercontent.com/101632970/229864150-232e68f7-f8b9-4d5f-961f-5407760a0ddd.png)

Bước 6: Xác định ứng viên thành phần dịch vụ:

![image](https://user-images.githubusercontent.com/101632970/229868902-04bff86c-3368-4edd-bb57-defc35ffa6a3.png)

Bước 7: Xác định ứng viên dịch vụ tiện ích (và liên kết với tài nguyên và phương pháp):
Ứng viên dịch vụ tiện ích Gửi Email:

![image](https://user-images.githubusercontent.com/101632970/229872179-20f02213-6a85-42af-af4d-c3bee240563c.png)

Bước 8: Xác định ứng viên dịch vụ vi mô (và liên kết với tài nguyên và phương pháp):
Ứng viên dịch vụ vi mô xác nhận đặt vé:

![image](https://user-images.githubusercontent.com/101632970/229872859-6b5684d4-3864-4625-97f3-01e7d6d7c38b.png)

Ứng viên dịch vụ vi mô xác nhận thanh toán:

![image](https://user-images.githubusercontent.com/101632970/229873029-45d930a7-702f-4fe6-aad6-516fc913a626.png)


Bước 9, Sửa đổi thành phần dịch vụ Đặt vé xem phim


![Picture2](https://user-images.githubusercontent.com/101632970/228401721-d6a2fc26-9893-4824-9f5f-e6bb0006980e.png)


Ngôn ngữ dự định sử dụng: ASP .Net
