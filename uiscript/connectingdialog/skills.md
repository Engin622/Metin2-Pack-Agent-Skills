# 🎓 Metin2 Skills: `connectingdialog.py` (Sunucuya Bağlanılıyor)

`connectingdialog.py`, kullanıcı giriş bilgilerini yazıp "Giriş" butonuna bastığında ekranda beliren "Sunucuya Bağlanılıyor..." yazısını içeren geçici bilgilendirme penceresidir.

---

## 🔍 Neleri Yönetir?

### 1. Durum Mesajı (`message`)
Bağlantı sürecinin o anki durumunu (`LOGIN_CONNECTING`) gösterir.

### 2. Geri Sayım / Ek Mesaj (`countdown_message`)
Eğer bağlantı sırasında bir bekleme süresi varsa veya ek bilgi verilecekse kullanılan ikinci metin alanıdır.

### 3. Sade Tasarım
Bu pencerede herhangi bir buton bulunmaz. İşlem başarılı olursa pencere kapanır ve karakter seçimine geçilir; başarısız olursa bir hata pop-up'ı açılır.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Görsel Değişimi:
Bu pencere `board` tipindedir. Eğer giriş ekranına özel, çerçevesiz veya daha şeffaf bir görünüm istiyorsan `type: "window"` yaparak arka plan görselini manuel atayabilirsin.

---

## 📉 connectingdialog.py Tasarım Hiyerarşisi
```mermaid
graph TD
    A[QuestionDialog: Bağlantı Paneli] --> B[Board: Standart Çerçeve]
    B --> C[Message: "Bağlanılıyor..."]
    B --> D[CountdownMessage: Bekleme Bilgisi]
```

---

**Veri Akışı:** `root/intrologin.py` -> `connectingdialog.py` -> `networkmodule.py`.
