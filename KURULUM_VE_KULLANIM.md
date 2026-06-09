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
git clone <REPO_URL>
cd Basis_odak_helper
```
> `<REPO_URL>` paylaşılan GitHub adresidir (depo sahibinden alınır). Git yoksa GitHub'dan
> "Download ZIP" ile indirip açabilirsin.

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
- **Claude Code olmadan:** Dosyaları elle de okuyabilirsin (özellikle `04_Soru_Testi/`), ama
  interaktif deneyim `/start` iledir.
