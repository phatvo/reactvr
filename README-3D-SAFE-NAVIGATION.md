# Hiệu chỉnh điểm di chuyển an toàn trong phòng 3D

Bản này đã kéo các vòng tròn xanh trên sàn vào sâu trong phòng, không đặt sát tường.

## Thay đổi chính

- `resources/data/gallery3d.json`: cập nhật `navigationPoints`.
- `index-3d.html`: giảm phạm vi di chuyển camera bằng `movementConfig`.
- Thêm hàm giới hạn camera trong vùng an toàn để hạn chế việc xoay nhìn bị lọt ra sau tường.

## Cách cập nhật

Copy đè các file sau vào repo GitHub Pages hiện tại:

```text
index-3d.html
resources/data/gallery3d.json
README-3D-SAFE-NAVIGATION.md
```

Sau đó push:

```bash
git add .
git commit -m "Move 3D navigation points away from walls"
git push
```

Mở lại:

```text
https://phatvo.github.io/reactvr/index-3d.html
```

Nhấn `Ctrl + F5` để xóa cache trình duyệt.
