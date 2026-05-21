# 1v1 VS — Sadece Client + Pack (Sunucu Kaynağı Yok)

Bu liste **sunucu (game/db/quest) değiştirmeden** yapılabilecek 1v1 / PvP fikirleridir.

**Kapsam:**
| Katman | Yol | Ne yapılır |
|--------|-----|------------|
| **Pack** | `D:\Metin2p\Rudymt2 - Kopya\pack` | Python UI, `uiscript`, ses, görsel |
| **Client (küçük)** | `D:\Rudy2\Client Source` | Var olan C++’ı Python’a açmak, kamera, efekt |

**Sunucu gerekmez** = bahis, ELO DB, ayna equip, arena hasarı, ban–pick gibi şeyler **bu dosyada yok** (altta “ileride server ile” diye not var).

**Zaten client’ta olan düello altyapısı:**
- `HEADER_GC_DUEL_START` → `RecvDuelStartPacket` → `SetDuelMode`, `InsertDUELKey`
- Pack: `uitarget.py` → `/pvp` ile `net.SendChatPacket("/pvp %d" % vid)`
- Pack: `player.IsPVPInstance(vid)`, `SetHPTargetBoard` ile rakip HP yüzdesi

---

## En iyi 10 (client + pack, gerçekçi)

| # | İsim | Pack | Client | Özet |
|---|------|:----:|:------:|------|
| 1 | **Düello HUD** | ✓ | küçük | Büyük rakip HP, süre, mesafe |
| 2 | **3-2-1 GO** | ✓ | küçük | `DUEL_START` anında tam ekran sayım |
| 3 | **Savaş özeti** | ✓ | — | Ölünce / bitince: süre, son HP%, hedef adı |
| 4 | **Sinema modu** | ✓ | — | Quest/minimap gizle, sadece düello UI |
| 5 | **Hedef paneli 1v1** | ✓ | — | Düello butonları, mesafe, hızlı whisper |
| 6 | **Minimap ok** | ✓ | — | Hedef VID’ye ok / işaret |
| 7 | **Düşük can alarmı** | ✓ | — | Kendi + rakip %HP’de ekran/ses |
| 8 | **1v1 ping tekeri** | ✓ | — | Hazır emote/chat (gel / dur / iyi oyun) |
| 9 | **Yerel Bo3 skor** | ✓ | — | Manuel veya ölüm algılayınca 2-1 göster |
| 10 | **FPS / odak kamera** | ✓ | ✓ | 1v1’de otomatik FPS (önceki iş, bekletmede) |

---

## A) Sadece Pack (exe derlemeden)

Bunların hepsi `root/`, `uiscript/`, `locale`, ses dosyası ile yapılır. EPack32 ile `root` + `uiscript` yeter.

### A1. Gelişmiş hedef paneli (`uitarget.py` + uiscript)
- Rakip **level, lonca, mesafe** (koordinat farkından yaklaşık).
- Sabit kısayol: **“Tekrar düello”** → whisper şablonu veya `/pvp` tekrar.
- Düello sırasında gereksiz butonları gizle (ticaret, parti daveti).
- `player.IsPVPInstance(vid)` iken paneli kırmızı çerçeve / farklı gauge rengi.

**Dosyalar:** `uitarget.py`, `uiscript/targetboard` (varsa), `localeInfo`.

---

### A2. Sinema / odak modu
- Tuş veya seçenek: minimap, görev penceresi, shop kısayolları gizlensin.
- Sadece can barı + hedef + skill bar kalsın.
- `constInfo.DUEL_FOCUS_MODE` ile aç/kapa.

**Dosyalar:** `game.py`, `interfaceModule.py`, `uisystemoption.py`.

---

### A3. Yerel süre kronometresi
- Hedef PvP iken `app.GetTime()` ile süre say.
- Ekranda `01:42` — sunucu doğrulamaz; **görsel / kişisel istatistik**.

---

### A4. Yerel Bo3 / skor tahtası
- Oyuncu **+1 / +2** veya rakip ölünce (hedef kaybolunca) skor artır.
- Üstte `Sen 2 - 1 Rakip` — turnuva değil, **arkadaş düellosu** için.
- Sıfırlama butonu.

**Not:** Sunucu ölümü saymaz; sadece client algısı. Ciddi lig için yetersiz, eğlence için yeterli.

---

