# Kurulum ve Kullanım — Sıfırdan `/start`'a

Bu rehber, **Claude Code'u hiç kullanmamış** bir Basis arkadaşını da hedefler. Özet üç adım:
**kur → repoyu klonla → `claude` çalıştır → `/start` yaz.**

> Komutlar 26 Haziran 2026'da resmi dokümana karşı doğrulandı: <https://code.claude.com/docs>

---

## 0. Claude Code nedir? (1 paragraf)

Claude Code, terminalde (veya VS Code / JetBrains / masaüstü uygulaması içinde) çalışan, bir
klasördeki dosyaları okuyup seninle **sohbet ederek** iş yapan Anthropic yapay zekâ aracıdır.
Bu depo onun için tasarlandı: sen `/start` yazıyorsun, o sana soruyor ve seni taahhüt
dökümanına kadar götürüyor.

> **⚠️ Hesap gereksinimi:** Claude Code; **Pro, Max, Team, Enterprise veya Console (API)**
> hesabı ister. **Ücretsiz claude.ai planı Claude Code'a erişim vermez.** (Alternatif: Amazon
> Bedrock / Google Vertex / Microsoft Foundry üzerinden API.)
> Sistem: Windows 10 1809+/11, macOS 13+, veya Linux; 4 GB+ RAM; internet.

---

## 1. Claude Code kurulumu

Aşağıdan **birini** seç. (Kurumsal makinede yetki sorunu olursa BT'den destek iste.)

### Windows
**WinGet (en kolay):**
```powershell
winget install Anthropic.ClaudeCode
```
**veya PowerShell ile yerel kurulum:**
```powershell
irm https://claude.ai/install.ps1 | iex
```
**veya npm ile** (Node.js 18+ kuruluysa):
```powershell
npm install -g @anthropic-ai/claude-code
```
> İpucu: Git for Windows kuruluysa Claude Code Bash aracını da kullanabilir (opsiyonel, önerilir):
> <https://git-scm.com/downloads/win>

### macOS / Linux / WSL
```bash
curl -fsSL https://claude.ai/install.sh | bash
```
(macOS'ta alternatif: `brew install --cask claude-code`)

### Kurulumu doğrula
```bash
claude --version
```
Sorun olursa: `claude doctor` çalıştır veya <https://code.claude.com/docs/en/troubleshoot-install>.

---

## 2. Repoyu klonla
```bash
git clone https://github.com/batoner/basis-focus-helper.git
cd basis-focus-helper
```
> Genel (public) bir repodur. Git kurulu değilse GitHub sayfasından **"Code → Download ZIP"**
> ile de indirip açabilirsin: <https://github.com/batoner/basis-focus-helper>

---

## 3. Çalıştır ve başla

Repo klasörünün **içindeyken**:
```bash
claude
```
İlk açılışta tarayıcıdan hesabınla giriş yaparsın (tek seferlik). Sonra şunu yaz:
```
/start
```
Hepsi bu. Gerisi sohbet: Claude Code seni karşılar ve interaktif teste başlar.

> Not: Komutlar repodaki `.claude/commands/` klasöründen gelir; bu yüzden Claude Code'u
> **repo klasörünün içinde** açman gerekir.

---

## 4. Komutlar

| Komut | Ne yapar | Çıktı |
|---|---|---|
| `/start` | Baştan sona tam yolculuk (önerilen) | yönlendirme |
| `/test` | Sadece interaktif öz-değerlendirme | `Benim_Ciktilarim/Test_Sonucu.md` |
| `/harita` | Sonuçtan güç/zayıf/ilgi haritası + odak önerisi | ekranda + dosyaya |
| `/proje` | Profiline uygun, dinamik proje önerisi | ekranda |
| `/taahhut` | Tek sayfalık taahhüt taslağını birlikte doldur | `Benim_Ciktilarim/Taahhut_Taslagi.md` |

Sadece `/start` ile gidebilir, içinden bu adımları tek tek de seçebilirsin. Komutları
`/help` ile de görebilirsin.

---

## 5. Çıktın nerede?

Tüm kişisel çıktıların `Benim_Ciktilarim/` klasörüne yazılır ve `.gitignore` sayesinde
GitHub'a **gönderilmez** — cevapların ve taahhüt taslağın yalnızca senin makinende kalır.
İlk yazma sırasında Claude Code izin isteyebilir; onaylaman yeterli.

---

## 6. Sık karşılaşılanlar

- **`claude` komutu bulunamadı:** Terminali yeniden aç; kurulum yöntemine göre PATH güncellenmiş
  olmalı. `claude doctor` ile kontrol et.
- **Giriş/erişim hatası:** Hesabın Pro/Max/Team/Enterprise/Console mı? Ücretsiz plan çalışmaz.
- **`/start` görünmüyor:** Claude Code'u repo klasörünün **içinde** açtığından emin ol.
- **Test cevaplarım kaybolur mu:** Hayır; `Benim_Ciktilarim/` altındaki dosyalar makinende kalıcıdır.
- **Claude Code olmadan:** Bu deponun içeriği düz markdown'dır; Claude Code şart değil. Başka bir
  AI ajanıyla (Gemini CLI, Google Antigravity…) da kullanabilirsin — aşağıya bak.

---

## 7. Claude Code yoksa: Gemini CLI · Google Antigravity · başka bir AI ajanı

Bu repoyu çalıştıran "beyin", `.claude/commands/` içindeki **düz-dil talimatlar** + markdown
içeriktir. Claude Code bunları `/start` ile otomatik çalıştırır; ama dosyaları okuyabilen
**herhangi bir AI ajanı** aynı akışı izleyebilir — ajan kendine uyarlar. Tek yapman gereken,
ajana `start.md`'deki akışı "izle" demek.

### Verilecek talimat (her araçta aynı — kopyala-yapıştır)
> *Bu repo bir SAP Basis retro yardımcısı. `.claude/commands/start.md` dosyasını oku ve oradaki
> akışı izleyerek beni adım adım yönlendir: brief → test → harita → proje → taahhüt. İçeriği ilgili
> klasörlerden (`00_Baglam`, `01_Sunum_Ozetleri`, `04_Soru_Testi`, `05_Proje_Katalogu`,
> `06_Taahhut_Sablonu`) oku; kişisel çıktılarımı `Benim_Ciktilarim/` altına yaz. Türkçe ve sade ol;
> uydurma kaynak kullanma.*
>
> (Yalnız bir adım istiyorsan `start.md` yerine `test.md` / `harita.md` / `proje.md` / `taahhut.md` de.)

### Gemini CLI (ücretsiz seçenek)
1. Kur: `npm install -g @google/gemini-cli` (veya kurulumsuz: `npx @google/gemini-cli`).
2. Repo klasöründe çalıştır: `gemini` → kişisel **Google hesabıyla giriş** (ücretsiz katman;
   API anahtarı gerekmez). *(Claude Code'un aksine ücretsiz kullanılabilir.)*
3. Yukarıdaki talimatı yapıştır. Gemini `start.md`'yi ve içerik dosyalarını okuyup akışı yürütür.

### Google Antigravity (veya başka agentic IDE/araç)
- Repo klasörünü araçta aç, ajana yukarıdaki **aynı talimatı** ver. Ajan `start.md`'yi ve
  içeriği okuyup seni yönlendirir, çıktıları `Benim_Ciktilarim/`'a yazar.

> Özet: `/start`'ın yaptığı her şey `.claude/commands/start.md`'de düz dille yazılı. Hangi aracı
> kullanırsan kullan, "şu dosyadaki akışı izle" demen yeterli; gerisini araç kendine uyarlar.
