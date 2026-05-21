# 🎓 Metin2 Skills: `debuginfo.py` (Hata Ayıklama Modu)

`debuginfo.py`, sistemin "Debug" (Hata ayıklama) modunda çalışıp çalışmadığını sorgulamaya yarayan çok basit ama kritik bir yapılandırma dosyasıdır.

---

## 🔍 Neleri Yönetir?

### 1. Global Debug Değişkeni
Sadece `g_isDebugMode` adlı bir global değişken tutar ve bunu `SetDebugMode` ile ayarlayıp `IsDebugMode` ile okuyan fonksiyonlar barındırır.

### 2. Syserr ve Log Çıktıları
Oyun içindeki diğer birçok `.py` dosyası (özellikle `networkmodule` veya `system.py`), hata mesajlarını ekrana veya `syserr.txt` dosyasına yazdırıp yazdırmayacağına buradaki `IsDebugMode()` değerine bakarak karar verir.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Canlı Sunucu (Production):
Oyunculara verdiğin istemcide (Client) bu değer her zaman `0` olmalıdır. Aksi halde oyuncular arka planda dönen Python hatalarını görebilir veya aşırı loglama yüzünden istemcileri (oyun) yavaşlayıp çökebilir.

**Sonuç:** `debuginfo.py`, geliştirici ile oyuncu sürümü arasındaki "Şalter"dir.
