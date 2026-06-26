# Nâng cấp ReactVR 360 sang phòng trưng bày 3D

Bộ file này dùng để nâng cấp repo `phatvo/reactvr` từ mô hình ảnh nền 360 sang một prototype phòng trưng bày 3D.

## File mới

```text
index-3d.html
resources/data/gallery3d.json
```

## Cách dùng nhanh trên GitHub Pages

1. Chép `index-3d.html` vào root repo, cùng cấp với `index.html` hiện tại.
2. Chép `resources/data/gallery3d.json` vào `resources/data/`.
3. Giữ nguyên thư mục ảnh hiện có:

```text
resources/exhibit/
├─ exhibit.json
├─ 1.jpg
├─ 2.jpg
├─ ...
└─ 30.jpg
```

4. Commit và push:

```bash
git add .
git commit -m "Add 3D gallery room prototype"
git push
```

5. Mở thử:

```text
https://phatvo.github.io/reactvr/index-3d.html
```

Nếu muốn dùng bản 3D làm trang chính, sau khi test ổn thì đổi tên:

```text
index.html      -> index-360.html
index-3d.html   -> index.html
```

## Ý tưởng layout

Phòng 3D có 5 ngách trưng bày:

```text
Ngách 1: ảnh 1  - 6
Ngách 2: ảnh 7  - 12
Ngách 3: ảnh 13 - 18
Ngách 4: ảnh 19 - 24
Ngách 5: ảnh 25 - 30
```

Mỗi ngách bố trí 2 hàng x 3 cột.

## Chỉnh vị trí ngách

Sửa file:

```text
resources/data/gallery3d.json
```

Ví dụ:

```json
{
  "id": "niche-1",
  "title": "Góc kỷ niệm 1",
  "items": ["1", "2", "3", "4", "5", "6"],
  "position": [-3.65, 1.72, -4.92],
  "rotation": [0, 0, 0],
  "size": [2.8, 2.25],
  "photoSize": [0.74, 0.50]
}
```

Ý nghĩa:

- `position`: vị trí ngách trong phòng 3D.
- `rotation`: góc xoay ngách.
- `size`: kích thước mảng ngách.
- `photoSize`: kích thước từng ảnh trong ngách.
- `items`: danh sách id ảnh lấy từ `resources/exhibit/exhibit.json`.

## Ghi chú

- Bản này chạy tĩnh trên GitHub Pages, không cần `npm install`, không cần build.
- Dùng Three.js từ CDN để dễ chạy như bản 360 hiện tại.
- Dữ liệu ảnh vẫn dùng `resources/exhibit/exhibit.json` hiện tại.


## Bản fix loading lâu

File `index-3d.html` đã dùng `importmap` với CDN jsDelivr để OrbitControls resolve được module `three`. Nếu màn hình đứng ở “Đang tải phòng 3D...”, mở F12 > Console để kiểm tra lỗi CDN/CORS/404.
