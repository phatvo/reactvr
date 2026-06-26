# ReactVR 3D Gallery - Click to Move

Bản này bổ sung component di chuyển dạng vòng tròn xanh trên sàn.

## Cách dùng

- Click vòng tròn xanh trên sàn để di chuyển nhanh đến khu vực tương ứng.
- Dùng W/A/S/D hoặc phím mũi tên để đi bộ thủ công.
- Kéo chuột để xoay góc nhìn.
- Click ảnh trưng bày để mở popup ảnh lớn.
- Có nút `Điểm di chuyển: Hiện/Ẩn` để bật/tắt các điểm di chuyển.

## File cần copy vào repo

- `index-3d.html`
- `resources/data/gallery3d.json`
- `README-3D-CLICKMOVE.md` nếu muốn lưu hướng dẫn.

## Cấu hình điểm di chuyển

Trong `resources/data/gallery3d.json`:

```json
{
  "id": "move-front",
  "title": "Tường trung tâm",
  "position": [0, 0.045, -2.35],
  "cameraPosition": [0, 1.7, -2.35],
  "target": [0, 1.55, -5]
}
```

Ý nghĩa:

- `position`: vị trí vòng tròn xanh trên sàn.
- `cameraPosition`: vị trí camera sau khi click.
- `target`: hướng nhìn sau khi di chuyển.
