# 🎓 Metin2 Skills: `grpblk.txt`, `makepackscript...` & `rootlibcythonizer.py` (Yardımcı/Yapı Dosyaları)

Bu dosyalar oyunun çalışma zamanında (oynanırken) kullanılan dosyalar değildir. Client'ın paketlenmesi veya derlenmesi sırasında kullanılan geliştirici (Developer) dosyalarıdır.

---

## 🔍 Dosyaların Amaçları

### 1. `grpblk.txt`
Grup Blokları. Eski EterPack sistemi tarafından kullanılan, bazı görsel blok verilerinin listelendiği gereksiz/artık (legacy) bir metin dosyasıdır.

### 2. `makepackscript_onlyrootnopython.txt`
`.epk` ve `.eix` dosyalarını paketlerken (packing), packer programına (örn: EterNexus veya MakePack) sadece `root` klasöründeki hangi dosyaların paketleneceğini söyleyen bir liste (script) dosyasıdır.

### 3. `rootlibcythonizer.py`
Python `.py` dosyalarını dışarıdan okunamaz (şifrelenmiş) `.pyc` veya C kütüphanelerine (Cython) dönüştürmek, yani kodları korumak (obfuscation) için kullanılan bir derleyici betiğidir. Hilecilerin `root` dosyalarını çalmasını engellemek için kullanılır.

---

**Sonuç:** Bu dosyaları oyuncuya giden "Pack" içine koymana gerek yoktur. Sadece senin bilgisayarında derleme yaparken işe yararlar.
