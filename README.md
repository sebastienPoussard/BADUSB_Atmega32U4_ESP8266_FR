# Généralités

EN CONSTRUCTION

Ce guide à pour vocation d'expliquer comment configurer les BAD-USB Atmega32U4 avec puce Wifi ESP8266 qui sont vendues sur AliExpress [lien](https://fr.aliexpress.com/item/32946940424.html)

![BAD-USB_front](https://raw.githubusercontent.com/sebastienPoussard/BADUSB_Atmega32U4_ESP8266_FR/master/img/badusb_front.png)
![BAD-USB_back](https://raw.githubusercontent.com/sebastienPoussard/BADUSB_Atmega32U4_ESP8266_FR/master/img/badusb_back.png)
Le code à été récuperé à plusieurs endroits puis modifié pour supporter les claviers AZERTY

# Arduino IDE
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
- puis faire l'upload.

# Flasher le firmware de la puce Wifi ESP8266
Nous allons maintenant directement programmer la puce Wifi :
- commencer par relier les 2 bornes sur la photo, la solution la plus sûre est de faire une soudure. Si vous n'avez pas le materiel nécessaire, alors vous devez faire un court-circuit entre les 2 bornes avec un objet métallique avant d'insérer la carte dans le port USB puis maintenir ce court-circuit tout le long de cette procédure.
![shunt](https://raw.githubusercontent.com/sebastienPoussard/BADUSB_Atmega32U4_ESP8266_FR/master/img/shunt.png)
