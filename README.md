#Allora

```
apt update && sudo apt upgrade -y

apt install git -y

apt remove ansible -y

apt-get install -y software-properties-common

apt-add-repository --yes --update ppa:ansible/ansible

apt install ansible

ansible --version
```
```
cd $HOME && \
ver="1.21.3" && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \
source $HOME/.bash_profile && \
go version
```

```
git clone https://github.com/nodemasterpro/deploy-node-allora.git

cd deploy-node-allora

```

اینجا اسم نود رو انتخاب کنید تو کامند زیر جایگذاری کنید
```
ansible-playbook install_validator_node_allora.yml -e moniker="your_moniker_name"

```


```

journalctl -u allora-node -f -o cat

```

کنترل سی بزنید استوپ شه

==================== این کامند ها در صورت نیاز است 

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 
اگر لاگ سالم نمینداخت هر کاری کردید یک بار نود رو ری استارت کنید

```
systemctl restart allora-node
```
اگر بازم هر کاری کردید لاگ سالم نمینداخت 
یکبار بزنید
```
cd
systemctl stop allora-node
rm -r deploy-node-allora
```

دوباره کامند هارو از اول بزنید . فقط اسم Moniker یا نودتونم عوض کنید


!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! ==================== این کامند ها در صورت نیاز است 



اگر میخواید از ولت خودتون استفاده کنید

```
allorad keys add wallet --recover
```

گر میخواید ولت جدید بسازید

```
allorad keys add wallet
```

فاست بگیرید

https://faucet.testnet.allora.network/


```
allorad status | jq .sync_info
```

صبر کنید نود سینک شه و False بشه
```
allorad query bank balances <your_wallet_address>
```
موجودی ولت رو چک کنید

```
cd
cd deploy-node-allora

ansible-playbook register_validator_node_allora.yml
```

مشخصات رو وارد کنید


```
allorad keys show wallet -a --bech val --keyring-backend test
```

ولیدیتور ادرس رو بگیرید
```
allorad query staking validator <validator_address>
```

```
allorad tx staking delegate $(allorad keys show wallet --bech val -a --keyring-backend test) 500000000uallo --from wallet --gas=auto --gas-adjustment=1.4 --keyring-backend test -y
```

نود وورکر رو هم راه اندازی کنید طبق ویدیو
Worker
```
cd
wget https://raw.githubusercontent.com/dxzenith/allora-worker-node/main/allora.sh && chmod +x allora.sh && ./allora.sh
```




https://app.allora.network/points/overview ولتتون رو به سایت هم وصل کنید

===================== این کامند ها در صورت نیاز است 
** کامند ری استارت نود ولیدیتوری در صورت نیاز
```
systemctl restart allora-node
```
==================== این کامند ها در صورت نیاز است 
** کامند چک کردن سلامت نود Woker


```
curl --location 'http://localhost:6000/api/v1/functions/execute' \
--header 'Content-Type: application/json' \
--data '{
    "function_id": "bafybeigpiwl3o73zvvl6dxdqu7zqcub5mhg65jiky2xqb4rdhfmikswzqm",
    "method": "allora-inference-function.wasm",
    "parameters": null,
    "topic": "1",
    "config": {
        "env_vars": [
            {
                "name": "BLS_REQUEST_PATH",
                "value": "/api"
            },
            {
                "name": "ALLORA_ARG_PARAMS",
                "value": "ETH"
            }
        ],
        "number_of_nodes": -1,
        "timeout": 2
    }
}'

```

کامند ری استارت کردن نور وورکر 
```
cd allora-chain
cd basic-coin-prediction-node
docker compose up -d
```

--------------------------------------------------------------------------------------------------

#Nubit

```
cd
curl -sL1 https://nubit.sh | bash
```

تا کلمات خصوصی رو داد حواستون باشه

استوپ کنید نود رو با کنترل + سی




یک اسکرین ایجاد کنید
```
apt install screen 
screen -S nubit
```

کنترل آ دی بزنید از اسکرین خارج شید
```
curl -sL1 https://nubit.sh | bash
```


به سایت نوبیت میریم

https://alpha.nubit.org/

اگر میخواید ولت ریکاوری کنید 

https://t.me/crypton_calls/17552 اموزش تو چنل هست

