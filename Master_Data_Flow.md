# 🎓 Metin2 Skills: Master Veri Akış Şeması (Client Mimarisi)

Bu şema, bir oyuncu oyuna girdiğinde veya bir eylem yaptığında (Örn: Bir canavara vurmak) istemci içindeki dosyaların birbiriyle nasıl konuştuğunu gösteren en üst seviye teknik haritadır.

---

## 📉 Genel Mimari Şeması

```mermaid
graph TD
    subgraph "1. Giriş ve Mantık (Logic Layer)"
        A[root / system.py] --> B[root / game.py]
        B --> C[root / interfacemodule.py]
    end

    subgraph "2. Görsel Düzen (UI Layout)"
        C --> D[uiscript / *.py]
    end

    subgraph "3. Veri ve Dil (Data & Locale)"
        B --> E[locale_tr / item_proto]
        B --> F[locale_tr / locale_game.txt]
        D --> G[locale_tr / locale_interface.txt]
    end

    subgraph "4. Görsel Varlıklar (Asset Layer)"
        E --> H[pack / item & icon]
        B --> I[pack / PC & Monster & NPC]
        D --> J[pack / ETC]
        B --> K[pack / Effect]
    end

    subgraph "5. Ses ve Atmosfer"
        B --> L[pack / Sound & BGM]
    end

    subgraph "6. Çevre ve Dünya"
        B --> M[pack / Outdoor & Zone & Property]
    end

    F & G & H & I & J & K & L & M --> Z[Metin2 Oyun Motoru / Render]
    Z --> Output((OYUN EKRANI))
```

---

## 🔍 Veri Yolculuğu Örneği: "Bir Kılıcı Envanterde Görmek"

1.  **Server**: İstemciye "Envanterin 1. slotunda Vnum 10 (Kılıç) var" paketini gönderir.
2.  **root (Python)**: Paketi alır, `item_proto` (locale_tr) içinden bu kılıcın adını ve özelliklerini bulur.
3.  **uiscript**: Envanter penceresini (`inventorywindow.py`) çizer.
4.  **locale_tr**: `item_list.txt` dosyasına bakarak Vnum 10'un ikon yolunu (`icon/item/00010.tga`) bulur.
5.  **pack/icon**: Belirtilen yoldaki resmi yükler.
6.  **Oyun Motoru**: Tüm bu verileri birleştirerek envanterdeki o kutucuğa kılıç resmini ve üzerine gelindiğinde özelliklerini (Tooltip) basar.

---

### 🎓 Sonuç
Metin2 istemcisi, **Python (Mantık)** ile **Granny/DirectX (Görsel)** arasında kurulan mükemmel bir köprüdür. Her klasör bu köprünün bir parçasını oluşturur. Bir parçanın eksik olması veya senkronize olmaması tüm sistemin aksamasına (Crash/Hata) neden olur.
