# Bản 3D có hỗ trợ di chuyển

## File cần copy vào repo

```text
index-3d.html
resources/data/gallery3d.json
```

Giữ nguyên thư mục ảnh hiện tại:

```text
resources/exhibit/exhibit.json
resources/exhibit/1.jpg ... 30.jpg
```

## Cách di chuyển

Trên PC:

```text
W hoặc mũi tên lên    : tiến
S hoặc mũi tên xuống  : lùi
A hoặc mũi tên trái   : sang trái
D hoặc mũi tên phải   : sang phải
Shift                 : đi nhanh
Kéo chuột             : xoay góc nhìn
Lăn chuột             : zoom
```

Trên điện thoại / tablet:

```text
Dùng cụm phím ảo ở góc dưới bên trái để tiến/lùi/trái/phải.
Vuốt màn hình để xoay góc nhìn.
```

## Nút mới trên giao diện

```text
Di chuyển: Bật/Tắt
```

Khi tắt, người xem chỉ có thể xoay/zoom và click ảnh, không di chuyển trong phòng.

## Giới hạn di chuyển

Camera được giới hạn trong phạm vi phòng:

```text
x: -5.15 đến 5.15
z: -4.35 đến 4.35
```

Nếu muốn cho đi rộng hơn/hẹp hơn, sửa trong `index-3d.html`:

```js
const movementConfig = {
  speed: 2.1,
  sprintMultiplier: 2.1,
  minX: -5.15,
  maxX: 5.15,
  minZ: -4.35,
  maxZ: 4.35
};
```

## Cập nhật lên GitHub

```bash
git add .
git commit -m "Add movement controls to 3D gallery"
git push
```

Mở thử:

```text
https://phatvo.github.io/reactvr/index-3d.html
```
