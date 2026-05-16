# 🎓 Metin2 Skills: `refinedialog.py` (Eşya Yükseltme / Demirci)

`refinedialog.py`, oyuncunun bir eşyayı artı basmak (Yükseltmek) istediğinde açılan, gereken malzemeleri ve başarı şansını gösteren onay penceresidir.

---

## 🔍 Neleri Yönetir?

### 1. Dinamik Boyutlandırma
Bu dosyadaki `width` ve `height` değerleri `0` olarak ayarlanmıştır. Bunun nedeni, pencerenin boyutunun o anki yükseltme işlemi için gereken malzeme sayısına göre `root/uirefine.py` tarafından anlık olarak hesaplanmasıdır.

### 2. Bilgi Metinleri
- **`SuccessPercentage`**: Eşyanın yükseltilme başarı şansını (Örn: %50) gösterir.
- **`Cost`**: İşlem için gereken Yang miktarını barındırır.

### 3. Kontrol Butonları
İşlemi onaylar (`OK`) veya iptal eder (`CANCEL`).

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Şans Göstergesini Renklendirme:
Eğer başarı şansı çok düşükse (Örn: %10), bu metnin rengini kırmızı yapmak oyuncu için iyi bir uyarı olabilir. Bu işlem `root/uirefine.py` içindeki `UpdateDialog` fonksiyonunda yapılır.

### ⚠️ Malzeme Slotları:
Gereken malzemelerin ikonları (İstiridye, İnci vb.) bu `.py` dosyasında tanımlı değildir. Bu slotlar, eşyanın `refine_proto`'daki verilerine göre kod tarafında (`root`) dinamik olarak oluşturulur ve pencereye eklenir.

---

## 📉 refinedialog.py Tasarım Hiyerarşisi
```mermaid
graph TD
    A[RefineDialog: Dinamik Boyut] --> B[Board: Ana Panel]
    B --> C[TitleBar: "Eşya Yükseltme"]
    B --> D[InfoArea: Şans ve Ücret]
    B --> E[DynamicSlots: Gereken Malzemeler - Kodla Eklenir]
    B --> F[Accept / Cancel Butonları]
```

---

**Veri Akışı:** `Server (Refine Info)` -> `root/uirefine.py` -> `refinedialog.py` -> Ekran.
