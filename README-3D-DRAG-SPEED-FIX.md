# Fix tốc độ xoay khi drag tay trên điện thoại

Bản này giảm tốc độ xoay khi kéo ngón tay trên mobile.

File chỉnh:

```text
index-3d.html
```

Thông số chính:

```js
const lookConfig = {
  sensitivity: 0.0026
};
```

Nếu vẫn nhanh, giảm còn `0.0020`. Nếu quá chậm, tăng lên `0.0030`.
