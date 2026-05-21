# 🎓 Metin2 Skills: `dragon_soul_refine_settings.py` (Simya Geliştirme Ayarları)

`dragon_soul_refine_settings.py`, Dragon Soul (Ejderha Taşı Simyası) sistemindeki taşların Seviye (Grade), Adım (Step) ve Güç (Strength) basarken ne kadar eşya ve yang (para) isteyeceğini belirleyen yapılandırma dosyasıdır.

---

## 🔍 Neleri Yönetir?

### 1. Geliştirme İhtiyaçları
- **`default_grade_need_count`**: Bir üst seviyeye geçmek için gereken taş sayısı (Örn: `[2, 2, 2, 2]`).
- **`default_step_need_count`**: Bir üst adıma geçmek için gereken sayı.

### 2. Geliştirme Ücretleri (Yang)
- **`default_grade_fee`**: Seviye atlarken istenen para miktarları (Örn: `30000, 50000` Yang).
- **`strength_fee`**: Güçlendirme yaparken kullanılan eşyaya göre (Normal, Kutsanmış, Kutsal) istenen ekstra ücret.

### 3. Maksimum Güç Tablosu
`default_strength_max_table` ile bir taşın sahip olduğu seviye ve adıma göre basılabilecek maksimum güç (artı) seviyesini (Örn: +4, +6) limitler.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Ekonomiyi Ayarlama:
Simya sistemi oyun ekonomisinin kara deliğidir (çok fazla para yakar). Buradaki `fee` (ücret) değerlerini artırarak sunucudaki enflasyonu önleyebilir, veya azaltarak oyuncuların daha hızlı simya yapmasını sağlayabilirsin.

### ⚠️ Sunucu-İstemci Senkronu:
Buradaki değerler sadece **görseldir!** Yani oyuncunun penceresinde "50.000 Yang İstiyor" yazar. Eğer sen burayı 10.000 yapıp sunucu tarafındaki (C++ veya DB) `dragon_soul_table.txt` dosyasını 50.000 olarak bırakırsan, oyuncu butona bastığında "Yetersiz Yang" hatası alır. Her zaman iki tarafı aynı yapmalısın.

**Sonuç:** `dragon_soul_refine_settings.py`, Simya atölyesinin "Fiyat Listesi"dir.
