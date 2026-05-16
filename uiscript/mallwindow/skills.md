# 🎓 Metin2 Skills: `mallwindow.py` (Nesne Market Deposu)

`mallwindow.py`, Nesne Market üzerinden satın alınan eşyaların oyun içine teslim edildiği "Nesne Market Deposu" penceresinin tasarımıdır. Standart depodan farklı olarak sadece eşya alımı için kullanılır.

---

## 🔍 Neleri Yönetir?

### 1. Pencere Boyutları (`width` / `height`)
Pencere 176x327 boyutlarındadır. Bu genişlik (176), standart bir envanter sayfasıyla aynıdır çünkü içerideki slot yapısı envantere benzer.

### 2. Başlık ve Kapatma (`TitleBar`)
- **`text`**: `uiScriptLocale.MALL_TITLE` (Nesne Market Deposu) başlığını görüntüler.
- **`style: attach`**: Başlık çubuğunun ana pencereye yapışık olduğunu ve pencereyle birlikte hareket ettiğini belirtir.

### 3. Slot Yapısı (Kod İçinde)
Bu `.py` dosyasında `ItemSlot` bloğu görünmese de, `root/uisafebox.py` dosyası bu pencereye dinamik olarak `ItemSlot` (eşya kareleri) ekler.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Görünüm Değiştirme:
Eğer market deposunu daha geniş yapmak istersen (Örn: 3 sayfa yan yana), `width` değerini `176 * 3` şeklinde artırabilirsin ancak bu durumda `root` tarafındaki slot dizilimini de düzenlemen gerekir.

### ⚠️ Karıştırmayın:
Bu dosya `safeboxwindow.py` (Normal Depo) ile karıştırılmamalıdır. Nesne Market deposunun kendine özel bir işleyişi vardır.

---

## 📉 mallwindow.py Tasarım Hiyerarşisi
```mermaid
graph TD
    A[MallWindow: Nesne Market Deposu] --> B[board: Arka Panel]
    B --> C[TitleBar: Başlık Çubuğu]
    C --> D[TitleName: Metin]
    B --> E[ExitButton: Kapatma Butonu]
    B -.-> F[ItemSlots: Eşya Yuvaları (Kodla Eklenir)]
```

---

**Veri Akışı:** `DB (Market Eşyaları)` -> `uisafebox.py` (Logic) -> `mallwindow.py` (Arayüz) -> Ekran.