*** کامند ری استارت کردن نوبیت اگر متوقف شده بود
```
screen -x nubit
curl -sL1 https://nubit.sh | bash
```

کنترل آ دی بزنید از اسکرین خارج شید

--------------------------------------------------------------------------------------------------

سایت Rivalz با ریفرال من 
rivalz.ai/?r=SoairCompany

بی ریفرال من 
rivalz.ai/



#Rivalz 

توضیحات مرحله به مرحله 

*** چون نصب Rivalz طولانی هست . اگر از اتصال اینترنتتون اطمینان ندارید اول یه اسکرین باز کنید و تو اسکرین ران کنید که مشکلی پیش نیاد

مثلا بزنید
```
screen -S rivalz
```


ابتدا یک فولدر ایجاد میکنیم
```
mkdir ubuntu
```
وارد فولدر میشویم و فایلی ایجاد میکنیم
```
cd ubuntu
nano virtualubuntu.sh
```

تمام متن زیر را کپی میکنیم . ***** در اول متن جای User و Password  یوزر پس خودتون رو وارد کنید و بعد کپی کنید 
```
#!/bin/bash

USER="crypton"
PASSWORD="Crypton1234"


apt update && apt upgrade -y


sudo apt install -y ubuntu-desktop

sudo apt install -y xrdp

sudo useradd -m -s /bin/bash $USER
echo "$USER:$PASSWORD" | sudo chpasswd

sudo usermod -aG sudo $USER

echo "gnome-session" > ~/.xsession

sudo systemctl restart xrdp

sudo systemctl enable xrdp

sudo apt install -y wget

wget https://api.rivalz.ai/fragmentz/clients/rClient-latest.AppImage -O rClient-latest.AppImage

chmod +x rClient-latest.AppImage

sudo -u $USER mkdir -p /home/$USER/Documents

sudo mv rClient-latest.AppImage /home/$USER/Documents/rClient-latest.AppImage

sudo chown $USER:$USER /home/$USER/Documents/rClient-latest.AppImage

echo
```

 
بعد از کپی کنترل + x را میزنیم . بعد y را و بعد اینتر را که فایل سیو شه


حالا کامند اجرا را میزنیم و حدود نیم ساعت تا یک ساعت صبر میکنیم پروسه تموم شه
```
chmod +x virtualubuntu.sh

./virtualubuntu.sh
```

یک فایل دیگه ایجاد میکنیم

```
nano VPSFix.sh
```
کل کد های زیر را کپی میکنیم
```
#!/bin/bash

# Version 1.1


SERVICE_FILE="/etc/systemd/system/default-interface-config.service"

if [ "$EUID" -ne 0 ]; then
  echo "Lutfen root olarak çaliştirin."
  exit 1
fi

if ! command -v ethtool &> /dev/null; then
  echo "ethtool bulunamadi, yukleniyor..."
  apt-get update
  apt-get install -y ethtool
fi

DEFAULT_INTERFACE=$(ip route show default | awk '/default/ {print $5}')

cat <<EOL > $SERVICE_FILE
[Unit]
Description=Configure default network interface
After=network.target

[Service]
Type=oneshot
ExecStart=/usr/sbin/ethtool -s $DEFAULT_INTERFACE speed 1000 duplex full autoneg off
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
EOL

systemctl daemon-reload

systemctl enable default-interface-config.service

systemctl start default-interface-config.service

echo 
```
بعد از کپی کنترل + x را میزنیم . بعد y را و بعد اینتر را که فایل سیو شه
```
chmod +x VPSFix.sh

./VPSFix.sh
```

اگر تو اسکرین ران کرده بودید میتونید با کنترل آ د از اسکرین خارج شید

حالا وارد remote desktop میشیم و با ایپی سرورمون وارد میشیم . یوزر و پسوورد همون یوزر پسووردی هست که انتخاب کردید


مراحل رو مثل ویدیو میریم


اینم سایت اخر برای ولیدیت کردن

https://be.rivalz.ai/api-v1/orbit-db/verify-orbit-db/yourwalletaddress

*** شما در نگاه اول با صفحه ای خالی مواجهی انگار ، سمت چپ بالای تصویر سیستم عامل میتونید روی قسمت منو مانند کلیک کنید تا بتونید موزیلا و فولدر و ... رو ببینید
