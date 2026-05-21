# 🎓 Metin2 Skills: `emotion.py` (Karakter Duygu/Dans Sistemi)

`emotion.py`, oyuncunun oyunda sohbet satırına komut yazarak (Örn: `/dance1`) veya duygu penceresinden (Emotion Window) tıklayarak yaptığı hareketlerin komutlarını ve tanımlarını eşleştiren dosyadır.

---

## 🔍 Neleri Yönetir?

### 1. Komut Eşleştirmesi (`EMOTION_DICT`)
Sistem, belirli bir ID'ye (Örn: `EMOTION_CLAP = 1`) bir sohbet komutu (`/clap`) atar. Oyuncu bu komutu yazdığında C++ tarafına bu ID iletilir ve karakter animasyona başlar.
- **Danslar**: `/dance1`, `/dance2` vb.
- **Duygular**: `/clap` (Alkış), `/angry` (Kızgın), `/kiss` (Öpücük).

### 2. İkon İsimleri (`name`)
Bu hareketlerin arayüzde (Duygu Penceresi) hangi isimle görüneceği, `localeInfo` üzerinden (Örn: `localeInfo.EMOTION_CLAP`) çoklu dile uygun olarak belirlenir.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Yeni Dans Eklemek:
Eğer sunucuya yeni bir dans animasyonu eklersen (Örn: `EMOTION_DANCE_7`), bu listeye `/dance7` komutuyla birlikte eklemelisin. Tabii C++ ve `msm` dosyalarında da bu animasyonun (motion) tanımlı olması şarttır.

### ⚠️ Maske Gerekliği:
Öpücük (`EMOTION_KISS`) gibi bazı eylemler, oyunun C++ kodlarında "Duygu Maskesi" (Emotion Mask) eşyası takılı olmadan yapılamaz olarak hardcoded sınırlandırılmıştır.

**Sonuç:** `emotion.py`, Metin2'nin sosyalleşme aracıdır!
