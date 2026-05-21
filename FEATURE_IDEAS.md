# Rudy2 / Metin2 — Özellik Fikirleri Kataloğu

Bu dosya, sunucuna veya client kaynağına eklenebilecek **farklı ve dikkat çekici** özellik fikirlerini toplar. FPS kamera şimdilik bekletmede; aşağıdakilerden birini seçip sırayla yapabilirsin.

**Teknik bağlam:**
- Client C++: `D:\Rudy2\Client Source`
- Pack (Python/UI): `D:\Metin2p\Rudymt2 - Kopya\pack`
- Dokümantasyon: `Metin2Skills` (bu repo)

> **1v1 VS — sadece client + pack** → **[FEATURE_IDEAS_1V1_VS.md](FEATURE_IDEAS_1V1_VS.md)**  
> (Düello HUD, 3-2-1 GO, sinema modu, yerel Bo3, ping tekeri; sunucu kaynağı gerekmez. Ayna maçı / ELO / bahis listede yok.)

---

## Öncelik önerisi (kolay → zor)

| Öncelik | Özellik | Zorluk | Etki |
|--------|---------|--------|------|
| 1 | Hızlı loot / toplu alma | Kolay | Günlük oynanış |
| 2 | Mini harita işaretçileri (party, boss) | Orta | QoL |
| 3 | Silah/kostüm önizleme paneli | Orta | Ticaret / shop |
| 4 | Ölüm özeti + hasar logu | Orta | PvP / dungeon |
| 5 | Gelişmiş hedef paneli | Orta | Herkes |
| 6 | FPS kamera (devam) | Zor | İmmersiyon |
| 7 | Web envanter / uzaktan depo | Zor | Modern sunucu |

---

## 1. Oynanış ve QoL (Quality of Life)

### 1.1 Akıllı loot filtresi
- Yere düşen eşyaları renkle ayır: yeşil+ otomatik topla, mavi altı sor.
- `item_proto` tipine göre: sadece taş, sadece ekipman, yang.
- **Nerede:** Client Python (`game.py`, loot paketi) + isteğe bağlı server doğrulama.

### 1.2 Toplu eşya işlemleri
- Envanterde: tüm +0 silahları depoya, tüm iksiri birleştir.
- Sağ tık menü: "Benzerlerini seç", "Satılabilirleri işaretle".

### 1.3 Hızlı kanal / sunucu hatırlatıcı
- Son oynanan karakter + kanal listesi giriş ekranında.
- Favori sunucuya tek tık.

### 1.4 Görev yol tarifi (quest GPS)
- Aktif görev için minimap üzerinde ok / mesafe.
- `atlasinfo` + quest koordinatlarından hesaplanır.

### 1.5 Otomatik pot / buff sırası
- Can %30 altı → kırmızı pot, %80 üstü → buff sırası.
- PvP haritasında kapalı (dengeli).

---

## 2. Savaş ve PvP

### 2.1 Hasar / iyileşme sayacı (combat log)
- Sağ altta son 5 saniye: verilen / alınan hasar, kritik, zehir.
- PvP turnuvasında şeffaflık.

### 2.2 Ölüm ekranı özeti
- "Kim öldürdü", skill, toplam hasar, süre.
- İntikam / aynı bölgeye dön butonu (sunucu kuralına bağlı).

### 2.3 Combo sayacı
- Art arda isabet → ekranda combo rakamı + hafif ses/efekt.
- Sadece görsel; bonus vermek dengesiz olabilir.

### 2.4 Hedef öncelik modu
- Tab ile: en yakın düşman / en düşük can / son saldıran.
- Boss’ta otomatik hedef kilidi.

### 2.5 Duel / 1v1 alanı
- Lonca dışı adil arena: eşit buff, izleyici modu.
- Client: arena UI; Server: ayrı map instance.

---

## 3. Görsel ve client

### 3.1 FPS / omuz kamerası (mevcut — bekletmede)
- Göz hizası, sınırlı fare bakışı, at bindiğinde yükseklik.
- **Durum:** Kısmen kodlandı; ince ayar gerekli.

### 3.2 Hava ve gün döngüsü seçici
- Oyuncu başına: sabah / gece / sis (sadece client `msenv`).
- Sunucu genelinde değil, kişisel atmosfer.

### 3.3 Kostüm set önizleme
- NPC veya UI: tüm vücut + saç + silah tek ekranda döner.
- `PC` / `item` pack yolları + Vnum.

### 3.4 Efsun / upgrade simülasyonu
- "+9 yaparsam ne olur" — sadece görsel, gerçek item yok.
- Oyuncu kaybettirmeden deneme hissi.

### 3.5 Özel kill efekti / bayrak
- İlk kan, boss son vuruş, lonca savaşı zaferi → ekran efekti.
- `Effect` pack + kısa Python tetikleyici.

---

## 4. Sosyal ve lonca

### 4.1 Gelişmiş lonca paneli
- Online üyeler, son giriş, bağış sıralaması.
- Lonca duyurusu (guild master yazar, girişte popup).

### 4.2 Hızlı davet / reddet geçmişi
- Son 10 whisper / party daveti listesi.
- Spam engelleme.

