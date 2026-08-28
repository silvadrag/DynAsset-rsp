# 🌐 DynAsset CDN – Resource Pack Storage Repository

> **Kho lưu trữ tài nguyên động (On-Demand CDN)** phục vụ cho hệ thống **DynAsset Fabric Mod** trên Minecraft & Cobblemon.

---

## 📖 Giới thiệu

Kho lưu trữ này chứa toàn bộ tài nguyên hình ảnh (Textures, Icons, Skins, GUI, Armor) được bóc tách từ các gói Resource Pack lớn để phục vụ cơ chế **nạp động qua mạng theo thời gian thực (Real-time Dynamic Loading)**.

Thay vì bắt người chơi phải tải và nạp một gói Resource Pack nặng hàng trăm MB làm tràn bộ nhớ RAM và gây giật lag lúc mở game, **DynAsset** chỉ tải đúng tài nguyên đang xuất hiện trên màn hình thông qua CDN của kho lưu trữ này.

---

## 📊 Thống kê Tài nguyên

* 🖼️ **Tổng số lượng Texture:** `6,269+ files PNG`
* ⚡ **Pokemon Skins (`cobblemon_skin`):** `1,899 assets` (Skins Pokemon Cobblemon)
* ⚔️ **Items & Weapons (`item_icon`):** `3,378 assets` (Vũ khí, công cụ, item tuỳ chỉnh)
* 🛡️ **Armor Textures (`armor_layer`):** `62 assets` (Bộ giáp nhân vật)
* 🖼️ **GUI & HUD Elements (`gui_texture`):** `23 assets` (Khung menu, thanh máu, giao diện)
* 🌐 **Generic Textures (`generic`):** `907 assets`

---

## 📂 Cấu trúc Thư mục

```text
DynAsset-rsp/
└── assets/
    ├── cobblemon/              # Textures Pokemon, Pokéballs, Animations
    ├── ci/                     # Custom Items, Weapons, Tools
    ├── iconpokemon/            # Pokemon UI Icons
    ├── guidite_server_pack/    # Server Menu & GUI Textures
    ├── minecraft/              # Vanilla Item & Armor Overrides
    └── ... (các gói plugin & mod khác)
```

---

## 🔗 Cấu trúc Link CDN Tải trực tiếp

Mỗi file trong repo này có thể được truy cập trực tiếp qua mạng toàn cầu qua định dạng:
```text
https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/assets/<namespace>/textures/<path>/<file>.png
```

*Ví dụ:*
* **Pikachu Base:** `https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/assets/cobblemon/textures/pokemon/0025_pikachu/pikachu.png`

---

## 🛠️ Tích hợp & Quản trị (DynAsset Mod)

Để sử dụng tài nguyên từ kho này trong server Minecraft:

1. **Nạp dữ liệu:** Chạy file `dynasset_bulk_import.sql` trong MariaDB qua HeidiSQL.
2. **Reload Server:**
   ```text
   /dynasset reload
   ```
3. **Gán Skin cho Pokémon:**
   ```text
   /dynasset giveskin <player_name> <slot_1_to_6> <asset_id>
   ```

---

*Phát triển và vận hành bởi **silvadrag** & **Lylee Project**.*