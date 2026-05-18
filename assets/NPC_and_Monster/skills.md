# 🎓 Metin2 Skills: `NPC` ve `Monster` (Yaratıklar ve NPC'ler)

`pack/NPC`, `pack/NPC2`, `pack/Monster` ve `pack/Monster2` klasörleri; oyundaki tüm yapay zeka kontrolündeki varlıkların (Satıcılar, Demirci, Canavarlar, Bosslar, Metin Taşları, Binekler ve Petler) modellerini, kaplamalarını ve animasyonlarını barındırır.

---

## 🔍 İçerisinde Neler Var?

### 1. `.gr2` (Canavar ve NPC Modelleri)
Tıpkı oyuncu karakterleri gibi, NPC ve canavarların da fiziksel iskeleti ve gövdesi Granny 3D (`.gr2`) formatında saklanır.
- **Kullanım Alanı**: Vahşi Köpek'in vücudu, Silah Satıcısı'nın modeli veya bir binek atın yapısı.

### 2. `.msa` (Hareket Animasyonları)
Bir canavarın nasıl saldıracağı, nasıl öleceği veya boşta beklerken (`wait`) nasıl nefes alacağı bu dosyalarda tanımlıdır.
- **`wait.msa`**: Boşta bekleme animasyonu.
- **`run.msa`**: Oyuncuyu kovalarken oynatılan koşma animasyonu.
- **`attack.msa`**: Saldırı animasyonları.
- **`dead.msa`**: Öldüğünde yere yığılma animasyonu.

### 3. `.mot` (Motion Dosyaları - Opsiyonel)
Eski veya bazı özel animasyonların hareket vektörlerini tutan ek veri dosyalarıdır. Genellikle `.msa` ile birlikte çalışırlar.

---

## 🛠️ Modifikasyon ve Sık Karşılaşılan Hatalar

### ✅ Binek veya Pet Eklemek:
Binekler (Örn: Domuz, Kurt, Aslan) ve Petler (Evcil hayvanlar) genellikle `NPC` veya `NPC2` klasörüne eklenir (Monster klasörüne değil). Modeli klasöre attıktan sonra `root/npclist.txt` dosyasına klasör adını ve oyundaki Vnum (Kodu) karşılığını işlemelisin. Aksi takdirde oyunda görünmez.

### ⚠️ Görünmezlik (Invisible Mob) Hatası:
Eğer sunucuda bir yaratık spawn ediyorsan (Örn: `/m 101`) ama ekranda hiçbir şey görünmüyorsa, sadece ismi yazıyorsa ve vurabiliyorsan:
1. `npclist.txt` içinde klasör yolu eksiktir veya yanlıştır.
2. Klasör içindeki `.gr2` dosyasının adı ile klasör adı veya `.msm` dosyası birbiriyle uyuşmuyordur.

---

## 📉 Yaratık & NPC Veri Akışı
```mermaid
graph TD
    A[Sunucu: Vahşi Köpek (Vnum 101) Spawn Et] --> B[İstemci: npclist.txt'ye Bak (101 = stray_dog)]
    B --> C[pack/Monster/stray_dog klasörüne git]
    C --> D[stray_dog.gr2 modelini ve stray_dog.dds kaplamasını yükle]
    D --> E[Sürekli Olarak wait.msa animasyonunu döngüye sok]
```
