# Fix touch drag xoay 360 tại chỗ

Bản này chỉnh thao tác drag ngón tay trên điện thoại:

- Drag ngón tay chỉ xoay góc nhìn.
- Camera giữ nguyên vị trí hiện tại trong phòng.
- Xoay ngang không giới hạn 360 độ.
- Không orbit quanh tâm phòng, không pan, không tự dịch chuyển khi drag.

File cần copy lên repo:

```text
index-3d.html
resources/data/gallery3d.json
```

Cập nhật GitHub Pages:

```bash
git add .
git commit -m "Keep camera position while touch dragging"
git push
```
