# 🎓 Metin2 Skills: `introloading.py` (Yükleme Ekranı İşlemleri)

`introloading.py`, oyuncu karakterini seçtikten sonra (veya harita değiştirirken) oyuna girerken ortaya çıkan "Yükleniyor" ekranının arkasındaki mekaniği çalıştıran dosyadır. 

---

## 🔍 Neleri Yönetir?

### 1. Modüllerin Yüklenmesi
Sistemin beyni gibi çalışır. `uiRefine`, `uiToolTip`, `uiInventory` gibi oyun için gereken **tüm arayüz pencerelerini (UI)** arka planda bu dosyadayken hafızaya (RAM) yükler. 

### 2. Yükleme Çubuğu (Gauge)
`uiscript/loadingwindow.py` dosyasındaki ilerleme barını (Gauge) adım adım dolduran fonksiyonlar buradadır. Dosyalar RAM'e yüklendikçe bar ilerler.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Yeni Sistem Eklemek:
Eğer oyuna yepyeni bir sistem (Örn: Çevrimdışı Pazar) eklersen ve bunun bir UI modülü varsa, bu modülü `introloading.py` içinde import edip başlatmalısın. Yoksa oyuncu ışınlandığında o sistem sıfırlanır veya çökertir.

### ⚠️ Syserr (Load Window Hataları):
Eğer `.py` arayüz dosyalarından birinde sekme/boşluk hatası varsa, oyuncu yükleme ekranında (bar dolarken) kalır ve oyuna giremez.
