# R3F 360 VR Tour - GitHub Pages

Project demo web tĩnh để upload trực tiếp lên GitHub Pages. Không cần `npm install`, không cần build.

## Cấu trúc thư mục

```text
r3f-github-pages-vr360/
├─ index.html
├─ .nojekyll
├─ README.md
└─ resources/
   ├─ bg/
   │  ├─ gallery.json
   │  ├─ sample-control-room-360.jpg
   │  └─ sample-substation-360.jpg
   ├─ data/
   │  └─ scenes.json
   ├─ exhibit/
   │  ├─ exhibit.json
   │  ├─ exhibit-scada-diagram.jpg
   │  ├─ exhibit-operation-process.jpg
   │  └─ exhibit-equipment-photo.jpg
   └─ video/
      └─ videos.json
```

## Cách upload lên GitHub Pages

1. Tạo repository mới trên GitHub, ví dụ: `r3f-vr-demo`.
2. Upload toàn bộ nội dung trong thư mục này lên repository. Lưu ý: `index.html` phải nằm ở root repository.
3. Vào repository > Settings > Pages.
4. Source: chọn `Deploy from a branch`.
5. Branch: chọn `main`, folder: `/root`.
6. Save và chờ GitHub Pages build xong.

Sau khi publish, app thường có dạng:

```text
https://<username>.github.io/<repo>/
```

## Cách thêm ảnh 360

Ảnh nên là equirectangular, tỷ lệ 2:1, ví dụ:

```text
4096x2048
8192x4096
```

Khuyến nghị đặt tên không dấu, không khoảng trắng:

```text
phong-dieu-khien.jpg
tram-500kv.jpg
nha-may-dien.jpg
```

Thực hiện:

1. Chép ảnh vào `resources/bg/`.
2. Thêm ảnh vào `resources/bg/gallery.json`.
3. Thêm hoặc sửa scene tương ứng trong `resources/data/scenes.json`.

Ví dụ `gallery.json`:

```json
{
  "id": "phong-dieu-khien",
  "sceneId": "phong-dieu-khien",
  "title": "Phòng điều khiển",
  "description": "Ảnh 360 phòng điều khiển.",
  "file": "phong-dieu-khien.jpg"
}
```

Ví dụ scene trong `scenes.json`:

```json
{
  "id": "phong-dieu-khien",
  "title": "Phòng điều khiển",
  "image": "phong-dieu-khien.jpg",
  "hotspots": []
}
```

## Cách thêm hotspot

Hotspot nằm trong mỗi scene ở file `resources/data/scenes.json`.

### Hotspot thông tin

```json
{
  "id": "hs-tu-scada",
  "type": "info",
  "title": "Tủ SCADA",
  "description": "Mô tả tủ SCADA.",
  "yaw": -35,
  "pitch": 2
}
```

### Hotspot mở YouTube

```json
{
  "id": "hs-video",
  "type": "video",
  "title": "Video hướng dẫn",
  "youtubeUrl": "https://www.youtube.com/watch?v=VIDEO_ID",
  "yaw": 28,
  "pitch": 5
}
```

### Hotspot chuyển cảnh

```json
{
  "id": "hs-next",
  "type": "navigate",
  "title": "Sang phòng máy",
  "targetSceneId": "phong-may",
  "yaw": 0,
  "pitch": -8
}
```

## Cách chỉnh vị trí hotspot

- `yaw`: góc ngang, đơn vị độ.
  - `0`: phía trước.
  - `90`: bên phải.
  - `-90`: bên trái.
  - `180`: phía sau.
- `pitch`: góc dọc, đơn vị độ.
  - Dương: lên trên.
  - Âm: xuống dưới.

## Cách thêm video vào panel

Sửa file `resources/video/videos.json`:

```json
{
  "title": "Video hướng dẫn thao tác",
  "description": "Mô tả ngắn.",
  "url": "https://youtu.be/VIDEO_ID"
}
```

Video YouTube sẽ mở bằng iframe overlay.

## Chạy thử local

Vì app dùng `fetch()` để đọc JSON, nếu mở trực tiếp bằng `file://` có thể không đọc được JSON. Để test đúng như GitHub Pages, chạy local server:

```bat
python -m http.server 8080
```

Mở:

```text
http://localhost:8080
```

Khi upload lên GitHub Pages thì không cần chạy server trên máy bạn.

## Ảnh trưng bày kiểu 3D trong phòng điều khiển

Project đã hỗ trợ `imagePlanes`: ảnh được render như một khung ảnh/biển trưng bày nổi trong không gian 360.

Dữ liệu ảnh trưng bày được tách riêng trong:

```text
resources/exhibit/exhibit.json
```

Ví dụ `resources/exhibit/exhibit.json`:

```json
{
  "id": "scada-diagram",
  "title": "Sơ đồ SCADA",
  "description": "Ảnh trưng bày dạng khung 3D. Click vào khung để xem ảnh lớn trong popup.",
  "file": "exhibit-scada-diagram.jpg",
  "category": "Phòng điều khiển"
}
```

Còn vị trí khung ảnh trong từng phòng/scene nằm trong `resources/data/scenes.json`:

```json
{
  "id": "imgplane-scada-diagram",
  "type": "imagePlane",
  "exhibitId": "scada-diagram",
  "yaw": -55,
  "pitch": 8,
  "distance": 7.5,
  "size": [2.8, 1.58]
}
```

Ý nghĩa cấu hình:

- `exhibitId`: liên kết tới `id` trong `resources/exhibit/exhibit.json`.
- `file`: tên ảnh trong `resources/exhibit/`, khai báo trong `exhibit.json`.
- `yaw`: vị trí ngang quanh phòng, đơn vị độ.
- `pitch`: vị trí cao/thấp, đơn vị độ.
- `distance`: khoảng cách khung ảnh so với camera ở tâm.
- `size`: kích thước khung ảnh trong không gian 3D, dạng `[rộng, cao]`.

Cách thêm ảnh trưng bày mới:

1. Chép ảnh vào `resources/exhibit/`, nên đặt tên không dấu và không khoảng trắng.
2. Mở `resources/exhibit/exhibit.json`, thêm một object mới gồm `id`, `title`, `description`, `file`.
3. Mở `resources/data/scenes.json`, thêm một object trong `imagePlanes` của scene cần hiển thị.
4. Gán `exhibitId` bằng đúng `id` đã khai báo trong `exhibit.json`.
5. Điều chỉnh `yaw`, `pitch`, `distance`, `size` nếu cần.
6. Commit và push lên GitHub.
