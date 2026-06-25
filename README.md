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
