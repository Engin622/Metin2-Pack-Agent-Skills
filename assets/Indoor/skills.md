# 🎓 Metin2 Skills: `Indoor` Klasörleri (Zindan ve İç Mekanlar)

`indoordeviltower1`, `indoormonkeydungeon` gibi `indoor` ön ekiyle başlayan klasörler, oyunun dış dünyasından (Outdoor) bağımsız olarak tasarlanmış, kapalı mekanları ve zindanları barındırır.

---

## 🔍 Neleri Yönetir?

### 1. Zindan Mimarisi
Bu klasörler, zindanın duvarlarını, zeminini, kapılarını ve dekoratif objelerini içeren `.gr2` ve `.dds` dosyalarını tutar.
- **`ymir work/zone/`**: Genellikle zindanın statik yapılarını içerir.

### 2. Işık ve Atmosfer (`Environment`)
Zindanlar genellikle karanlık veya sisli bir havaya sahiptir. Her zindan klasörü, o bölgeye özel ışık ayarlarını (`.msenv`) belirleyen verilere işaret eder.

### 3. Katmanlı Yapı
Şeytan Kulesi (`deviltower`) gibi çok katlı zindanlarda, her katın harita verisi bu klasör içindeki alt dizinlerde veya `Outdoor` benzeri bir yapıyla `maps` klasöründe tutulur.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Zindan Tasarımını Değiştirme:
Eğer bir zindanı (Örn: Maymun Zindanı) daha modern bir görünüme kavuşturmak istiyorsan, bu klasör içindeki duvar ve zemin kaplamalarını (`.dds`) daha yüksek çözünürlüklü olanlarla değiştirebilirsin.

### ⚠️ Görünmez Duvarlar:
Zindanlarda yol bulma (Pathfinding) ve çarpışma (Collision) verileri çok kritiktir. Bir duvar modelini değiştirirken eğer çarpışma verisini (`.gr2` içindeki mesh) bozarsan, oyuncular duvarların içinden geçebilir veya boşlukta kalabilir.

---

**Veri Akışı:** `Server (Dungeon Entry)` -> `pack/Indoor*` -> `Oyun Motoru (Renderer)`.
