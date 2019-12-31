# Généralités

EN CONSTRUCTION

Ce guide à pour vocation d'expliquer comment configurer les BAD-USB Atmega32U4 avec puce Wifi ESP8266 qui sont vendues sur AliExpress [lien](https://fr.aliexpress.com/item/32946940424.html)

![BAD-USB_front](https://raw.githubusercontent.com/sebastienPoussard/BADUSB_Atmega32U4_ESP8266_FR/master/img/badusb_front.png)
![BAD-USB_back](https://raw.githubusercontent.com/sebastienPoussard/BADUSB_Atmega32U4_ESP8266_FR/master/img/badusb_back.png)

Le code à été récuperé à plusieurs endroits puis modifié pour supporter les claviers AZERTY

# Remerciements & sources

[Le guide de Puckk en anglais](https://github.com/puckk/CJMCU-3212/blob/master/README.md)  
[L'issue #91 du Git spacehuhn/wifi_ducky](https://github.com/spacehuhn/wifi_ducky/issues/91)  
[git d'ODEMCU flasher pour windows](https://github.com/nodemcu/nodemcu-flasher)  
[La librairie KeyboardAzertyFr de martin-leo](https://github.com/martin-leo/KeyboardAzertyFr)  
[Les explication de nico78 sur la conversion en clavier Azerty](https://forum.arduino.cc/index.php?topic=552465.0)



# Arduino IDE
Commencer par installer arduino IDE [Sur le site officiel](https://www.arduino.cc/en/main/software)
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

- Télécharger le fichier firmware [ici](https://github.com/sebastienPoussard/BADUSB_Atmega32U4_ESP8266_FR/raw/master/fichiers/esp8266_wifi_duck_4mb.bin)

### Sous Windows
- Télécharger l'outil NODEMCU-FLASHER [ici](https://github.com/nodemcu/nodemcu-flasher/archive/master.zip)
source du projet Github [ici](https://github.com/nodemcu/nodemcu-flasher)
- Dans config, selectionner à la premiere ligne le firmware téléchargé précédemment.

![firmware](https://github.com/nodemcu/nodemcu-flasher/raw/master/Resources/Images/NodeMCU-Flasher-Setting.png)

- Enfin, selectionner le bon Port puis clicker sur Flasher

![flash](https://raw.githubusercontent.com/nodemcu/nodemcu-flasher/master/Resources/Images/NodeMCU-Flasher-Begin.png)



### Sous Linux

- Il vous faudra installer ESPTOOL pour flasher le firmware (il vous faudra avoir installer Python et pip au préalable)
```Bash
pip install –upgrade esptool
```
- Vous pouvez maintenant lancer la commande suivante pour flasher le firmware, remplacer l'emplacement du fichier <emplacement_esp8266_wifi_duck_4mb.bin>  
```Bash
esptool --trace   --baud 150200 --port /dev/ttyACM0 write_flash 0x00000 <emplacement_esp8266_wifi_duck_4mb.bin> --flash_size 4MB --flash_mode dio --flash_freq 40m
```
- Vous pouvez maintenant dessouder les 2 bornes ou bien arrếter de faire le court-circuit.
à verifier

# Flasher le programme Wifi Ducky


