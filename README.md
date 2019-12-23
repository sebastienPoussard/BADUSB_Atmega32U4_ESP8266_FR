# Généralités
Ce guide à pour vocation d'expliquer comment configurer les BAD-USB Atmega32U4 avec puce Wifi ESP8266 qui sont vendues sur AliExpress [lien](https://fr.aliexpress.com/item/32946940424.html)
![BAD-USB](https://ae01.alicdn.com/kf/HTB1SF8ZXLfsK1RjSszbq6AqBXXaU/Beetle-clavier-virtuel-Badusb-ATMEGA32U4-WIFI-ESP-8266-ESP8266-ESP-12E-TF-Micro-carte-SD-Module.jpg)
Le code à été récuperé à plusieurs endroits puis modifié pour supporter les claviers AZERTY

# Arduino ide
Commencer par installer arduino IDE [Téléchargement](https://www.arduino.cc/en/main/software)
Si vous utilisez Linux, il faudra desactiver le daemon ModemManager qui entre en conflit avec Arduino IDE (Cf. [lien](https://forum.sparkfun.com/viewtopic.php?t=46710))

# Configurer la puce en mode Programmeur ESP
Cette étape permet de configurer la puce Atmega32U4 pour lui dire que l'on veux flasher la puce Wifi ESP8266
