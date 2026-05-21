# 🎓 Metin2 Skills: `Proto Dosyaları` (item_proto ve mob_proto)

`item_proto` ve `mob_proto`, Metin2'nin gerçek kalbidir! Sunucu (Server) veritabanındaki eşya ve canavar tablolarının, İstemci'ye (Client) **şifrelenmiş, paketlenmiş (binary/LZ) bir kopyasıdır.**

---

## 🔍 Neleri Yönetirler?

### 1. `item_proto` (Eşya Veritabanı)
Oyundaki tüm eşyaların istatistiksel verilerini tutar. Silahların Saldırı Hasarı, Zırhların Defansı, takma seviyeleri, eşyanın kaç paraya NPC'ye satılacağı, eşyanın tipi (Silah mı, Görev eşyası mı, Balık mı?), efsunlanabilir olup olmadığı gibi kritik bilgilerin tümü buradadır.
**Görsel Hata:** `item_proto` bozuksa veya sunucuyla uyuşmuyorsa, örneğin kılıç aslında +200 Atak veriyordur ama sende (Client) +50 yazıyordur (Hasar vururken 200 vurursun ama ekranda 50 görürsün).

### 2. `mob_proto` (Canavar ve NPC Veritabanı)
Tüm Mob (Yaratık), Metin Taşı ve NPC'lerin özelliklerini tutar. Canavarın Seviyesi, Hangi boyutta olduğu, can (HP) miktarı, adı (Örn: "Yabani Köpek"), agresif olup olmadığı (sana kendi kendine saldırıp saldırmayacağı) gibi veriler burada saklanır.

---

## 🛠️ Nasıl Açılır ve Düzenlenir? (Kritik Uyarı)

### ⚠️ Düz Metin Değildir!
Bu dosyaları Notepad++ veya VSCode ile açarsan karşına anlamsız Çince/Karışık semboller (Binary verisi) çıkar. Bu dosyaları **manuel düzenleyemezsin.**

### ✅ Proto Dumper (Zagre / DumpProto)
Bu dosyaları düzenlemek için bir `DumpProto` aracına ihtiyacın var. 
1. `item_proto` dosyasını `DumpProto.exe` üzerine sürükleyip bırakırsın.
2. Araç sana bunu `item_proto_dump.xml` (veya `item_names.txt` + `item_proto.txt`) şeklinde düz metin tablosuna dönüştürür.
3. XML dosyasını düzenler, efsununu veya adını değiştirirsin.
4. XML dosyasını tekrar programla kapatıp (Compile) yeni bir `item_proto` oluşturur ve oyuna atarsın.

### 🔗 Otomasyon İpucu:
Daha önceki seanslarda "Automation" botundan bahsetmiştik. `mob_proto` içindeki veriler, Radar sisteminde canavar isimlerinin ve türlerinin çekildiği yerin ta kendisidir!

## 📉 Proto Senkronizasyonu
```mermaid
graph LR
    A[Sunucu MySQL (Navicat)] -->|Aynı Olmak Zorunda!| B[Client: mob_proto / item_proto]
    B --> C[Oyun İçi Zırh Defansı ve Mob Adı]
```
