# Fix chiều kéo ngón tay trên điện thoại

Bản này chỉnh lại phần xoay view bằng ngón tay trên mobile trong `index-3d.html`.

Các tham số nằm trong `lookConfig`:

```js
dragXSign: -1,
dragYSign: 1
```

Nếu sau khi test muốn đảo riêng chiều ngang hoặc chiều dọc, đổi dấu `1` thành `-1` hoặc ngược lại.

Bản này vẫn giữ cơ chế xoay ngang không giới hạn 360 độ.
