# 🎓 Metin2 Skills: `test_affect.py` (Efekt Test Modülü)

`test_affect.py`, geliştiricilerin oyundaki (Zehir, Yavaşlatma, Kutsama vb.) durum ikonlarını ve efektlerini oyun motoruna yüklemeden doğrudan Python üzerinden test etmek için kullandıkları kısa bir betiktir (script).

---

## 🔍 Neleri Yönetir?

### 1. Hızlı Başlatma (Mocking)
Oyuna giriş ekranlarını (`intrologin`, `introselect`) tamamen atlayarak, sadece ekran boyutlarını ayarlar (`wndMgr.SetScreenSize`) ve sahte bir `TestGame` sınıfı oluşturarak karakterin üzerindeki UI'ları test eder.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ⚠️ Üretimde Gereksiz (Production):
Bu dosyanın normal oyuncuların kullandığı istemcide hiçbir işlevi yoktur. `root` klasörünün içinden silebilirsin, oyunun çalışmasını etkilemez.
