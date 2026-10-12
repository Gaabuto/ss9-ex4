# Bài 4: Lưu trữ dữ liệu đơn giản với Docker Volume

## 1. Mục tiêu

* Tạo Named Volume có tên `easy-volume`.
* Ghi dữ liệu vào Volume bằng container Alpine.
* Sử dụng container Alpine thứ hai để đọc lại dữ liệu.
* Kiểm tra dữ liệu vẫn tồn tại sau khi container đầu tiên kết thúc.

## 2. Tạo Docker Volume

Chạy lệnh:

```bash
docker volume create easy-volume
```

Kiểm tra danh sách Volume:

```bash
docker volume ls
```

Kết quả mong đợi: xuất hiện Volume có tên `easy-volume`.

## 3. Ghi dữ liệu vào Volume

Chạy container Alpine để ghi nội dung vào tệp `/data/test.txt`:

```bash
docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
```

Giải thích:

* `--rm`: Tự động xóa container sau khi lệnh hoàn thành.
* `-v easy-volume:/data`: Gắn Volume `easy-volume` vào thư mục `/data` trong container.
* `alpine`: Sử dụng image Alpine Linux nhẹ.
* `sh -c`: Thực thi lệnh shell bên trong container.
* `echo`: Ghi nội dung vào tệp `test.txt`.

Sau khi lệnh hoàn thành, container đầu tiên sẽ kết thúc và bị xóa, nhưng dữ liệu trong Named Volume vẫn được giữ lại.

## 4. Đọc lại dữ liệu từ Volume

Sử dụng một container Alpine khác để đọc tệp đã lưu:

```bash
docker run --rm -v easy-volume:/data alpine cat /data/test.txt
```

Kết quả mong đợi:

```text
Luu tru du lieu Docker
```

Kết quả cho thấy dữ liệu vẫn tồn tại mặc dù container dùng để ghi dữ liệu đã kết thúc và bị xóa.

## 5. Kết luận

Đã tạo thành công Named Volume `easy-volume`, ghi dữ liệu vào Volume bằng một container Alpine và đọc lại dữ liệu bằng một container khác.

Docker Volume giúp lưu trữ dữ liệu độc lập với vòng đời của container, do đó dữ liệu vẫn tồn tại sau khi container bị dừng hoặc xóa.
