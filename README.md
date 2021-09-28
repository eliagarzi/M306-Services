# Werkstattauftrag W7 Webmin


# 1. Autoren, Versionierung des Dokumentes

**Autoren:** Elia Garzi, Sebastian Gruber

**Datum:** 29.09.2021

**Version:** 1.0

# 2. Einfuehrung

**1. Was ist Webmin?**


   - Beschreibung: Welche Funktionen wird der Service erfuellen
   - Vorgesehener Zeitaufwand für die Realisierung
   - Stolpersteine

# 3. Benoetigte Hard- und Software
   - Hardware (Materialliste, Funktionalitaet)
   - Software (Anforderungen, Firmware, OS-Image, ergaenzende SW-Packages, Abhängigkeiten, Funktionalitaet)

# 4. Installationsanleitung
   - Anweisungen verstaendlich und nachvollziehbar
   - Keine fertigen Loesungsschritte aufzeigen
   - Hilfestellung (Tipps, Quellen...)

## **1. Pi-OS installieren**
Bevor man das Raspberry Pi nutzen kann, muss darauf ein Betriebssystem installiert werden. 
Dazu gibt das offizielle Pi OS, welches auf Debian basiert. 

Zur einfachen Installation des Betriebessystemes nutzen wir den Pi Imager, der von der offiziellen Website heruntergeladen werden kann:

https://www.raspberrypi.org/software/


**1. Pi-Hole Image auf SD Karte installieren**
Nach der Installation startet man den Pi Imager und wählt als Betriebssystem Pi OS (32-Bit) aus und als SD-Karte die SD-Karte die man mit dem Raspberry Pi bekommen hat. 

![Pi OS mit dem Pi Imager installieren](https://user-images.githubusercontent.com/62818267/135052119-cdbbcb2a-f0aa-4372-a9c2-80e4a8bb2afd.png)


**2. Grundkonfiguration vornehmen**
Für diesen Schritt braucht man: 
- Einen Bildschirm 
- WLAN oder LAN-Kabel


Sobald man das Pi OS installiert hat, kann man die SD-Karte in den Raspberry Pi stecken und das Pi starten. Anschliessend kommt eine einfache Grundkonfiguration. Hier muss man die Sprache und das Passwort setzen. Es ist wichtig, dass die Zeitzone richtig auf Zurich konfiguriert ist. 

Wir haben unser Raspberry Pi mit einem TBZ Access Point verbunden. Dafür wählt man oben Rechts das WLAN-Icon aus. 

![Den TBZ-WLAN Access Point auswählen für eine Netzwerkverbindung](https://user-images.githubusercontent.com/62818267/135052323-5dcdb100-6dda-405a-a4b8-f963bef7c092.png)


## **2 Remoteverbindung mit Raspberry Pi herstellen**
Um das Raspberry Pi einfacher zu verwalten nutzt man eine Remoteverbindung. 

**1. VNC und SSH aktivieren**

Um VNC zu aktivieren folgt man diesem Pfad: <br>
Einstellungen/Raspberry-Pi-Konfiguration/Schnittstelle

![SSH und VNC in den Einstellungen aktivieren](https://user-images.githubusercontent.com/62818267/135052013-7266a091-3a32-462a-867b-ff9f3d6bd1f7.png)

Damit die Verbindung funktioniert, braucht man die IP-Adresse
![Ip Adresse](https://user-images.githubusercontent.com/62818267/135052280-13b123f7-6655-4d44-ad18-1fc2801ff447.png)


**2. Sich über VNC verbinden**
- VNC Viewer installieren
- VNC Viewer ausführen und über die IP-Adresse verbinden
**3. Sich über SSH verbinden**



## **3 Webmin auf dem Raspberry Pi installieren**
**1. Alle Updates installieren**

Bevor man Webmin installiert, sollte man sicherstellen, dass alle Updates installiert sind.

Dazu öffnet man die Konsole auf dem Raspberry Pi und gibt folgenden Befehl ein:

`sudo apt-get update && sudo apt-get upgrade -y`

**2. Webmin Repository hinzufügen**

**2. Webmin installieren**

# 5. Qualitaetskontrolle

# 6. Error-Handling

# 7. Quellen

**Bilder:** Von uns
**Pi-Imager:** https://www.raspberrypi.org/software/
**Putty:** https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
**VNC Viewer:** https://www.realvnc.com/de/connect/download/viewer/


# 8. OpenSource Lizenz
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/3.0/ch/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/">Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 3.0 Schweiz Lizenz</a>
