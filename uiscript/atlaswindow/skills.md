# 🎓 Metin2 Skills: `atlaswindow.py` (Büyük Harita Tasarımı)

`atlaswindow.py`, oyuncu "M" tuşuna bastığında açılan büyük dünya haritasının (Atlas) dış çerçevesini, boyutlarını ve başlığını tanımlayan tasarım dosyasıdır.

---

## 🔍 Neleri Yönetir?

### 1. Pencere Yapısı (`window`)
Haritanın ekranın neresinde açılacağını ve temel boyutlarını belirler. Genellikle ekranın sağ üst kısmına yakın bir konumda başlar.

### 2. Başlık Çubuğu (`board_with_titlebar`)
Pencerenin üstündeki "Dünya Haritası" yazısını ve kapatma butonunu içeren standart Metin2 panel yapısını kullanır.
- **`title`**: `uiScriptLocale.ZONE_MAP` değişkeninden gelen "Dünya Haritası" metnini görüntüler.

### 3. Dinamik İçerik
Bu dosya sadece "kabuk" (frame) görevi görür. Haritanın asıl görseli (`atlas.sub` veya map klasöründeki resimler), `root/uiminimap.py` içindeki mantık tarafından bu pencerenin üzerine dinamik olarak çizilir.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Boyut Değiştirme:
Eğer haritanın daha büyük görünmesini istiyorsan, `width` ve `height` değerlerini artırmalısın. Ancak bunu yaptığında `root` tarafındaki harita çizim koordinatlarını da güncellemen gerekebilir.

### ✅ Konum Ayarı:
`x` koordinatındaki `SCREEN_WIDTH - 136 - 256 - 10` gibi formüller, haritanın farklı ekran çözünürlüklerinde her zaman orantılı bir yerde kalmasını sağlar.

---

## 📉 atlaswindow.py Tasarım Hiyerarşisi
```mermaid
graph TD
    A[AtlasWindow: Ana Pencere] --> B[board: Başlıklı Panel]
    B --> C[TitleBar: Harita Başlığı]
    B --> D[Dinamik Katman: Harita Görseli (Kodla Eklenir)]
```

---

**Veri Akışı:** `atlasinfo.txt` (Harita Bilgisi) -> `uiminimap.py` (Logic) -> `atlaswindow.py` (Görsel Çerçeve) -> Ekran.
