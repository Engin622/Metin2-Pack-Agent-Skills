# 🎓 Metin2 Skills: `intrologo.py` (Açılış Logoları ve Video)

`intrologo.py`, oyunun kısayoluna (exe) ilk tıklandığında ekrana gelen "Gameforge", "Ymir" gibi yapımcı şirketlerin logolarını veya `.avi` formatındaki tanıtım videolarını oynatan dosyadır.

---

## 🔍 Neleri Yönetir?

### 1. Video Listesi (`videoList`)
Oynatılacak videoları barındırır. (Örn: `["logo1.avi", "logo2.avi"]`).

### 2. Atla (ESC) Tuşu
Oyuncu klavyeden herhangi bir tuşa bastığında logoların veya videonun hızlıca atlanıp giriş ekranına (Login) geçilmesini sağlar.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ✅ Açılışı Hızlandırmak (Videoları Kapatmak):
Çoğu PvP sunucusu oyuncuyu bekletmemek için logoları kapatır. Bunu yapmak için `videoList` dizisini boş bırakabilir (`videoList = []`) veya C++ tarafından `PHASE_WINDOW_LOGO` fazını doğrudan atlayabilirsin.
