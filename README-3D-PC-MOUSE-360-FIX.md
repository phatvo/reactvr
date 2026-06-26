# Fix PC mouse 360 rotation

Bản cập nhật này sửa lỗi chuột trên PC:

- Drag chuột xoay ngang đủ 360 độ.
- Camera giữ nguyên vị trí đang đứng khi drag chuột.
- Không dùng OrbitControls để orbit quanh tâm phòng nên không còn bị kéo view/camera ra ngoài phòng.
- Giữ nguyên thao tác drag ngón tay trên điện thoại, cảm biến, click-to-move và phòng 20m x 20m x 6m.

Nếu muốn đảo chiều chuột, sửa trong `index-3d.html`:

```js
const lookConfig = {
  mouseXSign: -1,
  mouseYSign: 1
};
```

Đổi `-1` thành `1` hoặc ngược lại cho từng trục.
