# Subsquid-Testnet Run Netwoek One

![image](https://pbs.twimg.com/profile_banners/1417081246904197121/1694021343/1500x500)

## Sistem gereksinimleri:
### Ubunutu 22.04
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Mangata  | 4          | 8       | 80  |
  

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
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
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
npm install --global @subsquid/cli@latest
```
