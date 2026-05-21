# 🎓 Metin2 Skills: `consolemodule.py` (Oyun İçi Geliştirici Konsolu)

`consolemodule.py`, aslında Metin2'nin beta veya test aşamalarında kullanılan, oyun içi geliştirici konsolunun (`Console` sınıfı) altyapısını kuran modüldür.

---

## 🔍 Neleri Yönetir?

### 1. Konsol Mimarisi
Oyunda harita parçalarını (`terrain`, `water`, `sky`), render sıralamalarını (`distance`, `texture`) ve dosya yollarını (Örn: `D:\Ymir Work\`) analiz etmeye yarayan komut altyapısını içerir.

### 2. Ymir Work Bağımlılığı
Dosyanın içindeki `self.curPathName = "D:\\Ymir Work\\"` satırı, oyun dosyalarının neden hala bu dizinden okunduğunun (C++ tarafında hardcoded olan bu yolun Python tarafındaki izdüşümü) bir kanıtıdır.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ⚠️ Kapalı Özellik:
Standart oyuncularda ve modern client'larda bu konsol kapalıdır (veya tuş ataması silinmiştir). Ancak kaynak kodundan (C++) "Developer Mode" aktif edilirse bu Python modülü üzerinden komutlar çalıştırılabilir. Üzerinde oynama yapmak normal oyuncuya bir şey hissettirmez.

**Sonuç:** `consolemodule.py`, Ymir (eski geliştirici) mühendislerinin dünyayı şekillendirirken kullandığı eski bir araç setidir.
