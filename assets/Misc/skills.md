# 🎓 Metin2 Skills: `Tree`, `npc2` & `season` Klasörleri

Bu klasörler, oyun dünyasının bitki örtüsünü, güncellenmiş NPC modellerini ve dönemsel/hikayesel görsel paketlerini barındırır.

---

## 🔍 Neleri Yönetir?

### 1. `Tree/` (Ağaçlar ve Bitki Örtüsü)
Haritalardaki tüm ağaçların, çalıların ve çiçeklerin 3D modellerini içerir. Metin2 motoru ağaçlar için özel bir render tekniği (SpeedTree benzeri) kullanabilir.
- **`.spt` dosyaları**: Ağaçların rüzgarda sallanma ve yaprak dökme gibi fiziksel davranışlarını tanımlar.

### 2. `npc2/` (Güncel NPC Modelleri)
Orijinal `NPC` klasörüne ek olarak, daha yüksek kaliteli veya yeni etkinliklerde gelen NPC'leri (Örn: Simyacı, Etkinlik Yöneticisi) barındırır.

### 3. `season*/` (Mevsimsel ve Tematik Paketler)
Kış teması, bahar teması gibi mevsimlik değişiklikleri veya belirli bölgelerin (Örn: Avrupa sunucularına özel) görsel farklarını barındıran paketlerdir.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Harita Yeşillendirme:
Haritadaki ağaçları değiştirmek istersen `Tree/` klasöründeki modelleri güncelleyebilir veya yeni modeller ekleyip `Property` dosyalarından bu ağaçlara referans verebilirsin.

### ⚠️ Alpha Kanalları:
Ağaç yaprakları ve çalılar için kullanılan `.dds` dosyalarında **Alpha Channel (Şeffaflık)** çok önemlidir. Eğer alpha kanalı düzgün ayarlanmazsa ağaç yaprakları siyah kutucuklar şeklinde görünür.

---

**Veri Akışı:** `Property` -> `pack/Tree` & `pack/npc2` -> `Oyun Motoru`.
