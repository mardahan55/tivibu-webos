# Tivibu Web for LG webOS

Tivibu’nun TV arayüzünü LG ana ekranından açan bağımsız bir topluluk uygulaması. Bildiğiniz üzere LG nin resmi mağazasında tivibu'nun resmi uygulaması bulunmamakta, tarayıcıdan açılabilse bile stabil çalışmamakta ve sürekli yeniden giriş istemekte bu yüzden bu uygulamayı geliştirdim. Türk Telekom veya LG ile bağlantısı yoktur. İzlemek için kendi Tivibu hesabınız ve ilgili içeriğe erişim hakkınız gerekir. Giriş işlemi Tivibu’nun kendi ekranında yapılır.

## Uyumluluk

Bu beta, LG OLED55B56LA (B5, webOS 25) üzerinde kullanılan başlatıcıdan hazırlandı. Başlatıcı Tivibu’ya bu modelin profilini bildirir. Başka modellerde giriş, kumanda ve oynatma denenmedi.

## Windows üzerinden kurulum

1. GitHub’daki **Releases** sayfasından `local.tivibuweb.launcher_0.6.0_all.ipk` dosyasını indirin.
2. Bilgisayara Node.js yükleyin. TV ve bilgisayarı aynı yerel ağa bağlayın.
3. LG uygulama mağazasından **Developer Mode** uygulamasını yükleyin. LG geliştirici hesabınızla giriş yapın, **Dev Mode Status** seçeneğini açın ve TV’nin yeniden başlamasını bekleyin.
4. IPK’nın bulunduğu klasörde PowerShell’i açın. Aşağıdaki ilk komutla bir cihaz ekleyin. Cihaz adı `lgtv`, adres TV’nin Developer Mode ekranındaki IP adresi, port `9922`, kullanıcı `prisoner`, bağlantı profili `tv` olmalı.
5. TV’de **Key Server** seçeneğini açın. İkinci komutu çalıştırınca TV’de görünen geçici kodu girin. Üçüncü komutla yükleyin.

```powershell
npx.cmd --yes --package=@webos-tools/cli@3.2.6 ares-setup-device
npx.cmd --yes --package=@webos-tools/cli@3.2.6 ares-novacom --device lgtv --getkey
npx.cmd --yes --package=@webos-tools/cli@3.2.6 ares-install --device lgtv .\local.tivibuweb.launcher_0.6.0_all.ipk
```

TV’nin ana ekranından **Tivibu Web**’i açın. Developer Mode oturumunun süresi dolup mod devre dışı kaldığında LG bu yöntemle yüklenen uygulamaları kaldırır. Oturum süresini TV’deki Developer Mode uygulamasından uzatabilirsiniz. [LG Developer Mode kılavuzu](https://webostv.developer.lge.com/develop/getting-started/developer-mode-app)

## Giriş ve kumanda

- **İzin ver ve hatırla** seçildiğinde başlatıcı, LG’nin TV’ye verdiği cihaz kimliğini Tivibu’nun TV arayüzüne iletir ve otomatik açılış tercihini TV’de saklar. **Paylaşmadan aç** ile kimliği göndermeden tek seferlik açabilirsiniz.
- **Canlı TV** sırasında ↑ veya ↓ ile kanal listesini açın, **OK** ile kanal seçin. Listeyi kapatmak için **Geri** tuşuna bir kez basın.
- **Geçmiş yayınlar** için Tivibu’da **TV Rehberi**’ni açın, tarih seçin ve izlemek istediğiniz yayını seçin.
