# 🎓 Metin2 Skills: `exception.py` (Hata Mesajı Yönetimi)

`exception.py`, Python tarafında bir hata (Crash/Exception) oluştuğunda, bu hatanın hangi dosyada ve kaçıncı satırda olduğunu yakalayıp `syserr.txt` dosyasına yazdırılabilir formata çeviren ufak bir hata ayıklama dosyasıdır.

---

## 🔍 Neleri Yönetir?

### 1. Hata İzleme (Traceback)
`sys.exc_info()` ve `traceback` modüllerini kullanarak hatanın nereden geldiğini okur. 
Örn: `uiInventory.py (line: 145) ValueError - Item not found` şeklinde standart bir metin çıktısı üretir.

---

## 🛠️ Modifikasyon ve Kritik Uyarılar

### ⚠️ Dokunulmaması Gerekenler:
Bu dosya Python'un temel standartlarına uygun yazılmıştır. Üzerinde oynama yapmak, gerçek hata mesajlarını (syserr) okunmaz hale getirebilir ve sorunu çözmeni engeller.
