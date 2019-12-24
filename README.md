# Généralités

EN CONSTRUCTION

Ce guide à pour vocation d'expliquer comment configurer les BAD-USB Atmega32U4 avec puce Wifi ESP8266 qui sont vendues sur AliExpress [lien](https://fr.aliexpress.com/item/32946940424.html)
![BAD-USB](https://ae01.alicdn.com/kf/HTB1SF8ZXLfsK1RjSszbq6AqBXXaU/Beetle-clavier-virtuel-Badusb-ATMEGA32U4-WIFI-ESP-8266-ESP8266-ESP-12E-TF-Micro-carte-SD-Module.jpg)
Le code à été récuperé à plusieurs endroits puis modifié pour supporter les claviers AZERTY

# Arduino ide
Commencer par installer arduino IDE [Téléchargement](https://www.arduino.cc/en/main/software)
Si vous utilisez Linux, il faudra desactiver le daemon ModemManager qui entre en conflit avec Arduino IDE (Cf. [lien](https://forum.sparkfun.com/viewtopic.php?t=46710))
```Bash
sudo systemctl stop ModemManager.service
```
Vous pouvez le relancer à la fin de ce tuto avec  
```Bash
sudo systemctl start ModemManager.service
```

# Configurer la puce en mode Programmeur ESP
Cette étape permet de configurer la puce Atmega32U4 pour lui dire que l'on veux flasher la puce Wifi ESP8266 par la suite.
- brancher la carte à l'ordinateur
- sous Arduino IDE selectionner Tools > Board > Arduino Leonardo. Selectionner le port qui correspond ( Tools > Port > XXX )
- Charger le code de [Step1.ino](https://github.com/sebastienPoussard/BADUSB_Atmega32U4_ESP8266_FR/blob/master/fichiers/step1.ino)
- puis faire Upload.
