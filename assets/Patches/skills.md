# 🎓 Metin2 Skills: `metin2_patch_*` Klasörleri (Güncelleme ve Eklenti Sistemi)

`metin2_patch_dragon_rock`, `metin2_patch_etc` gibi isimlerle başlayan klasörler, oyunun orijinal sürümünün üzerine eklenen güncellemeleri, yeni sistemleri ve sezonluk içerikleri barındıran "yama" (Patch) dosyalarıdır.

---

## 🔍 Neleri Yönetir?

### 1. Yeni İçerik Dağıtımı
Metin2 istemcisi modüler bir yapıya sahiptir. Mevcut `item` veya `Monster` klasörünü her seferinde devasa bir şekilde güncellemek yerine, yeni gelen içerikler (Örn: Ejderha Ateşi Burnu canavarları) ayrı bir patch klasöründe tutulur.
- **`metin2_patch_dragon_rock`**: Yeni harita nesneleri ve zeminleri.
- **`metin2_patch_costume`**: Yeni eklenen kostümler ve saç stilleri.

### 2. `Index` Dosyası Önceliği
`pack` klasöründeki `Index` dosyası, hangi dosyanın daha öncelikli olduğunu belirler. Eğer aynı isimli bir dosya hem ana klasörde hem de bir patch klasöründe varsa, oyun genellikle patch klasöründekini (En güncel olanı) yükler.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Yeni Sistem Ekleme:
Kendi sunucuna yeni bir sistem (Örn: Kuşak Sistemi) eklediğinde, tüm dosyaları `metin2_patch_kuşak` gibi yeni bir klasöre koyup `Index` dosyasına en üste eklemek en temiz yöntemdir.

### ⚠️ Bağımlılıklar:
Patch klasörleri genellikle bağımsız görünse de, içindeki modeller (`.gr2`) ana klasörlerdeki veya diğer patchlerdeki kaplamalara (`.dds`) ihtiyaç duyabilir.

---

**Veri Akışı:** `pack/Index` -> `pack/metin2_patch_*` -> `Oyun Motoru`.
