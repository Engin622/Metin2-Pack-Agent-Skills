# 🎓 Metin2 Skills: `atlasinfo.txt` (Harita Koordinat Sistemi)

`atlasinfo.txt`, oyun motorunun haritaların boyutlarını ve dünya içindeki `X/Y` koordinatlarını tanımladığı sistem (config) dosyasıdır. Python dosyası değil, doğrudan C++ tarafının da okuduğu kritik bir haritadır.

---

## 🔍 Neleri Yönetir?

### 1. Sütun Mantığı
Dosyadaki her satır 5 parçadan (sütun) oluşur:
1.  **Harita Adı** (Örn: `metin2_map_a1`)
2.  **Base X Koordinatı** (Örn: `409600`)
3.  **Base Y Koordinatı** (Örn: `896000`)
4.  **X Boyutu** (Block size - Harita Eni, Örn: `4`)
5.  **Y Boyutu** (Block size - Harita Boyu, Örn: `5`)

### 2. Dünya Konumlandırması (Base X/Y)
Oyuncu `/warp 4096 8960` yazdığında aslında 1. Köy (Yongan) haritasının Base (Temel) koordinatlarına ışınlanır. Buradaki X ve Y değerlerine oyun motoru arka planda iki tane `00` ekler.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Yeni Harita Ekleme:
Oyuna yeni bir map (Örn: `metin2_map_t1`) eklediğinde bu dosyaya o haritanın Base X, Base Y ve block boyutlarını girmek **zorundasın**. Aksi halde `/warp` atamazsın ve haritanın minimap'i siyah çıkar.

### ⚠️ Koordinat Çakışması:
İki farklı haritaya aynı (veya birbirinin üzerine binecek kadar yakın) Base X ve Base Y değerleri atarsan, haritaların zemin dokuları birbirine girer ve karakterin uzay boşluğuna düşer!

---

**Sonuç:** `atlasinfo.txt`, Metin2'nin "Dünya Küresi"dir. Tüm kıtaların nerede durduğunu tanımlar.
