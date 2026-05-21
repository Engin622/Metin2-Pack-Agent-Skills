# 🎓 Metin2 Skills: `uiduelreplay.py` (Düello Tekrarı / İzleme Sistemi)

`uiduelreplay.py`, oyunda oyuncuların yaptıkları vs'leri (düelloları) daha sonradan bir video izler gibi oynatabilmelerini veya duraklatabilmelerini sağlayan medya oynatıcısı tarzındaki arayüzün kodlarıdır.

---

## 🔍 Neleri Yönetir?

### 1. Oynatıcı Kontrolleri
Arayüzde bulunan Oynat (Play), Duraklat (Pause) ve Durdur (Stop) butonlarının işlemlerini yönetir.

### 2. İsteğe Bağlı Özellik (Import Hatası)
Dosyanın en başında `try: import duelReplay` kullanılmıştır. Bu modül (C++ tabanlı) sunucuda veya client'ta kurulu değilse, arayüz sistemi `DUEL_REPLAY_AVAILABLE = False` diyerek kendini kapatır. Çökmeyi önlemek için iyi bir tasarımdır.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ⚠️ Eski veya Çalışmayan Kod:
Metin2'nin orijinal sürümünde bu özellik genelde aktif edilmemiştir veya tam stabil değildir. Özel bir turnuva sistemi veya düello arenası yapmıyorsan, bu dosyanın client içinde pasif durması bir sorun teşkil etmez.
