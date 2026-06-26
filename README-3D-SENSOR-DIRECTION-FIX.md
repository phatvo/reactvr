# Fix chiều cảm biến điện thoại

Bản này đã đảo chiều yaw của cảm biến để khi xoay điện thoại sang phải, view quay sang phải.

Cấu hình nằm trong `index-3d.html`:

```js
const sensorConfig = {
  yawSign: 1,
  pitchSign: 1
};
```

Nếu một dòng máy cụ thể vẫn bị ngược chiều ngang, đổi `yawSign` thành `-1`.
Nếu chiều nghiêng lên/xuống bị ngược, đổi `pitchSign` thành `-1`.
