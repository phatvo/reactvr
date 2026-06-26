# Fix xoay ngang 360 trên điện thoại

Bản này sửa phần điều khiển góc nhìn trên điện thoại:

- Không dùng OrbitControls để xoay bằng ngón tay trên mobile.
- Dùng cơ chế xoay nhìn tại chỗ bằng pointer/touch riêng.
- Kéo tay sang phải thì góc nhìn quay sang phải.
- Kéo tay lên thì góc nhìn quay lên.
- Yaw không bị giới hạn, cho phép xoay ngang đủ 360 độ ở mọi vị trí trong phòng.
- Giữ lại click ảnh, click điểm di chuyển, cảm biến điện thoại và cụm phím ảo.

## Cập nhật lên GitHub

Copy đè các file trong gói này vào repo, sau đó chạy:

```bash
git add .
git commit -m "Fix mobile 360 horizontal rotation"
git push
```

Sau khi GitHub Pages deploy xong, mở lại trang trên điện thoại bằng tab ẩn danh hoặc refresh mạnh để tránh cache.