### A5. 1v1 ping / emote tekeri
- 4–6 slot: “Hazır mısın”, “Gel”, “GG”, “Bekle”, “Pot yok söz” (sadece metin).
- `uicharacter` emotion mantığı + `net.SendChatPacket` veya mevcut emotion komutları.

---

### A6. Ölüm / bitiş kartı (basit)
- `SetHPTargetBoard` + hedef kapanınca küçük panel:
  - Süre, son görülen rakip HP%, isim.
- İsteğe bağlı: `app.SaveScreenShot` ile otomatik ekran görüntüsü (client’ta varsa).

**Dosyalar:** yeni `uiduelsummary.py`, `game.py` hook.

---

### A7. Minimap rakip işareti
- `player.GetTargetVID()` + `chr` pozisyon → minimap üzerinde ok.
- Zaten guild war observer sayacı var (`uiminimap.UpdateObserverCount`) — benzer UI deseni.

---

### A8. Ses ve UI “duyuru”
- PvP kabul / düello başlangıcında pack sesi + `big_notice` benzeri yazı.
- Sunucu mesajı gelmese bile **hedef seçilince** “Düello modu” (yerel).

---

### A9. Kural kartı (sadece kozmetik)
- Sunucu kural uygulamaz; maç öncesi **rastgele eğlence kartı** gösterilir:
  - “Bu round: sadece skill, pot yok (sözleşme)”
  - “Cam gövde (roleplay)”
- Oyuncular kendi aralarında uyar — **hile koruması yok**, sadece tema.

---

### A10. Arena işaretçisi (onur sistemi, pack)
- Oyuncu `F9` ile “arena merkezi” kaydeder (mevcut koordinat).
- Minimap’te daire çizer; dışına çıkınca **uyarı metni** (hasar vermez).
- Sunucusuz adil alan için gönüllü kural.

---

## B) Pack + küçük Client (önerilen paket)

Client’ta **yeni sunucu paketi yok**; sadece mevcut düello paketini Python’a bağlamak.

### B1. `OnDuelStart` callback (çok önemli — diğerlerinin temeli)

`RecvDuelStartPacket` sonunda şu an sadece `CloseTargetBoard` çağrılıyor. Eklenir:

```cpp
PyCallClassMemberFunc(m_apoPhaseWnd[PHASE_WINDOW_GAME], "OnDuelStart", Py_BuildValue("(i)", count));
// veya rakip VID listesi ile tuple
```

Pack `game.py`:

```python
def OnDuelStart(self, *args):
    self.interface.OpenDuelHUD()
    self.duelCountdown.Start()
```

**Dosya:** `PythonNetworkStreamPhaseGame.cpp`, `game.py`, yeni `uiduelhud.py`.

---

### B2. `chr.GetDuelMode()` Python binding

C++’ta zaten var: `DUEL_NONE`, `DUEL_CANNOTATTACK`, `DUEL_START`.

Pack her karede veya 0.2 sn’de bir:
- `DUEL_START` → HUD açık
- `DUEL_NONE` → HUD kapalı

**Dosya:** `PythonCharacterModule.cpp` veya `PythonPlayerModule.cpp`.

---

### B3. Düello HUD (asıl “farklı” his)

Tam ekran üst/orta:
- Rakip adı + büyük HP bar (`SetHPTargetBoard` verisini kopyala)
- Süre (B3 ile birleşir)
- Mesafe metre (iki VID pozisyonu — client’ta `chr.GetPixelPosition` varsa)
- İsteğe bağlı: kendi HP (`player.GetStatus(player.HP)`)

**Pack ağırlıklı;** pozisyon için bazen küçük `chr` binding gerekir.

---

### B4. 3-2-1 GO geri sayım

`OnDuelStart` → 3 sn boyunca saldırıyı **görsel** kilitleme yok (server yönetir) ama:
- Dev sayılar + ses
- Bitince “FIGHT” — HUD aktif

Tamamen client gösterimi; sunucu zaten kendi countdown’ını yapıyorsa çift olabilir — test ile ayarlanır.

---

### B5. Düşük can gerilimi
- Kendi HP %25 altı: hafif kırmızı vignette (pack `ui.Bar` full screen alpha).
- Rakip HP %15 (`SetHPTargetBoard`): kısa ses + HUD pulse.

---

### B6. FPS / yakın kamera sadece 1v1
- `constInfo` + `app.SetFirstPersonCamera` (FPS işi devam edince).
- `GetDuelMode() == DUEL_START` veya `IsPVPInstance` iken otomatik aç; bitince eski kamera.

