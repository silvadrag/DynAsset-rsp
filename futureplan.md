# 🚀 Kế Hoạch Mở Rộng Kho Tài Nguyên CDN (DynAsset RSP Future Plan)

Tài liệu này định hướng phát triển và tự động hóa cho kho lưu trữ Resource Pack CDN (`DynAsset-rsp`).

---

## 🔮 1. Tự Động Hóa CI/CD GitHub Actions
* 🤖 **Auto-Packaging Workflow:** Thiết lập GitHub Action tự động khi có commit file model/texture mới vào nhánh `main`:
  - Tự động phát hiện cấu trúc skin và nén thành `bundles/<skin_name>.zip`.
  - Tự động sinh file `manifest.json`.
  - Tự động tính mã băm SHA-256.
  - Tự động cập nhật file SQL `seed_assets.sql` hoặc gọi Webhook đồng bộ trực tiếp vào MariaDB của server game.

---

## ⚡ 2. Nén Nâng Cao & Tối Ưu Băng Thông (Modern Image Compression)
* Thử nghiệm nén không suy hao (lossless/near-lossless) cho textures:
  - Tối ưu hóa PNG bằng `pngquant` / `oxipng` giúp giảm 30-50% dung lượng file ảnh mà không làm mờ texture.
  - Thử nghiệm định dạng WebP cho các icon/menu GUI.

---

## 🛡️ 3. Hạ Tầng Lưu Trữ Đa Vùng (Multi-CDN Mirroring)
* Tích hợp kho lưu trữ phụ (Cloudflare R2 / Backblaze B2) song song với GitHub Raw CDN.
* Giúp tăng tốc độ tải tài nguyên tại Việt Nam và đảm bảo kết nối 100% không bị ảnh hưởng khi có sự cố mạng quốc tế.
