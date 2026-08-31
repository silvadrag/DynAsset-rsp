# 📜 Nhật Ký Tiến Trình Kho Tài Nguyên (DynAsset RSP Progress Log)

Tài liệu này ghi lại toàn bộ quá trình bóc tách, chuẩn hóa, đóng gói và phát hành kho tài nguyên đám mây `DynAsset-rsp` (`exported_assets`).

---

## 📊 Số Liệu Thống Kê Tổng Quan (12,052 Files)
* 📦 **SkinBundles Trọn Bộ (`cobblemon_bundle`):** `1,235 bundles` (Model 3D + Poser + Animation + Texture).
* 🖼️ **Item Icons 2D (`item_icon`):** `3,614 assets` (Vũ khí, công cụ, vật phẩm).
* ⚔️ **Item Models 3D (`item_model`):** `2,972 assets` (Model JSON hiển thị cầm tay/đầu/ground).
* 🐉 **Bedrock 3D Models (`bedrock_model`):** `1,165 assets` (Khung xương `.geo.json` Pokémon/Entity).
* 🎵 **Sound Effects (`sound_effect`):** `158 assets` (Âm thanh `.ogg` chiêu thức, tiếng kêu).
* 🛡️ **Armor Textures (`armor_layer`):** `62 assets` (Bộ giáp nhân vật).
* 🖼️ **GUI & HUD Elements (`gui_texture`):** `23 assets` (Giao diện, menu, khung thoại).
* 🌐 **Generic Assets (`generic` & `generic_model`):** `1,345 assets`.

---

## 📅 Các Cột Mốc Đã Hoàn Thành

### 📌 Cột Mốc 1: Phân Tích & Bóc Tách Toàn Diện
- Phân tích file zip gốc `resource_pack (44).zip` chứa toàn bộ tài nguyên Cobblemon của server.
- Sử dụng script Python quét đệ quy toàn bộ thư mục `assets/` để lập chỉ mục định danh và đường dẫn.

### 📌 Cột Mốc 2: Đóng Gói 1,235 Skin Thành Single-Zip Bundles
- Gom cụm tự động 4 thành phần cho mỗi skin:
  - Model hình học 3D (`.geo.json`)
  - Định nghĩa tư thế (`.json` poser)
  - Hoạt cảnh chuyển động (`.animation.json`)
  - Texture bề mặt (`.png`)
- Tạo file `manifest.json` chứa metadata chính xác: `species`, `aspects`, `layers`, `modelKey`, `poserKey`.
- Nén độc lập từng skin thành file `.zip` đặt trong thư mục `bundles/` với dung lượng siêu nhẹ (10KB - 80KB/bundle).

### 📌 Cột Mốc 3: Lập Bảng Dữ Liệu SQL & Tính Mã Băm SHA-256
- Tính toán mã băm SHA-256 cho từng file tài nguyên để bảo vệ toàn vẹn và hỗ trợ kiểm tra cache client.
- Tạo file `seed_assets.sql` nạp tự động toàn bộ 12,052 assets vào MariaDB `dynasset_registry`.

### 📌 Cột Mốc 4: Đẩy Kho Lưu Trữ Lên GitHub Cloud CDN
- Xuất bản repository [`silvadrag/DynAsset-rsp`](https://github.com/silvadrag/DynAsset-rsp) hoạt động như một Cloud CDN tốc độ cao phục vụ tính năng On-Demand Streaming cho người chơi Minecraft.
