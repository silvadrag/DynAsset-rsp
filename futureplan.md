# 🚀 Kế Hoạch Mở Rộng Kho Tài Nguyên CDN (DynAsset RSP Future Plan)

Tài liệu này định hướng phát triển và tự động hóa cho kho lưu trữ Resource Pack CDN (`DynAsset-rsp`).

---

## 📌 BẢNG TRẠNG THÁI HẠ TẦNG CDN

| Hạng mục | Trạng thái | Chi tiết |
| :--- | :---: | :--- |
| **Bóc tách & Lập chỉ mục 12,052 assets** | ✅ **HOÀN THÀNH** | Đã gom thành 1,235 Pokemon Bundles, 3,614 Icons, 2,972 Models 3D... |
| **Tính mã băm SHA-256 & Sinh SQL** | ✅ **HOÀN THÀNH** | File `querrySQL/dynasset_bulk_import.sql` đã sẵn sàng nạp. |
| **Xuất bản Cloud CDN GitHub** | ✅ **HOÀN THÀNH** | Repository `silvadrag/DynAsset-rsp` nạp trực tiếp qua Raw GitHub CDN. |
| **Tự động hóa CI/CD GitHub Actions** | ⏳ **ĐANG CHỜ** | Tự đóng gói bundle và sinh SHA-256 khi có commit file mới. |
| **Nén Texture Lossless Nâng Cao** | ⏳ **ĐANG CHỜ** | Tối ưu PNG bằng `oxipng` / `pngquant` giảm 30-50% băng thông. |
| **Hạ tầng Multi-CDN (Cloudflare R2)** | ⏳ **KẾ HOẠCH TƯƠNG LAI** | Mirror dữ liệu tăng tốc độ tải tại Việt Nam. |

---

## 🔮 CÁC MỤC TIÊU PHÁT TRIỂN TIẾP THEO

### 🤖 1. Tự Động Hóa CI/CD GitHub Actions
- Thiết lập GitHub Action tự động khi có commit file model/texture mới vào nhánh `main`:
  - Tự động phát hiện cấu trúc skin và nén thành `bundles/<skin_name>.zip`.
  - Tự động sinh file `manifest.json`.
  - Tự động tính mã băm SHA-256.
  - Tự động cập nhật file SQL `dynasset_bulk_import.sql` hoặc gọi Webhook đồng bộ trực tiếp vào MariaDB của server game.

---

### ⚡ 2. Nén Nâng Cao & Tối Ưu Băng Thông (Modern Image Compression)
- Thử nghiệm nén không suy hao (lossless/near-lossless) cho textures:
  - Tối ưu hóa PNG bằng `pngquant` / `oxipng` giúp giảm 30-50% dung lượng file ảnh mà không làm mờ texture.
  - Thử nghiệm định dạng WebP cho các icon/menu GUI.

---

### 🛡️ 3. Hạ Tầng Lưu Trữ Đa Vùng (Multi-CDN Mirroring)
- Tích hợp kho lưu trữ phụ (Cloudflare R2 / Backblaze B2) song song với GitHub Raw CDN.
- Giúp tăng tốc độ tải tài nguyên tại Việt Nam và đảm bảo kết nối 100% không bị ảnh hưởng khi có sự cố mạng quốc tế.
