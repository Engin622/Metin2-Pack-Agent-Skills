# 🎓 Metin2 Skills: `safeboxwindow.py` (Depo / Safebox)

`safeboxwindow.py`, oyuncunun köy gardiyanı veya depo sorumlusu üzerinden açtığı, eşyalarını sakladığı güvenli depolama alanının ana çerçevesidir.

---

## 🔍 Neleri Yönetir?

### 1. Ana Kontroller
Bu dosya sadece deponun dış kasasını ve temel butonlarını içerir:
- **`ChangePasswordButton`**: Depo şifresini değiştirmek için kullanılan butondur.
- **`ExitButton`**: Depoyu kapatır.

### 2. Dinamik İçerik (Slotlar)
Pencerenin içinde asıl eşyaların durduğu slotlar (Grid Table), deponun kaç oda (Sayfa) olduğuna bağlı olarak `root/uisafebox.py` tarafından çalışma anında (Runtime) oluşturulur ve pencereye dahil edilir.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Depo Boyutunu Büyütme:
Eğer daha büyük bir depo tasarımı (Örn: 9x15 slot) istiyorsan, `safeboxwindow.py` dosyasındaki `width` ve `height` değerlerini artırmalı ve `root` tarafındaki slot oluşturma döngüsünü güncellemelisin.

### ⚠️ Şifre Güvenliği:
Depo açılmadan önce oyuncudan şifre istenir. Bu şifre doğrulandıktan sonra bu pencere ve içindeki slotlar görünür hale gelir.

---

## 📉 safeboxwindow.py Tasarım Hiyerarşisi
```mermaid
graph TD
    A[SafeboxWindow] --> B[Board: Ana Kasa]
    B --> C[TitleBar: "Depo"]
    B --> D[ControlButtons: Şifre Değiştir, Kapat]
    B --> E[DynamicGrid: Eşya Slotları - Kodla Oluşturulur]
```

---

**Veri Akışı:** `Server (Safebox Items)` -> `root/uisafebox.py` -> `safeboxwindow.py` -> Ekran.
