# Kick Ses Komutları

Kick sohbetine bağlanıp izleyiciler sohbete bir komut yazdığında (örn. `!creeper_patlama`) bilgisayarında seçtiğin MP3/WAV sesini çalan, Windows için sade bir Python programı.

## Özellikler

- Kick sohbet bağlantısını yapıştır, gerçek sohbete bağlan (giriş yapmak gerekmez, sohbet yalnızca okunur)
- Arayüzden komut ekle, düzenle ve sil
- Her komuta bilgisayarından bir MP3 veya WAV dosyası ata
- Ses seviyesi ve komut bekleme süresi ayarı
- Tüm ayarlar kaydedilir, program yeniden açılınca korunur
- Bağlantı koparsa otomatik yeniden bağlanır

## Kurulum

1. [Python 3.10 veya üzerini](https://www.python.org/downloads/) kur. Kurulumda **"Add python.exe to PATH"** kutusunu işaretle.
2. Bu klasörü bilgisayarına indir.
3. `baslat.bat` dosyasına çift tıkla.

İlk açılışta gerekli paketler otomatik kurulur (internet gerekir). Sonraki açılışlar hızlıdır.

## Kullanım

1. Kick kanalının bağlantısını yapıştır (örn. `https://kick.com/kanaladi`) ve **Bağlan**'a bas.
2. **Komut Ekle** ile bir komut adı yaz ve bir ses dosyası seç.
3. İzleyiciler sohbete komutu yazınca ses çalar. **Sesi Dene** ile sesi önceden dinleyebilirsin.
4. Komutu değiştirmek için çift tıkla veya **Düzenle**'yi kullan.

Bağlantı olarak `kick.com/kanaladi`, `https://kick.com/popout/kanaladi/chat` ya da yalnızca `kanaladi` de kabul edilir.

### Komut adı kuralları

Komut adının başına `!` otomatik eklenir; büyük harfler küçültülür, boşluklar `_` olur. Türkçe karakter (`ç ğ ı ö ş ü İ`) kabul edilmez.

| Yazdığın | Komut |
|---|---|
| `Creeper Patlama` | `!creeper_patlama` |
| `HOSGELDIN` | `!hosgeldin` |
| `Şiir` | hata verir (Türkçe karakter) |

### Ayarlar

- **Ses seviyesi:** 0–100 arası, bir sonraki çalan sesten itibaren geçerli olur.
- **Komut bekleme süresi:** Aynı komut art arda yazıldığında, süre dolana kadar tekrar çalınmaz (her komutun beklemesi ayrı sayılır). `0` yazarsan bekleme olmaz.

Ayarlar ve komutlar program klasöründeki `ayarlar.json` dosyasında saklanır.

> Sesler senin bilgisayarında çalar. Yayında duyulmasını istiyorsan OBS'te masaüstü sesini (Audio Output Capture) yayına eklemelisin.

## Sorun giderme

| Sorun | Çözüm |
|---|---|
| "Python bulunamadı" | Python'u kur ve kurulumda PATH kutusunu işaretle. |
| "Kick isteği reddetti (HTTP 403)" | Kick'in bot koruması engelledi. Biraz bekleyip tekrar dene; olmazsa `.venv\Scripts\python -m pip install -U curl_cffi` çalıştır. |
| "Kanal bulunamadı" | Bağlantıdaki kanal adını kontrol et. |
| Ses çıkmıyor | Windows'ta varsayılan ses çıkış cihazını ve dosyanın bozuk olmadığını kontrol et. **Sesi Dene** ile test et. |
| "Failed to build pygame" hatası | Eski `pygame` yerine `pygame-ce` kullanılıyor; güncel dosyaları indirip `.venv` klasörünü sil ve `baslat.bat`'ı yeniden çalıştır. |
| Paketler yeniden kurulsun | `.venv` klasörünü sil ve `baslat.bat`'ı yeniden çalıştır. |
| Beklenmeyen hata | Ayrıntılar `hata.log` dosyasına yazılır. |

## Dosyalar

- `kick_ses.py`: program
- `baslat.bat`: kurulumu yapar ve programı açar
- `requirements.txt`: Python paketleri

## Not

Program, Kick'in herkese açık sohbet bağlantısını (Pusher WebSocket) kullanır; Kick resmi olmayan bu yapıyı değiştirirse güncelleme gerekebilir. Bu proje Kick ile bağlantılı değildir.
