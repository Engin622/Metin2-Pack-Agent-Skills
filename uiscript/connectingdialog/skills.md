# 🎓 Metin2 Skills: `connectingdialog.py` (Bağlantı Bekleme Ekranı)

`connectingdialog.py`, karakteri seçip "Başla" butonuna bastığında veya sunucuya ilk giriş yaparken ekranda beliren "Sunucuya bağlanılıyor..." ve geriye doğru sayan mesaj kutusunun tasarım dosyasıdır.

---

## 🔍 Neleri Yönetir?

### 1. Durum Mesajı (`message`)
"Sunucuya bağlanılıyor..." gibi mevcut durum bilgisini gösteren statik metin alanıdır.

### 2. Geri Sayım Bilgisi (`countdown_message`)
Bağlantının kurulması veya iptal edilmesi için geriye doğru sayan (veya saniye tutan) dinamik metin alanıdır.

### 3. Butonsuz Yapı
Bu ekranda herhangi bir "İptal" veya "Tamam" butonu yoktur. Bu, oyuncunun işlem sürerken bağlantıyı zorla kesmesini önlemek için bilerek yapılmış bir tasarımdır.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Özel Bekleme Görselleri:
Pencere çerçevesinin içine dönen bir kum saati veya yükleme (loading) animasyonu eklemek istersen, `ani_image` nesnesi kullanarak pencereyi hareketlendirebilirsin.

### ⚠️ Yanlış Kullanım:
Bu dialog, sunucu ile client arasındaki "Handshake" (el sıkışma) işlemi bitene kadar ekranda kalır. Bu arayüzün kodu veya pozisyonu bozulursa oyuncu oyuna bağlandığını anlayamayabilir.

---

## 📉 connectingdialog.py Yapısı
```mermaid
graph TD
    A[ConnectingDialog] --> B[Board: Küçük Çerçeve]
    B --> C[Message: "Bağlanılıyor..."]
    B --> D[CountdownMessage: Geri Sayım]
```

**Sonuç:** `connectingdialog.py`, oyun motorunun arka planda dünyayı yüklerken oyuncuyu ekranda tuttuğu "Sabır Noktası"dır.
