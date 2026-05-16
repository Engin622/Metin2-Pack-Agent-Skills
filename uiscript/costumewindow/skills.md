# 🎓 Metin2 Skills: `costumewindow.py` (Kostüm Sistemi)

`costumewindow.py`, envanterin yanında açılan ve karakterin giydiği kostüm, saç stili ve kostüm silahı gibi görsellik odaklı ekipmanları yöneten penceredir.

---

## 🔍 Neleri Yönetir?

### 1. Kostüm Slotları (`CostumeSlot`)
Ana envanterden bağımsız olarak 3 ana slot barındırır:
- **`COSTUME_START_INDEX+0`**: Kostüm zırhı (Body).
- **`COSTUME_START_INDEX+1`**: Kostüm saçı (Hair).
- **`COSTUME_START_INDEX+2`**: Kostüm silahı veya binek (Server yapısına göre değişir).

### 2. Arka Plan Görseli (`costume_bg.jpg`)
Slotların arkasında yer alan ve genellikle şık bir kostüm figürü içeren tematik arka plan görselidir.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Yeni Kostüm Slotu Ekleme:
Eğer sunucuna "Kuşak" (Sash) veya "Pet" gibi sistemler eklemek istiyorsan, bu pencereyi genişleterek yeni slotlar tanımlayabilirsin. `COSTUME_START_INDEX` değerini `item.py` içindeki tanımlara göre artırmalısın.

### ⚠️ Hizalama:
Bu pencere genellikle envanterin solunda açılacak şekilde (`SCREEN_WIDTH - 175 - 140`) konumlandırılmıştır. Envanterin yerini değiştirirsen bu pencerenin de koordinatlarını güncellemelisin.

---

## 📉 costumewindow.py Tasarım Hiyerarşisi
```mermaid
graph TD
    A[CostumeWindow] --> B[Board: Küçük Panel]
    B --> C[TitleBar: "Kostüm"]
    B --> D[Costume_Base: Arka Plan Resmi]
    D --> E[CostumeSlot: Kostüm, Saç, Silah Slotları]
```

---

**Veri Akışı:** `Server (Costume Data)` -> `root/uiinventory.py` -> `costumewindow.py`.