### 4.3 Mentor sistemi
- Yeni oyuncu + rehber: bonus yang/EXP (düşük), rehber rozeti.
- Server quest + client rozet ikonu.

### 4.4 Ortak hedef panosu
- Lonca: "Bu hafta 10k metin taşı" — ilerleme çubuğu.
- Server-side sayaç, client `guild` UI.

---

## 5. Ekonomi ve ticaret

### 5.1 Pazar fiyat geçmişi
- Son satılan item ortalama fiyatı (sunucu DB log).
- Alırken "pahalı / ucuz" uyarısı.

### 5.2 Güvenli takas onay adımları
- Takas: her item eklemede onay kutusu.
- Yanlışlıkla +9 kılıç vermeyi azaltır.

### 5.3 Offline pazar arama (web veya client)
- "Şu item hangi dükkanlarda var" — sunucu cache.
- Büyük sunucularda fark yaratır.

### 5.4 Yang / won cüzdan özeti
- Günlük harcama grafiği (basit liste bile yeter).
- Client log veya server `log` tablosu.

---

## 6. Dungeon ve etkinlik

### 6.1 Zindan süre + skor tablosu
- Temiz süre, ölüm sayısı, verilen hasar.
- Haftalık reset leaderboard.

### 6.2 Boss mekanik uyarıları
- "AOE geliyor", "kaç" — ekran kenarı ikon + ses.
- Quest flag veya boss HP fazına bağlı.

### 6.3 Otomatik eşleşme (matchmaking)
- 4 kişilik dungeon kuyruğu.
- Server queue; client bekleme penceresi.

### 6.4 Sezonluk battle pass (hafif)
- Günlük görev: X canavar, Y metin.
- Ödül: kostüm, başlık, consumable — server tablosu.

---

## 7. Teknik / altyapı (sunucu sahibi için)

### 7.1 Client–server versiyon kontrolü
- Yanlış pack ile girişte net uyarı: "Pack 1.2 gerekli".

### 7.2 Crash raporu (opsiyonel)
- `syserr` özetini tek tıkla panoya kopyala (GDPR’ye dikkat).

### 7.3 Modüler patch sistemi
- Her özellik ayrı `metin2_patch_ozellik_adi` — Index üstte.
- Geri alması kolay.

### 7.4 Özellik bayrakları (`constinfo` / config)
- `ENABLE_COMBAT_LOG = 1` gibi tek yerden aç/kapa.
- Bakım kolaylığı.

---

## 8. "Farklı" — dikkat çeken fikirler

### 8.1 Şehir içi mini oyunlar
- Zar, balık tutma skor tablosu, haftalık birinciye unvan.
- Mevcut balık sistemini genişlet.

### 8.2 Dönüşüm koleksiyonu
- "İlk kez öldürdüğün canavar" kartı — koleksiyon defteri UI.
- Achivement hissi, düşük ödül.

### 8.3 Karakter fotoğraf modu
- UI gizle, poz seç, F12 ekran görüntüsü + basit filtre.
- Reklam / Discord için oyuncu üretir.

### 8.4 Sesli emote paketi
- Kısa `.wav` — güldü, alkış (mesafe sınırlı).
- `Sound` pack + mesafe kontrolü.

### 8.5 Bölgesel boss dünyası
- Haritada rastgele spawn; minimap uyarısı.
- Tüm sunucu birlikte — sosyal etkinlik.

### 8.6 Silah görünümü kilidi
- Görünüm Vnum ≠ gerçek stat Vnum (transmog).
- Çok istenen özellik; server `item` + client render.

---

## 9. FPS kamera — devam notları (bekletmede)

Şu an kodda olanlar (referans):
- `SetFirstPersonCamera` / `SetEyeCamera`
- Fare pitch/yaw, vücut dönüşü, at yüksekliği

Sonraki oturumda yapılacaklar:
- [ ] Öne bakış açısı doğrulama (gerekirse +180° offset)
- [ ] Saldırı animasyonunda stabil yaw
- [ ] At / binek kamera offset testi
- [ ] Pack: `uiscript` FPS butonu (`Rudymt2 - Kopya\pack`)

---

## 10. Nasıl seçim yapılır?

1. **Oyuncu kitlene** — PvP mi, farm mı, sosyal mi?
2. **Tek özellik seç** — bitir, test et, duyur.
3. **Patch olarak yayınla** — `metin2_patch_xxx` + kısa patch notu Discord’da.
4. Bu dosyaya işaretle:

```markdown
- [x] Tamamlandı: ...
- [ ] Devam ediyor: ...
- [ ] İptal: ...
```

---

## Hızlı başlangıç önerisi (ilk 3 iş)

1. **Combat log (2.1)** — Client ağırlıklı, oyuncu hemen hisseder.  
2. **Loot filtresi (1.1)** — Farm sunucularında çok sevilir.  
3. **Kostüm önizleme (3.3)** — Görsel etki yüksek, orta zorluk.

Hangisini yapmak istediğini yaz; o özellik için adım adım dosya listesi ve uygulama planı çıkarılabilir.

---

*Oluşturulma: 2026-05-18 — Rudy2 / Metin2Skills*
