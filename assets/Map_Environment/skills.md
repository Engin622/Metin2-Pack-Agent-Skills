# 🎓 Metin2 Skills: `Harita ve Çevre` (Outdoor, Property, Terrain, Zone, Tree)

Metin2'de haritalar tek bir devasa 3D model değildir. Bunun yerine, bir taban zemin (Terrain), üzerine yerleştirilen binalar/nesneler (Zone) ve ağaçlar (Tree) kullanılarak LEGO gibi birleştirilir. Tüm bu kurallar `Property` ve `Outdoor` klasörleri ile yönetilir.

---

## 🔍 İçerisinde Neler Var?

### 1. `Property` Klasörü (`.prb`, `.prt`, `.prd`)
Bu klasör, oyundaki her cansız nesnenin (evler, köprüler, kayalar, fenerler) kimlik kartlarını barındırır.
- **`.prb` (Property Building)**: Bir nesnenin adını, `.gr2` modelinin yolunu ve gölge düşürüp düşürmeyeceğini belirler.
- Eğer bir haritaya yeni bir ev ekleyeceksen, önce o evin modelini `Zone` klasörüne atmalı, sonra o modeli tanımlayan bir `.prb` dosyasını `Property` klasörüne koymalısın.

### 2. `Zone` ve `Tree` Klasörleri
- **`Zone`**: Evler, kaleler, surlar, heykeller gibi statik nesnelerin 3D `.gr2` modellerini ve `.dds` kaplamalarını barındırır.
- **`Tree`**: Oyundaki tüm ağaçların, çalıların ve bitkilerin modellerini barındırır. Ağaçlar rüzgarda sallanma efektine sahip oldukları için özel yapıdadırlar (`SpeedTree`).

### 3. `Terrain` Klasörü (`.raw`, `.tga`)
Zemin dokularını ve yükseklik haritalarını (dağlar, vadiler, nehir yatakları) yönetir.
- Zemin çim, toprak veya kar görünümlü olabilir; bu dokular burada tutulur ve harita dosyaları tarafından mozaik gibi döşenir.

### 4. `Outdoor` Klasörleri (Örn: `OutdoorA1`, `OutdoorDesert`)
Gerçek oyun haritalarının yapılandırma klasörleridir. İçerisinde haritanın parçalara bölünmüş sektörleri bulunur (`000000.txt`, `area_data.txt` vb.).
- **`msenv`**: Haritanın atmosfer ayarlarını (Gökyüzü rengi, sis rengi ve yoğunluğu, güneşin açısı) belirten metin dosyasıdır. Eğer çöl haritasını karanlık/gece yapmak istersen `.msenv` dosyasını düzenlersin.

---

## 🛠️ Modifikasyon ve Sık Karşılaşılan Hatalar

### ✅ Kendi Haritanı Yapmak:
WorldEditor gibi bir programla harita tasarladığında, program sana `Outdoor` formatında klasörler verir. Bu klasörleri pack'e atmalı ve `root/atlasinfo.txt` dosyasına koordinatlarını girmelisin.

### ⚠️ Simsiyah Evler veya Zemin Hatası:
Haritaya ışınlandığında binalar tamamen siyahsa veya beyazsa, `Property` dosyasında yazan `.dds` yolundaki resim `Zone` klasöründe yoktur. Eğer ağaçlar havada duruyorsa, zeminin yükseklik (`.raw`) haritası ile objelerin Z (yükseklik) koordinatları uyuşmuyordur.

---

## 📉 Harita Yükleme Veri Akışı
```mermaid
graph TD
    A[İstemci: 1. Köye Işınlanıyor (OutdoorA1)] --> B[Zemin Yükseklik ve Dokularını Çiz (Terrain)]
    B --> C[Haritadaki Evleri ve Objeleri Yerleştir (Zone & Property)]
    C --> D[Bitki Örtüsünü Yerleştir (Tree)]
    D --> E[Atmosfer ve Işık Ayarlarını Yükle (msenv)]
    E --> F[Karakteri Haritaya Bırak]
```
