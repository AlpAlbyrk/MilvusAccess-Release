# MilvusAccess — Dağıtım

Bu depo yalnızca **kurulum paketlerini** barındırır; kaynak kod içermez.
Sürümler sağdaki **Releases** bölümünde yayımlanır.

## Destek ekibi için hızlı yol

Sunucuda **yönetici PowerShell** açın:

```powershell
# İlk kez indirme (script zip'in içinde de var, ilk seferde buradan alın)
Invoke-WebRequest https://github.com/AlpAlbyrk/MilvusAccess-Release/releases/latest/download/update.ps1 -OutFile update.ps1

# GÜNCELLEME (en son sürüm; mevcut ayarlar, keys\ ve logs\ korunur, DB scripti çalışır)
.\update.ps1 -SqlServer SUNUCU\INSTANCE

# İLK KURULUM (IIS site + havuz + izinler + COM kaydı + DB + ayar)
.\update.ps1 -FirstInstall -SqlServer SUNUCU\INSTANCE -ConnectionString "Server=SUNUCU;Database=MilvusAccess;User Id=...;Password=...;TrustServerCertificate=True;MultipleActiveResultSets=True"
```

Belirli bir sürüm için `-Version 1.2.0`, internetsiz sunucu için indirilmiş zip ile `-ZipPath C:\indirilen\MilvusAccess-1.2.0.zip`.
Tüm parametreler ve ön koşullar: paketin içindeki `DEPLOY.md`.

## Paket içeriği

| Dosya | Açıklama |
|---|---|
| `MilvusAccess-X.Y.Z.zip` | IIS'e kopyalanacak publish çıktısı (+ `install.sql`, `update.ps1`, `DEPLOY.md`) |
| `install.sql` | Veritabanı kurulum/güncelleme scripti (idempotent; ayrıca da eklenir) |
| `update.ps1` | Kurulum/güncelleme scripti (ayrıca da eklenir) |

Sürüm notları her Release'in altında yer alır.
