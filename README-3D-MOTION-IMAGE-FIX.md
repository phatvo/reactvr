# Fix hiệu ứng ảnh bị bể khi di chuyển

Bản này tối ưu phần ảnh treo trong phòng 3D khi người dùng đang di chuyển/xoay camera.

Các thay đổi chính:

- Đẩy mặt ảnh ra khỏi khung/nền xa hơn để tránh z-fighting/flicker.
- Bật polygonOffset cho material ảnh.
- Tắt depthWrite cho ảnh để hạn chế nhấp nháy khi camera di chuyển.
- Tăng renderOrder của ảnh so với khung.
- Tối ưu texture: mipmap, LinearMipmapLinearFilter, LinearFilter, anisotropy.
- Giới hạn pixelRatio trên mobile để giảm tải GPU khi phòng 20m x 20m x 6m.

Nếu ảnh vẫn còn mờ/vỡ trên điện thoại yếu, nên nén ảnh trưng bày về khoảng 1200-1600px chiều ngang thay vì ảnh quá lớn.
