# 🌐 DynAsset CDN – Resource Pack Storage Repository

> **Kho lưu trữ tài nguyên động (On-Demand CDN)** phục vụ cho hệ thống **DynAsset Fabric Mod** trên Minecraft & Cobblemon.

---

## 📖 Giới Thiệu

Kho lưu trữ này chứa toàn bộ tài nguyên hình ảnh (Textures, Icons, Skins, GUI, Armor), Model 3D (Bedrock JSON, Geo Models), Dáng đứng (Posers), Chuyển động (Animations) và Âm thanh (.ogg) được bóc tách từ các gói Resource Pack lớn để phục vụ cơ chế **nạp động qua mạng theo thời gian thực (Real-time Dynamic Asset Streaming)**.

Thay vì bắt người chơi phải tải và nạp một gói Resource Pack nặng hàng trăm MB làm tràn bộ nhớ RAM và gây giật lag lúc mở game, **DynAsset** chỉ tải đúng tài nguyên đang xuất hiện trên màn hình thông qua CDN của kho lưu trữ này.

---

## 📊 Thống Kê Toàn Bộ Tài Nguyên (12,052 Files)

* 📦 **SkinBundles Trọn Bộ (`cobblemon_skin`):** `1,235 bundles` (Model 3D + Poser + Animation + Texture)
* 🖼️ **Item Icons 2D (`item_icon`):** `3,614 assets` (Vũ khí, công cụ, item tuỳ chỉnh)
* ⚔️ **Item Models 3D (`item_model`):** `2,972 assets` (Model 3D vật phẩm JSON)
* 🐉 **Bedrock 3D Models (`bedrock_model`):** `1,165 assets` (Khung xương 3D Pokémon/Entity)
* 🎵 **Sound Effects (`sound_effect`):** `158 assets` (Âm thanh chiêu thức, tiếng kêu .ogg)
* 🛡️ **Armor Textures (`armor_layer`):** `62 assets` (Bộ giáp nhân vật)
* 🖼️ **GUI & HUD Elements (`gui_texture`):** `23 assets` (Khung menu, thanh máu, giao diện)
* 🌐 **Generic Assets (`generic` & `generic_model`):** `1,345 assets`

---

## 📂 Cấu Trúc Thư Mục

```text
DynAsset-rsp/
├── pack.mcmeta                 # Metadata Resource Pack chuẩn
├── pack.png                    # Icon hiển thị Resource Pack
├── polymer_armor_shader/       # Shader overlays
└── assets/
    ├── cobblemon/
    │   ├── bedrock/
    │   │   ├── animations/     # Animation keyframes (.animation.json)
    │   │   ├── models/         # 3D Bedrock Models (.geo.json)
    │   │   ├── posers/         # Dáng đứng & pose logic (.json)
    │   │   ├── species/        # Resolvers liên kết Model + Texture (.json)
    │   │   └── pokemon/        # Resolvers, models & posers theo phân loài
    │   ├── textures/
    │   │   ├── pokemon/        # Skin vân da Pokémon
    │   │   └── poke_balls/     # Skin quả cầu Pokéball
    ├── ci/                     # Custom Items, Weapons, Tools (Models & Textures)
    ├── iconpokemon/            # Pokémon UI Icons
    ├── guidite_server_pack/    # Server Menu & GUI Textures
    ├── minecraft/              # Vanilla Item & Armor Overrides
    └── ... (các namespace phụ trợ khác)
```

---

## 🔗 Cấu Trúc Link CDN Tải Trực Tiếp

Mỗi file trong repo này có thể được truy cập trực tiếp qua mạng toàn cầu qua định dạng:
```text
https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/{path}
```

*Ví dụ:*
- **SkinBundle Resolver:** `https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/assets/cobblemon/bedrock/pokemon/resolvers/0_incineroarblade_base.json`
- **Model 3D (.geo.json):** `https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/assets/cobblemon/bedrock/pokemon/models/incineroarblade.geo.json`
- **Poser (.json):** `https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/assets/cobblemon/bedrock/pokemon/posers/incineroarblade.json`
- **Animation (.animation.json):** `https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/assets/cobblemon/bedrock/pokemon/animations/incineroarblade.animation.json`
- **Texture (.png):** `https://raw.githubusercontent.com/silvadrag/DynAsset-rsp/main/assets/cobblemon/textures/pokemon/incineroarblade/incineroarblade.png`

---

## 🛠️ Tích Hợp & Nạp Vào MariaDB

1. **Import Database:** Mở **HeidiSQL** (kết nối MariaDB), mở file `querrySQL/dynasset_bulk_import.sql` và bấm **F9** để nạp toàn bộ 11,324 assets.
2. **Reload Server Ingame:**
   ```text
   /dynasset system reload
   ```
3. **Gán Skin cho Pokémon:**
   ```text
   /dynasset pokemon skin <player_name> <slot_1_to_6> <bundle_id>
   ```

---

*Phát triển và vận hành bởi **silvadrag** & **Lylee Project**.*