**Client:** mevcut FPS patch. **Pack:** `game.py` + `uisystemoption`.

---

### B7. Rakip TextTail vurgusu
- `RecvDuelStartPacket` zaten `RefreshAllPCTextTail()` çağırıyor.
- İsteğe bağlı client: düello VID’lerinde isim rengi / efekt (mevcut PVP key mantığı `InstanceBaseEffect.cpp`).

Pack tarafı sınırlı; tam renk için **küçük C++** `InstanceBaseEffect` düzenlemesi.

---

### B8. İzleyici modu UI (sunucu `/observer` varsa)
- Pack’te zaten: `player.IsObserverMode()`, `BINARY_BettingGuildWar_SetObserverMode`.
- 1v1 için: iki oyuncunun HP’sini üstte göster (hedef seçmeden VID listesi gerekir → **OnDuelStart VID listesi**).

---

### B9. Ölüm anı “clutch” efekti (sadece görsel)
- Rakip HP 0% veya hedef yok oldu → 0.5 sn slow UI fade + ses.
- Gerçek slow-motion oyun hızı değil; **sinematik his**.

**Client (opsiyonel):** kamera zoom bir frame — zor, pack fade yeterli.

---

### B10. Hasar / vuruş sayacı (yaklaşık)
- `SetHPTargetBoard` farklarından “tahmini hasar alındı”.
- Tam damage log sunucu ister; **eğitim amaçlı yaklaşık** sayaç client’ta yeter.

---

## Önerilen uygulama sırası

1. **B1** `OnDuelStart` + **B2** `GetDuelMode` (bir günde client patch)  
2. **B3** Düello HUD + **B4** countdown  
3. **A2** sinema modu + **A5** ping tekeri  
4. **A4** yerel Bo3 + **A6** özet kartı  
5. **B6** FPS (ayrı branch, isteğe bağlı)

---

## Paket önerisi (senin “3 güzeldi ama server lazım” durumuna göre)

**Ayna maçı (3) iptal** — server şart.

Yerine aynı “adil ve heyecanlı” his için **client+pack paketi:**

| Eski (server) | Yeni (client+pack) |
|---------------|---------------------|
| Ayna equip | Sinema modu + büyük HUD + “adil oyun” kozmetik kural kartı (sözleşme) |
| Bo3 server | Yerel Bo3 skor + özet kartı |
| ELO | Yok (veya sonra server) |
| Arena daralması | Minimap daire işaretçisi (onur, hasar yok) |

---

## Sunucu kaynağı olmadan YAPILAMAZ (referans)

Bunlar **bu projede şimdilik listeden çıkarıldı:**

- Ayna maçı, loadout draft, bahis, ELO DB  
- Cep boyutu instance, arena dışı hasar  
- Pot/skill yasağının **zorunlu** uygulanması  
- Turnuva bracket, escrow, anti-smurf  

İleride server açarsan `FEATURE_IDEAS.md` ve bu dosyanın eski maddeleri birleştirilebilir.

---

## Seçim

Hangisinden başlayalım?

1. **B1+B3** — Düello HUD (en çok fark edilir)  
2. **A4+A6** — Yerel Bo3 + bitiş özeti (sadece pack, exe yok)  
3. **A2+A5** — Sinema + ping (hızlı, sadece pack)

“1” dersen önce `OnDuelStart` + `GetDuelMode` client patch listesini dosya dosya yazarım.

---

---

## Uygulandı: Düello tekrar + ölüm kamerası (MVP)

**Client:** `DuelReplayManager.cpp`, `PythonDuelReplayModule.cpp` → `duelReplay` modülü  
**Pack:** `root/uiduelreplay.py`, `root/game.py`

| Tuş | İşlev |
|-----|--------|
| **1** | Ölen gözü |
| **2** | Öldüren gözü |
| **3** | Dünya kamerası (R/T/E/Q zoom/pitch/döndür) |
| **F10** | Son 30 sn tekrar |
| **ESC** | Tekrardan çık |

Kayıt düello/PvP başında açılır; **JPEG kareleri diske** yazılır (`Belgeler\Metin2\DuelReplay\session_...\`). RAM’de tutulmaz. F10 = video slideshow; 10 dk sonra klasör silinir.

---

*İlişkili: `FEATURE_IDEAS.md` · Güncelleme: 2026-05-18 — sadece client+pack*
