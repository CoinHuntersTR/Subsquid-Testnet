# Subsquid-Testnet Run Network One

![image](https://pbs.twimg.com/profile_banners/1417081246904197121/1694021343/1500x500)

## Sistem gereksinimleri:
### Ubunutu 22.04
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Subsquid  | 4          | 8       | 80  |
  

## Kurulum

### Güncelleme

```
sudo apt update && sudo apt upgrade -y && sudo apt install nodejs && sudo apt install git
```
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

```
curl -sL https://deb.nodesource.com/setup_20.x | sudo -E bash -
```

> Burada yaklaşık 1dk bekliyoruz. İşlem bittiğinde devam edersiniz.

```
sudo apt-get install -y nodejs
```

> Global NodeJS paketlerini saklamak için klasör oluşturma

```
mkdir ~/global-node-packages
```

> NodeJS'i global klasöre kurma

```
npm config set prefix ~/global-node-packages
```
```
echo 'export PATH="${HOME}/global-node-packages/bin:$PATH"' >> ~/.bashrc
```

```
source ~/.bashrc
```

> Subsquid CLI kurulumu

```
npm install --global @subsquid/cli@latest
```

```
sqd --version
```

> @subsquid/cli/2.8.0 linux-x64 node-v20.5.1 ve üstü olmalı.

### Squid'ı başlatalım.

```
sqd init uniform-load-squid -t https://github.com/subsquid-quests/network-test-one-uniform-load-squid
```
```
cd uniform-load-squid
```
```
npm ci
```

> Bu adımları yaptıktan sonra, subsquid görev sayfasına gelelim.

![Ekran görüntüsü 2024-02-19 112524](https://github.com/CoinHuntersTR/Subsquid-Testnet/assets/111747226/04e4b1a9-5be9-4a79-af3f-cd704c3001b3)


> Buradaki Get Key anahtarını bilgisayarımıza indirelim.

> Sonrasında Mobaxterm veya winscp ile terminalimize bağlanıp.

>  `/root/uniform-load-squid/query-gateway/keys/` dosya yolu içerisine indirdiğimiz dosyayı ekliyoruz.

### Peer ID'yi Alıp Gateway Kaydı Yapma

```
sqd get-peer-id
```

> Id adresini aldıktan sonra, [BURADAN](https://app.subsquid.io/profile/gateways/add?testnet) siteye gidiyoruz.

![Ekran görüntüsü 2024-02-19 112904](https://github.com/CoinHuntersTR/Subsquid-Testnet/assets/111747226/4c430441-1234-4254-9b98-cde17e6f72fe)

> `Gateway Name` istediğiniz bir isim verebilirsiniz. peer-id node içinde size verilen ID girip Register diyoruz.

### Token Kilitleme

> Peer ID sonrasında, [BURADAN](https://app.subsquid.io/profile/gateways) siteye gidiyoruz ve biraz önce oluşturduğumuz Gateway 10 adet tQSD kilitliyoruz.

![Ekran görüntüsü 2024-02-19 113209](https://github.com/CoinHuntersTR/Subsquid-Testnet/assets/111747226/010ef2cf-ccfe-479e-95f7-c259675d40e5)

### Squid'ı Başlatma

```
sqd up
```
> Burada Docker hatası alırsanız. Aşağıdaki komutu çalıştırın;

```
nano commands.json
```
> Açılan sayfada aşağıdak komutları bulup değişiklik yapıyoruz. Sonrasında Ctrl x Y enter yapıp `sqd up` komutunu tekrar çalıştırın.

```
         "up": {
         "deps": ["check-key"],
         "description": "Start a PG database",
-        "cmd": ["docker", "compose", "up", "-d"] // sizde bu şekilde ise
+        "cmd": ["docker-compose", "up", "-d"] // buradaki gibi düzenleyin.
       },
       "down": {
         "description": "Drop a PG database",
-        "cmd": ["docker", "compose", "down"] //sizde bu şekilde ise 
+        "cmd": ["docker-compose", "down"] // buradaki gibi düzenleyin.
       },
```

```
sqd build
```
```
sqd run .
```
> Bu adımları yaptıktan sonra aşağıdaki gibi bir çıktı görüyorsanız işlem tamamdır. Bitmesini bekleyin. En son dashboard puanı claim edebilirsiniz.

![Ekran görüntüsü 2024-02-19 113612](https://github.com/CoinHuntersTR/Subsquid-Testnet/assets/111747226/fa0f72fb-5c42-4af8-8cb2-6eda98af0596)

